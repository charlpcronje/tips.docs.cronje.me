# Whiptail basic usage

Each file ypu create must be made executable, with the following command the file will be executable by using `sh ./demo.sh`

```shell
chmod 744 demo.sh

# Run file: sh ./demo.sh
```

To run the file without out having to put sh in front of the filename:

```shell
chmod 777 demo.sh

# Run file: ./demo.sh
```

## Code Server for Creating Scripts

VS Code-server that is running on port `:4444` on `devserv.me` is perfect for creating these scripts, you can create the files and then run them in the built in terminal to test them, if you're not using code-server yet, then you should really stop not using code-server! Here is the [install instructions for code-server](http://setup.docs.devserv.me/codeserver/)
Then also have a look at

- [Code-Server Extensions](http://setup.docs.devserv.me/codeserverextensions/)
- [Code-Server as Service](http://setup.docs.devserv.me/codeserverservice/)

- I'm creating these scripts in `/srv/scripts`.
- Run it by using `./` before the filename if the location is not along the PATH.

## Display a basic dialog box

- For a quick test to see if whiptail is working, enter the following command

```shell
message="Today, we will learn about Whiptail."
whiptail --msgbox --title "Intro to Whiptail" "$message" 10 50
```

- Create a file named `query.sh` with the following content

```bash
# Part 1 - Query for the user's name
NAME=$(whiptail --inputbox "What is your name?" 8 39 --title "Getting to know you" 3>&1 1>&2 2>&3)
                                                                        
exitstatus=$?
if [ $exitstatus = 0 ]; then
echo "Greetings," $NAME
else
echo "User canceled input."
fi

echo "(Exit status: $exitstatus)"

#Part 2 - Query for the user's country

COUNTRY=$(whiptail --inputbox "What country do you live in?" 8 39 --title "Getting to know you" 3>&1 1>&2 2>&3)
                                                                       
exitstatus=$?
if [ $exitstatus = 0 ]; then
echo "I hope the weather is nice in" $COUNTRY
else
echo "User canceled input."
fi

echo "(Exit status: $exitstatus)"
```

Okay so that was some input fields, now for some yes/no

create `tuesday.sh` with the following content

```bash
if (whiptail --title "Is it Tuesday?" --yesno "Is today Tuesday?" 8 78); then
    echo "Happy Tuesday, exit status was $?."
else
    echo "Maybe it will be Tuesday tomorrow, exit status was $?."

fi
```

The `--yesno` box option also permits us to edit the content of the "Yes" and "No" fields. Here is an example:

```bash
if (whiptail --title "Is it Tuesday?" --yesno "Is today Tuesday?" 8 78 --no-button "Not Tuesday" --yes-button "Tuesday"); then
echo "Happy Tuesday, exit status was $?."
else
echo "Maybe it will be Tuesday tomorrow, exit status was $?."
fi
```

One last thing. Whiptail sends the user's input to stderr. Yes, you read that correctly: stderr, and

Here is the phrase for doing that:

```bash
3>&1 1>&2 2>&3
```

**Explanation:**

Create a file descriptor 3 that points to 1 (stdout)
Redirect 1 (stdout) to 2 (stderr)
Redirect 2 (stderr) to the 3 file descriptor, which is pointed to stdout
Here is how it looks in a script snippet from the above `--inputbox` example:

```bash
NAME=$(whiptail --inputbox "What is your name?" 8 39 --title "Getting to know you" 3>&1 1>&2 2>&3)
```

Here's a list of the primary box options available for whiptail:

```bash
--title
--infobox
--msgbox
--yesno
--inputbox
--passwordbox
--menu
--textbox
--checklist
--radiolist
--gauge
```
