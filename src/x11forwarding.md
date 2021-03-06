---
title: Local dev Server X11 Forwarding
---
<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>

## MobaXTerm

This SSH Client software comes with an XServer Built in
For windows install [MobaXTerm](https://mobaxterm.mobatek.net/download-home-edition.html)

## What is X11 Forwarding?

X11 forwarding is a mechanism that allows a user to start up remote applications but forward the application display to your local Windows machine.
The url's are not always available remotely so to get past this you can run Firefox with X11 forwarding

## Install Firefox on CentOS 8

```shell
mkdir /srv/tools
wget -O- "https://download.mozilla.org/?product=firefox-latest-ssl&os=linux64&lang=en-US" | tar -jx -C /srv/tools/
```

Create a symlink to a newly downloaded `/srv/tools/firefox/firefox` executable.

```shell
ln -s /srv/tools/firefox/firefox /usr/bin/firefox
```

Start the latest Firefox browser from GUI menu or by executing the `firefox` command.

```shell
firefox
```

Open MobaXTerm and Create Open new Tab, Then manually open a new SSH connection to your server but with the -X directive

Check the server's sshd_config (normally `/etc/ssh/sshd_config`), and make sure `X11Forwarding` option is enabled with the line

```conf
X11Forwarding yes
```

Allow clients to connect from any host using `xhost+`

Execute the following command to disable the access control, by which you can allow clients to connect from any host.

```shell
xhost +
```

If X11Forwarding is not specified, the default is no on the Debian machines I have available to check.

```shell
ssh -X user@server-id

# Set environment variable for display
export DISPLAY="localhost:0.0"
firefox
```

It might give you some errors the first time, but then just close the process and try again, a `Linux` looking windows should pop up out of nowhere... You are now running a Local Browser on the `Centos 8 Server` but viewing the `window` in `windows`, thanks to `X11 Forwarding`

If firefox gives you driver problems, try installing google-chrome

```sh
yum install google-chrome
```

And execute the following command to run chrome with min settings to open even if there are some issues with the drivers

```sh
google-chrome --disable-gpu --disable-software-rasterizer --no-sandbox
```