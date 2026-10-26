---
title: Arch Linux
description: Add the URepo repository to pacman and install packages.
section: Installation
order: 1
---

## 1. Add the repository

Add this to the end of `/etc/pacman.conf`:

```ini
[universalrepository]
SigLevel = Required TrustedOnly
Server = https://universalrepo.pages.dev/arch/
```

## 2. Import the key and sync

Download and import the public key:

```sh
curl -fLo universalrepository.asc https://downloads.sourceforge.net/project/universalrepository/arch/universalrepository.asc
sudo pacman-key --add universalrepository.asc
```

Check its fingerprint:

```sh
sudo pacman-key --finger C57FBE5A22ED5000C8149B21A7CA149CF8A6B28C
```

It should match `C57F BE5A 22ED 5000 C814 9B21 A7CA 149C F8A6 B28C`. If it does, sign the key locally to trust it:

```sh
sudo pacman-key --lsign-key C57FBE5A22ED5000C8149B21A7CA149CF8A6B28C
rm universalrepository.asc
```

Sync the repositories and update your system:

```sh
sudo pacman -Syu
```

## 3. Install packages

```sh
sudo pacman -S universalrepository/limine-entry-tool
```

List all packages in the repository:

```sh
pacman -Sl universalrepository
```
