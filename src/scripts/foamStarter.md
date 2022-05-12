# Foam Brain Starter Template

Foam is a tool that supports creating relationships between thoughts and information to help you think better.

Foam kitchen sink, showing a few of the key features

Whether you want to build a Second Brain or a Zettelkasten, write a book, or just get better at long-term learning, Foam can help you organise your thoughts if you follow these simple rules:

1. Create a single Foam workspace for all your knowledge and research following the [Getting started](https://foambubble.github.io/foam/#getting-started) guide.
1. Write your thoughts in markdown documents (I like to call them Bubbles, but that might be more than a little twee). These documents should be atomic: Put things that belong together into a single document, and limit its content to that single topic. [source](https://zettelkasten.de/posts/overview/#principles)
1. Use Foam’s shortcuts and autocompletions to link your thoughts together with [[wikilinks]], and navigate between them to explore your knowledge graph.
1. Get an overview of your Foam workspace using a [Graph Visualisation](https://foambubble.github.io/foam/features/graph-visualisation) (⚠️ WIP), and discover relationships between your thoughts with the use of [Backlinking](https://foambubble.github.io/foam/features/backlinking)

Foam is a like a bathtub: What you get out of it depends on what you put into it.

To quickly get started with a new "foam brain" project I created a script that will create a new foam with a starter template

## Create a new Foam Project

```sh
foam /var/www/zzz/projectFolder
```

> Here is the script to expain what it does:


```sh
#!/bin/bash
clear;

```conf
 ___  __               __   __                      ___ 
|__  /  \  /\   |\/|  |__) |__)  /\  | |\ |   |\/| |__  
|    \__/ /~~\  |  | .|__) |  \ /~~\ | | \| . |  | |___ 

01000110    01001111    01000001    01001101    00101110 
01000010    01010010    01000001    01001001    01001110 
            00101110    01001101    01000101                                                         
```
echo "┌────────────────────────────────────────────────┐"
echo "│ INSTRUCTIONS - NEW FOAM BAIN                            │
echo "│ foam [path to new foam brain]                           │
echo "│                                                         │
echo "│ Example:                                                │
echo "│ foam /var/www/zzz/newBrain                              │
echo "│                                                         │
echo "│ The above example will create directory                 │
echo "│ mkdir -p /var/www/zzz/newBrain                          │
echo "│ cp /srv/scripts/foam/template/* /var/www/zzz/newBrain   │
echo "│ cd /var/www/zzz/newBrain                                │
echo "│                                                         │
echo "│ Then if you have code-server installled it will attempt │
echo "│ to open vscode in the new foam brain                    │
echo "└────────────────────────────────────────────────┘"
echo " ";
echo "ENTER THE FULL PATH OF NEW FOAM BRAIN";
read BRAIN_PATH;

echo "CONFIRM FOAM PATH: $BRAIN_PATH ? yn"; Do 
read "Confirm yn"
echo 
case $yn in
  [Yy]* ) 
    mkdir -p $BRAIN_PATH;  cp /srv/scripts/foam/template/* $BRAIN_PATH/;
    cd $BRAIN_PATH;
  [Nn]* ) exit;;
 
    * ) echo "Goodbye!";; break;;
esac

echo " ";
echo " "; 
echo "by Charl Cronje - http://cv.CRONje.ME"
```

Now the script must just be made executable:

```sh
chmod +x /srv/scripts/foam.sh
```

Create symbolic link to make the script global

```sh
ln -s /srv/scripts/foam.sh /usr/bin/foam
```

