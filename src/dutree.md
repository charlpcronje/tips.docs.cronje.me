# Dutree

dutree is a free open-source, fast command-line tool for analyzing disk usage, written in Rust programming language. It is developed from durep (disk usage reporter) and tree (list directory content in tree-like format) command line tools. dutree therefore reports disk usage in a tree-like format.

It displays coloured output, depending on values configured in the GNU LS_COLORS environment variable. This env variable enables for setting the colours of files based on extension, permissions as well as file type.

## Features

- how the file system tree.
- upports aggregating of small files.
- llows for comparing different directories.
- upports excluding of files or directories.

## Install dutree

```sh
cd ~
sudo curl https://sh.rustup.rs -sSf | sh
```

Once installed, you can run the following command to install `dutree` in Linux distributions as shown.

```sh
cargo install --git https://github.com/nachoparker/dutree.git
```

After installing `dutree`, it uses environment colors according to the variable **LS_COLORS**, it has the same colors ls `--color` command that our distro has configured.

```sh
ls --color
```

The simplest way of running `dutree` is without arguments, this way it shows a filesystem tree.

```sh
dutree
```

![img1](https://www.tecmint.com/wp-content/uploads/2018/04/Linux-Filesystem-Disk-Usage.png)

_Linux Filesystem Disk Usage_

To display real disk usage instead of file size, use the -u flag.

```sh
dutree -u
```

![img2](https://www.tecmint.com/wp-content/uploads/2018/04/Show-Linux-Disk-Usage.png)

## Show Directories in Depth

You can show directories up to a given **depth** (default **1**), using the -d flag. The command below will show directories up to a **depth** of **3**, under the current working directory.

For example if the current working directory (~/), then display size of `~/*/*/*` as shown in the following sample screenshot.

```sh
dutree -d 3
```

![img4](https://www.tecmint.com/wp-content/uploads/2018/04/Show-Directories-in-Depth-Disk-Usage.png)

## Exclude Files or Directories in Output.

To exclude matching a file or directory name, use the -x flag.

```sh
 dutree -x CentOS-7.0-1406-x86_64-DVD.iso
```

![img5](https://www.tecmint.com/wp-content/uploads/2018/04/Exclude-Filename-in-output.png)

_Show Disk Usage with Exclude Filename_

You can also get a quick local overview by skipping directories, using the -f option, like so.

```sh
dutree -f
```

![img6](https://www.tecmint.com/wp-content/uploads/2018/04/Quick-Overview-by-Skipping-Directories.png)

_Quick Overview by Skipping Directories_

A full summary/overview can be generated using the -s flag as shown.

```sh
dutree -s
```

![img7](https://www.tecmint.com/wp-content/uploads/2018/04/Linux-Disk-Usage-Summary.png)

_Linux Disk Usage Summary_

## Aggregate Small Files

It is possible to aggregate files smaller than a certain size, default is 1M as shown.

```sh
dutree -a
```

![img8](https://www.tecmint.com/wp-content/uploads/2018/04/Aggregate-Small-Files.png)

## Exclude Hidden Files

The -H switch allows for excluding hidden files in the output.

```sh
dutree -H
```

The -b option is used to print sizes in bytes, instead of kilobytes (default).

```sh
dutree -b
```

To turn off colors, and only display ASCII characters, use the -A flag like so.

```sh
$ dutree -A
```

You can view the dutree help message using the -h option.

```sh
dutree -h

# OUTPUT BELOW

Usage: dutree [options]  [..]
 
Options:
    -d, --depth [DEPTH] show directories up to depth N (def 1)
    -a, --aggr [N[KMG]] aggregate smaller than N B/KiB/MiB/GiB (def 1M)
    -s, --summary       equivalent to -da, or -d1 -a1M
    -u, --usage         report real disk usage instead of file size
    -b, --bytes         print sizes in bytes
    -x, --exclude NAME  exclude matching files or directories
    -H, --no-hidden     exclude hidden files
    -A, --ascii         ASCII characters only, no colors
    -h, --help          show help
    -v, --version       print version number
dutree Github Repository: https://github.com/nachoparker/dutree
```

Dutree is a simple yet powerful command-line tool to show `file size` and `analyze` disk usage in `tree-like` format, on `Linux` systems. 
