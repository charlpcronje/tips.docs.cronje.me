---
title: Chrome Apps and Extensions
---
<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>

## Creating an chrome app or extension

### Create a `[manifest.json](manifest.json)`

```json
{
    "name": "DEVSERV IDE", 
    "version": "0.1",
    "manifest_version": 3,
    "description":"AWS's Cloud 9 IDE in self hosted",
    "app": {
        "urls": ["https://c9.CRONje.ME/ide.html"],
        "launch": {
            "web_url": "https://c9.CRONje.ME/ide.html"
        }
    },
    "
        "128": "cloud9.png"
    }
}
```

## Almost done

- From here you can go to `chrome://extensions`
- Toggle on developer mode at the top right
- Click on `Load Unpacked`
- Select the folder that contains the `manifest.json`
- Goto `chrome://apps` and it will be there as an app. One you opened it you pin it to you taskbar and tun it as a windows app.
