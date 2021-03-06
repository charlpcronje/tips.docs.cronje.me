---
title: Install RClone | CRONje.ME
label: Install RClone
order: 100
authors:
  - name: Charl Cronje
    email: charl@CRONje.ME
    link: https://blog.cronje.me
    avatar: https://assets.cronje.me/avatars/darker.jpg
tags: [open source,dev,software,contribute,js,php,firebase,mysql,oracle,log]
---
<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>

## Install RClone

```sh
curl https://rclone.org/install.sh | sudo bash
```

Then when it's done installing, execute the following command:

```sh
rclone config
```

![Now it will prompt you to add a (n) new remote service. Answer `n`](rclone/rclone1.jpg)


![Now it asks for a name for tour new remote, you can name it anything but just remember what you name it. Enter `name`](rclone/rclone2.png)


![Now it wants you to find the service in a list, in my case it was nr 22 OneDrive. Enter `22`](rclone/rclone3.png)


![Now it will ask you for your microsoft `App Client Id` and `client secret`, you don't have to enter anything. Enter, `Enter`, `Enter`](rclone/rclone6.png)


![Edit Advanced Config? (y/n).  Enter `n`](rclone/rclone7.png)


![Use auto config. Enter `y`](rclone/rclone9.png)


![That will open a website to OneDrive to Login with your normal OneDrive credentials](rclone/rclone10.png)


If at this point you can't open a browser because you're in a terminal then don't worry, there is a way around this. 

!!!
[Open browser with `X11 Forwarding`](x11forwarding.md)
!!!

![Once you've entered your credentials you'll get a confirmation email](rclone/rclone11.png)

![Select the share applicable to you in the list. Enter `1`](rclone/rclone13.png)

![Then choose a drive to use. Enter `0`](rclone/rclone14.png)

![That is that for the config. Choose `q`](rclone/rclone16.png)

![Mount network drive](rclone/rclone17.png)

But to let the command run every time the server start, add the command to `/etc/rc.d/rc.local`

```sh
nano /etc/rc.d/rc.local
```

Add the following command to the end of the file, where `one` is the name you have the share in step 2 and `/var/one` is where you want your onedrive to mount.


```sh
# /etc/rc.d/rc.local
rclone --vfs-cache-mode writes mount one: /var/one
```

# Mounting the drive on Startup with systemctl service

```sh
nano /etc/systemd/system/rclone.service
```

Copy and Paste the folowing

```sh
[Unit]
Description=OneDrive (rclone)
AssertPathIsDirectory=/var/one

After=network.service

[Service]

Type=simple
ExecStart=/usr/bin/rclone mount \
        --config=/root/.config/rclone/rclone.conf \
        --allow-other \
        --cache-tmp-upload-path=/tmp/rclone/upload \
        --cache-chunk-path=/tmp/rclone/chunks \
        --cache-workers=8 \
        --cache-writes \
        --cache-dir=/tmp/rclone/vfs \
        --cache-db-path=/tmp/rclone/db \
        --no-modtime \
        --drive-use-trash \
        --stats=0 \
        --checkers=16 \
        --bwlimit=40M \
        --dir-cache-time=60m \
        --cache-info-age=60m one:/ /var/one

ExecStop=/bin/fusermount -u /var/one
Restart=always
RestartSec=10

[Install]

WantedBy=default.target
```

Then run the following command that will run the service and `enable` to add it to the startup

```sh
systemctl start rclone
systemctl enable rclone
```
