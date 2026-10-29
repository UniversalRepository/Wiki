---
title: Alpine Linux
description: Add the URepo repository to apk and install packages.
section: Installation
order: 5
---

Packages are built for edge only. Repositories use `alpine/main`, `alpine/community`, and `alpine/testing` on SourceForge.

### 1. Import the key
```bash
curl -fLo universalrepository.rsa.pub https://downloads.sourceforge.net/project/universalrepository/alpine/universalrepository.rsa.pub
doas install -m 644 universalrepository.rsa.pub /etc/apk/keys/
rm universalrepository.rsa.pub
```

### 2. Add the repository and sync
For packages in `community`:
```bash
echo 'https://downloads.sourceforge.net/project/universalrepository/alpine/community' | doas tee -a /etc/apk/repositories
doas apk update
```

### 3. Install packages
```bash
doas apk add noctalia
```


