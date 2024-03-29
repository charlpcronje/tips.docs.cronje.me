---
title: Clear disk space on CentOS/RHEL 6, 7, 8
---
<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>

```sh
curl -Ls http://bit.ly/clean-centos-disk-space | sudo bash
```

Scared to run that? Just run individual commands that the script runs.

Before anything, you have to install the yum-utils package:

```
yum -y install yum-utils
```

## 1. Trim log files

```sh
find /var -name "*.log" \( \( -size +50M -mtime +7 \) -o -mtime +30 \) -exec truncate {} --size 0 \;
```

This will truncate any *.log files on the volume /var that are either older than 7 days and greater than 50M or older than 30 days.

## 2. Cleanup YUM cache

The simple command to cleanup yum caches:

```sh
yum clean all
```

- Note that the above command will not remove everything related to yum. For instance, metadata for disabled repositories will not be affected.
- You may want to free up space taken by orphaned data from disabled or removed repositories:

```sh
rm -rf /var/cache/yum
```

Also, when you accidentally run yum through a regular user (forgot sudo), yum will create user-cache. So lets delete that too:

```sh
rm -rf /var/tmp/yum-*
```

## 3. Remove orphan packages

```sh
package-cleanup --quiet --leaves 
```

> Confirm removing orphan packages
> Now, if happy with suggestions given by the previous command, run:

```sh
package-cleanup --quiet --leaves | xargs yum remove -y
```

## 4. Remove WP CLI cached WordPress downloads

WP CLI saves WordPress archives every time you setup a new WordPress website. You can remove those caches by the following command:

```sh
rm -rf /root/.wp-cli/cache/*
rm -rf /home/*/.wp-cli/cache/*
```

## 5. Remove old kernels

Before removing old kernels, you might want to simply reboot first in order to boot up from the latest kernel.
That's because you can't remove an old kernel if you're booted into it 🙂

The following commands will keep just 2 latest kernels installed:

```sh
(( $(rpm -E %{rhel}) >= 8 )) && dnf remove $(dnf repoquery --installonly --latest-limit=-2 -q)
(( $(rpm -E %{rhel}) <= 7 )) && package-cleanup --oldkernels --count=2
```

> Note that with some VPS providers (Linode for example), servers use provider's built kernels by default and not the ones on the server itself. So it makes little sense to keep more than 1 old kernel on the system. So:

```sh
(( $(rpm -E %{rhel}) >= 8 )) && dnf remove $(dnf repoquery --installonly --latest-limit=-1 -q)
(( $(rpm -E %{rhel}) <= 7 )) && package-cleanup --oldkernels --count=1
```

## 6. Remove Composer cache

```sh
rm -rf /root/.composer/cache
rm -rf /home/*/.composer/cache
```

## 7. Remove core dumps

If you had some severe failures with PHP which caused it to segfault and had core dumps enabled, chances are – you have quite a few of those.
They are not needed after you are done debugging the problem. So:

```sh
find -regex ".*/core\.[0-9]+$" -delete
```

## 8. Remove error_log files (cPanel)

If you use the disgusting cPanel, you surely got dozens of error_log files scattered across your web directories. Much better if you can install the Citrus Stack. A temporary solution is to remove all those files:

```sh
find /home/*/public_html/ -name error_log -delete
```

## 9. Remove Node.js caches

```sh
rm -rf /root/.npm /home/*/.npm /root/.node-gyp /home/*/.node-gyp /tmp/npm-*
```

## 10. Remove Mock caches

Been building some RPM packages with mock? Those root caches can be quite large.
If you no longer intend to build RPM packages on a given machine:

```
rm -rf /var/cache/mock/* /var/lib/mock/*
```

## 11. Clear generic program caches

Multiple programs have a convention of storing their caches under users' home .cache subdirectory.
Example: `/home/username/.cache/progname`.

You may want to clear up those, but not the subdirectories of programs. Like so:

```sh
rm -rf /home/*/.cache/*/* /root/.cache/*/* 
```
