---
title: Introduction
description: What UniversalRepository is and which distributions it supports.
section: Getting started
order: 1
---

UniversalRepository (URepo) maintains native packages for several Linux distributions in one unified system.

Build definitions, package templates and source patches for every package live in the [packages repository](https://github.com/UniversalRepository/packages). Built and signed binary packages are published on [SourceForge](https://sourceforge.net/projects/universalrepository).

Currently only `x86_64` targets are supported.

## Supported distributions

| Distribution       | Path                           | Format        | Build tool | Status      |
| ------------------ | ------------------------------ | ------------- | ---------- | ----------- |
| Arch Linux         | `arch/pkgs`                    | `PKGBUILD`    | `makepkg`  | Supported   |
| Void Linux (glibc) | `void/srcpkgs`                 | `template`    | `xbps-src` | Supported   |
| Fedora / openSUSE  | `rpm/specs`                    | `SPEC`        | `rpmbuild` | In progress |
| Chimera Linux      | `chimera/main`, `chimera/user` | `template.py` | `cbuild`   | Supported   |

## Where to go next

- To use the repository, follow the install guide for your distribution: [Arch Linux](/wiki/install/arch) or [Void Linux](/wiki/install/void).
- To build a package yourself, see [Building natively](/wiki/build/native) or [Building in a container](/wiki/build/container).
- To help out, read [Contributing](/wiki/contribute).
