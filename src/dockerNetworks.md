---
title: Docker Networks
---
<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>

## List Existing Docker Networks

```shell
docker network ls
```

## Create a new Docker Network

```shell
docker network create -d bridge servBridge

# -d (Driver)
# bridge (The driver)
# servBridge (The network name)
```
