# Python Set Version

Every now and then I have to change the default python version, this started to become hassle.

This script lets me choose the default version and creates and alias to `python`

```sh
# pythonSetVersion.sh

#!/bin/bash

select OPTION in 'python2.7' 'python3.6' 
do
    echo alias python="'/usr/bin/$OPTION'";
    alias python='/usr/bin/$OPTION';
    echo . ~/.bashrc;
    . ~/.bashrc
    break;
done
echo "Python vesion set to $OPTION";
```

Once I created the script I had to make it executable

```sh
chmod +x pythonSetVersion.sh
```

Then I created a symbolic link in my `/usr/bin` directory

```sh
ln -s /srv/scripts/pythonSetVersion.sh /usr/bin/psv
```

To to change the python version I just need to type `psv`

