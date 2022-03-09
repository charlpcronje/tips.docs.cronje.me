
# Install RPM packages

`RPM` You will find RPM's everywhere and for the considerable future. It is very simple to install one of these

## Download file

```shell 
# wget url
wget http://some_website/sample_file.rpm
```

## Install Package

```shell
sudo rpm -i sample_file.rpm
```

### Install `RPM` File with `Yum`

```shell
sudo yum localinstall sample_file.rpm
```

### Install `RPM` on `Fedora`

```shell
sudo rpm -i sample_file.rpm
```

### Install using `dnf`

```shell
sudo dnf localinstall sample_file.rpm
```

> Unlike many Linux tools, DNF is not a set of initials. It is merely the next evolution of the yum package manager.

## Remove RPM Package

The RPM installer can be used to remove (or uninstall) a software package.

Enter the following into a terminal window:

```shell
sudo rpm -e sample_file.rpm
```

The `-e` option instructs `RPM` to erase the software.

## Check `RPM` Dependencies

So far, this guide assumes the software either doesn’t have dependencies or already has them installed.

To check the .rpm file for dependencies using the following command:

```shell
sudo rpm -qpR sample_file.rpm
```

- The system should list all the dependencies:

**`-q`** – This option tells RPM to **query** the file
**`-p`** – This option lets you specify the target **package** to query
**`-R`** – This lists the **requirements** for the package

If there are any missing dependencies, you can install them from the standard repositories using yum or dnf. If your software requires other non-standard software, it will often be noted in the installation instructions.

## Download RPM Packages from the Repository

One exciting feature of the yum package manager is that it allows you to download .rpm files directly from the repository. This might be helpful if you have limited bandwidth, or want to copy a single downloaded file between systems. It could also help if you have intermittent internet access, and you don’t want to spend time waiting for your installer to finish.

To download a `.rpm` file from the repositories, enter the following:

```shell
sudo yumdownloader packagename
```

If you wanted to download the files for Apache, for instance, you’d replace `packagename` with `httpd`. You can then install the file as above
