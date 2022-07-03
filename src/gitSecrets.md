---
title: Git Secrets
---
<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>

# Installation

## Dependencies

`git-secret` relies on two dependencies: `git` and `gpg`. Download and install them before using this project. `git-secret` is tested to work with:

```sh
git version 2.7.0
gpg (GnuPG) 1.4.20
```

## Supported platforms

`git-secret` works with `Mac OS X` >= 10.9, `Ubuntu` >= 14.04, `Debian` >= 8.3, and `Fedora` / `CentOS`. You can check the full list [here](https://github.com/sobolevn/git-secret/blob/master/.github/workflows/test.yml). You can add your platform to this list, if all the tests pass for you. `Cygwin` support [is planned](https://github.com/sobolevn/git-secret/issues/40).

## Installation process

There are several ways to install `git-secret`:

___

### Homebrew

```sh
brew install git-secret
```

___

### `deb` package

You can find the `deb` repository [here](https://gitsecret.jfrog.io/artifactory/git-secret-deb/). Pre-requirements: make sure you have installed `apt-transport-https` and `ca-certificates`

```sh
sudo sh -c "echo 'deb https://gitsecret.jfrog.io/artifactory/git-secret-deb git-secret main' >> /etc/apt/sources.list"
wget -qO - 'https://gitsecret.jfrog.io/artifactory/api/gpg/key/public' | sudo apt-key add -
sudo apt-get update && sudo apt-get install -y git-secret

# Testing, that it worked:
git secret --version
```

___

### `rpm` package

You can find the `rpm` repository [here](https://gitsecret.jfrog.io/artifactory/git-secret-rpm/).

```sh
wget https://raw.githubusercontent.com/sobolevn/git-secret/master/utils/rpm/git-secret.repo -O git-secret-rpm.repo
# Inspect what's inside! You can also enable `gpg` check on repo level.
sudo mv git-secret-rpm.repo /etc/yum.repos.d/
sudo yum install -y git-secret

# Testing, that it worked:
git secret --version
```

___

### Alpine

You can find the `apk` repository [here](https://gitsecret.jfrog.io/artifactory/git-secret-apk/). See list of supported architectures [here](https://github.com/sobolevn/git-secret/blob/master/utils/apk/meta.sh)

```sh
sh -c "echo 'https://gitsecret.jfrog.io/artifactory/git-secret-apk/all/main'" >> /etc/apk/repositories
wget -O /etc/apk/keys/git-secret-apk.rsa.pub 'https://gitsecret.jfrog.io/artifactory/api/security/keypair/public/repositories/git-secret-apk'
apk add --update --no-cache git-secret

# Testing, that it worked:
git secret --version

```

___

### Arch Linux

The _Arch_ way to install git-secret is to use the directions for “Installing Packages” at [Arch User Repository Documentation](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) along with the `PKGBUILD` file from the [git-secret Arch Linux Package](https://aur.archlinux.org/packages/git-secret/)

You can also install from the [AUR](https://aur.archlinux.org/) using your helper of choice by installing the package `git-secret`, for example using [yay](https://github.com/Jguer/yay)

```sh
yay -S git-secret
```

___

### Manual

```sh
git clone https://github.com/sobolevn/git-secret.git git-secret
cd git-secret && make build
PREFIX="/usr/local" make install
```

Note that you can install to any prefix in your `PATH`