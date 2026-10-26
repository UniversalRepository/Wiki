---
title: Void Linux
description: Add the URepo repository to XBPS and install packages.
section: Installation
order: 2
---

## 1. Add the repository

```sh
echo 'repository=https://universalrepo.pages.dev/void' | sudo tee /etc/xbps.d/10-universalrepository.conf
```

## 2. Sync and import the key

```sh
sudo xbps-install -S
```

XBPS will ask you to import the public key. Confirm it only if the fingerprint is:

```text
0f:fa:c3:8e:fd:cd:c9:52:88:f0:34:ca:df:6c:c6:fa
```

## 3. Install packages

```sh
sudo xbps-install svc
```

List all packages in the repository:

```sh
xbps-query -iM --repository=https://sourceforge.net/projects/universalrepository/files/void -s ''
```
