---
title: Use OneDrive for storage for web-hosting | CRONje.ME
label: Use OneDrive for storage for web-hosting
order: 100
authors:
  - name: Charl Cronje
    email: charl@CRONje.ME
    link: https://blog.cronje.me
    avatar: https://assets.cronje.me/avatars/darker.jpg
tags: [open source,dev,software,contribute,js,php,firebase,mysql,oracle,log]
---
<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>

## Before you start

I did a doc about using `rclone` to mount your OneDrive to your linux server here: [Mount OneDrive to Server](./mountOneDrive.md). Make sure you understand how to mount your OneDrive, then continue from here.

> **Please Note:** This is an example on CentoOS 8 but will work about the same on Ubuntu or whatever distro you are using, just make sure about the paths etc.

I mount my OneDrive with the following command:

```sh
rclone --vfs-cache-mode writes mount one: /var/www/mnt/one
```

So from that you should be able to see that I'm mounting my OneDrive in my `/var/www/` folder under the directory `./mnt/one/`. Then in my vhosts.conf file I added the following entry for a virtual host:

```
# example.cronje.me
<VirtualHost 100.100.100.100:8080>          # I'm using Nginx reverse proxy so I'm running apache on  port 8080, but usually it would be 80. Or if you a are using Nginx foryour web server that should not make a difference.
    ServerName example.cronje.me
    ServerAdmin admin@cronje.me
    DocumentRoot /var/www/mnt/one/files/example      # So in my OneDrive I have a folder structure of /files/example and that is where I have index.html or index.php or whatever that I want apache to execute. Also I have all my vidoes and music and documents in there that I want to serve on the web, and it works as expected
    <Directory /var/www/mnt/one/files/example>
        Require all granted
        Options -Indexes +FollowSymLinks
        AllowOverride All
    </Directory>
    ErrorLog /var/www/mnt/logs/error.log      # I just keep the log files out of OneDrive to not have to write there all the time.
    CustomLog /var/www/mnt/logs/access.log combined 
</VirtualHost>
```

- That is about that, and it is really not putting any delay on my server response, maybe I'm just lucky that my server is close to where my OneDrive files are hosted.
- Then I'm also using one file, file manager that I copied to `/var/www/mmnt/one/files/example`. It is a single `php`
file that serves a web-based file manager so that I can browse my files on onedrive and get the links to them. You can download this .php file here: `https://www.files.gallery/`

 Thats how I get 1TB of web storage for $5 a month via OneDrive.