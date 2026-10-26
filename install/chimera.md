---
title: Chimera Linux
description: Add the URepo repository to APK and install packages.
section: Installation
order: 3
---

## 1. Add the repository
This adds the `user` repository:
```sh
echo 'repository=https://universalrepo.pages.dev/chimera/user' | sudo tee /etc/apk/repositories.d/00-universalrepository.list
```

If using packages from `main`, add its URL to the same file once that repository contains packages:
```text
v3 https://universalrepo.pages.dev/chimera/main
```

## 2. Import the key and sync

Download and install our public key:
```bash
curl -fLo universalrepository.rsa.pub https://downloads.sourceforge.net/project/universalrepository/chimera/universalrepository.rsa.pub
sudo install -m 644 universalrepository.rsa.pub /etc/apk/keys/
rm universalrepository.rsa.pub
```

Sync the repositories:
```bash
sudo apk update
```

### 3. Packages

Now you can install a package from URepo:
```bash
sudo apk add umbriel
```

List packages in the `user` repository:
```bash
apk list --from none --repository https://downloads.sourceforge.net/project/universalrepository/chimera/user
```

For debug symbols, also add the following to the repository file and sync again:
```text
v3 https://downloads.sourceforge.net/project/universalrepository/chimera/user/debug
```

Then install the corresponding debug package:
```bash
sudo apk add umbriel-dbg
```
