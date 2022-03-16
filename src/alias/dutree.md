# Alias for Dutree

## Aliases for all users

Create a file in `/etc/profile.d/` directory

```sh
cd /etc/profile.d/
nano myAlias.sh
```

Define the alias in the file

```sh
alias hdtop="dutree -d 2 -a"
# Goes 2 Dirs deep and agreagtes all files smaller than 1MB
```

Give right permission to the file

```sh
chmod 755 myAlias.sh
```

Restart SSH session exiting terminal and opening a new one (or use source /etc/profile.d/myAlias.sh)


## Alias for a specific user

To create an alias permanently add the alias to your .bashrc file

```sh
sudo vi ~/.bashrc
```

And then add your alias at the bottom

```sh
alias hdtop="dutree -d 2 -a"
```

