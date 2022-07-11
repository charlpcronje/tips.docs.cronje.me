---
title:  Some General Linux Tips
---
<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>

## Add folder to the path

```shell
export PATH=$PATH:/srv/scripts
```

## Symbolic Links

Example link

```shell
ln -s /srv/scripts/service-menu /usr/bin/sm

# ln for link
# -s for symbolic
# Destination (File you are linking to)
# Source (File or link to be created to link to Destination)

```
