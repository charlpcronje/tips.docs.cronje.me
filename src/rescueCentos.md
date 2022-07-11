---
title: Rescue CentOS 7 System
---
<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>

- I was busy working on my server in VS Code-Sever when a new SSH connection just would not work, then system after system started failing. At first I thought I was hacked, but when I checked the logs there were no sign of any attempts or any other logins.
- I come from a windows background so I thought restarting would probably fix the problem, but it did not. When I restarted I never got to make a new SSH connection. So I logged into my management console and opened the KVM Console.
- I can't speak for all hosting companies but I'm quite sure that most of them will have a place where you'll be able to access your virtual server without having to use SSH.
- At when I restarted my server I saw it was still booting up but it stopped at this point:

![stopped](rescue/stopped.png)

- After spending some time on Google I figured out that booting from the CentOS DVD will put me in the position to access my file system
- I'm not adding all the commands and screenshots here but I'm rather giving a broad view of what I did, there could be thousands of reasons why your OS stopped working so going into the specifics would be pointless.
- In my case the /bin and /sbin directories got deleted which I could simply copy from the dvd.
- I needed to add the DVD to my server's virtual DVD drive to be able to boot from it.
- This might not have been the most helpful but I hope this will at least put you in the right direction.
