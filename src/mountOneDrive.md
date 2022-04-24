---
title: Install RClone | DEVserv.ME
label: Install RClone
order: 100
authors:
  - name: Charl Cronje
    email: charl@devserv.me
    link: https://charl-cv.devserv.me
    avatar: https://assets.devserv.me/avatars/darker.jpg
tags: [open source,dev,software,contribute,js,php,firebase,mysql,oracle,log]
---

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