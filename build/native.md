---
title: Building natively
description: Build a package on your own system with the urepo entry point.
section: Build and contribute
order: 1
---

Builds go through the `urepo` entry point at the root of the [packages repository](https://github.com/UniversalRepository/packages):

```sh
./urepo build distro/package
```

For example, to build the `svc` package for Void Linux:

```sh
./urepo build void/svc
```

This assumes your host system's `$PATH` contains the tooling needed for the chosen target, whichever distribution you are running.

> If you would rather not clutter your system with build tooling, use a [container build](/wiki/build/container) instead.
