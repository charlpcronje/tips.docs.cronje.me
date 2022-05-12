# Git Usage

## Remove file from the repository

```shell
git rm --cached your_filename
```

## Make git not notice changes to a file

This will keep the file in the repository, but it won't commit changes to it. It will stay unchanged in the repository:

```shell
git update-index --assume-unchanged your_filename
```

To undo the previous command(tell git that you do want to keep track of changes for the file), there's the opposite command, `--no-assume-unchanged`

```shell
git update-index --no-assume-unchanged your_filename
```

## Get the remote URL of a Repo

```shell
cd /path/to/repo
git remote show origin

# Output
remote origin
  Fetch URL: https://github.com/isa-holdings/vue.ts.vite.securezone.co.za.git
  Push  URL: https://github.com/isa-holdings/vue.ts.vite.securezone.co.za.git
  HEAD branch: main
  Remote branch:
    main tracked
  Local branch configured for 'git pull':
    main merges with remote main
  Local ref configured for 'git push':
    main pushes to main (up to date)
```
