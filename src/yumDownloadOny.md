# YUM Download only

Sometimes it might happen that you will be working off line and you ned to install files to be installed later.

you can ask YUM to download the Package with it's repo but not to install it yet by using the `downloadonly` option

```shell
yum install --downloadonly --donwloaddit=<directory> <package>
```

This feature is available since CentOS 7, I ou want to use it on CentOS 6 then yo first have to install a YUM Plugin

```shell
yum install yum-plugin-downloadonly
``
