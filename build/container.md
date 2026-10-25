---
title: Building in a container
description: Build packages in a Podman or Docker container to keep your host clean.
section: Build and contribute
order: 2
---

A container keeps build tooling off your host system. The commands below assume rootless Podman and can be adapted for Docker.

## 1. Build the container image

If you use Docker, first run:

```sh
cp .containerignore .dockerignore
```

Then build the image:

```sh
podman build --file Containerfile --build-arg "BUILDER_UID=$(id -u)" --build-arg "BUILDER_GID=$(id -g)" --tag localhost/urepo-builder:local .
```

The first build can take a while. Later rebuilds reuse cached layers.

## 2. Prepare signing keys

Builds sign their output, so you need a key for each distribution.

| Distribution | Signing key     | Key format                                          |
| ------------ | --------------- | --------------------------------------------------- |
| Void         | `keys/void.pem` | RSA private key in PEM format                       |
| Arch         | `keys/arch.key` | OpenPGP private key export, ASCII armored or binary |

## 3. Build packages

Start the container:

```sh
podman run --rm -it --privileged \
    --userns=keep-id --user builder \
    --volume "$PWD:/workspace" \
    localhost/urepo-builder:local
```

To build for Void Linux, start it with these extra variables instead:

```sh
podman run --rm -it --privileged \
    --userns=keep-id --user builder \
    --volume "$PWD:/workspace" \
    --env UREPO_VOID_SIGNED_BY=UniversalRepository \
    --env UREPO_VOID_CHROOT_CMD=bwrap \
    localhost/urepo-builder:local
```

Inside the container, name a distribution and a package:

```sh
./urepo build void/svc
```

Targets from different distributions can be built in one command:

```sh
./urepo build void/foo arch/bar
```
