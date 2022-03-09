# Set 4 Web

- To constantly set file and folder permissions for folders in `/var/www` can be a hassle
- Please note this script is not for production, the permissions set here is for testing purposes and is not secure
- However this is perfect for testing


## The Script

```sh        
# set4Web.sh

#!/bin/bash

clear;
echo ".__ .___.  . __..___.__ .  .   .  ..___"
echo "|  \[__ \  /(__ [__ [__)\  /   |\/|[__ "
echo "|__/[___ \/ .__)[___|  \ \/  * |  |[___"
echo "───────────────────────────────────"─
echo "SET PERMISSIONS 4 WEB DIRECTORY & FILES "
echo " ";
if [ -z $1 ]; then 
    echo "┌──────────────────────────────────────────────┐"
    echo "│ USAGE INSTRUCTIONS                           │"
    echo "│                                              │"
    echo "│ set4web [full path]                          │"
    echo "│                                              │"
    echo "│ EXAMPLE:                                     │"
    echo "│ set4web /var/www/html                        │"
    echo "│                                              │"
    echo "│ The above example will run the following:    │"
    echo "│ chmod -R 775 /var/www/html                   │"
    echo "│ chown -R apache:apache /var/www/html         │"
    echo "│                                              │"
    echo "│ Note: These settings are for ease of         │"
    echo "│ use while in a dev environment and should    │"
    echo "│ NOT be used in a production environment      │"
    echo "└──────────────────────────────────────────────┘"
else 
    ACTION_PATH="$1"
	
    BLUE="\033[0;34m"
    GREEN="\033[0;32m"
    NC="\033[0m"
    
    echo "Setting Permissions 4 : $ACTION_PATH"
    chmod -R 775 $ACTION_PATH && printf "${BLUE}775 Permission${NC} set on ${GREEN}$ACTION_PATH${NC}, files and sub-directories\n"
    chown -R apache:apache $ACTION_PATH && printf "${BLUE}apache:apache owner${NC} set om ${GREEN}$ACTION_PATH${NC}, files and sub-directories"
fi
echo " ";
echo " "; 
echo "by Charl Cronje - http://charl-cv.devserv.me"
```

- The Script accepts one paramarter and the is the full path of the directory you want to `set4web` plus all it's sub-directories and files
- Then I had to set the script to be executable

```sh
chmod +x set4web.sh
```

Then I created a synbolic link to my /usr/bin folder to make the script global accessable

```sh
ln -s /srv/scripts/set4Web.sh /usr/bin/set4web
```

Now to set the permissions 4 web for `/var/www/test` I only have to type `set4web /var/www/test`


