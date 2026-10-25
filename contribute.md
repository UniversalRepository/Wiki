---
title: Contributing
description: Where package sources live and how to send changes.
section: Build and contribute
order: 3
---

UniversalRepository is open source under the MIT license. Package sources, issues and pull requests are handled on [GitHub](https://github.com/UniversalRepository/packages).

## Where things live

Each distribution keeps its package definitions in its own directory:

| Distribution       | Directory                      |
| ------------------ | ------------------------------ |
| Arch Linux         | `arch/pkgs`                    |
| Void Linux (glibc) | `void/srcpkgs`                 |
| Fedora / openSUSE  | `rpm/specs`                    |
| Chimera Linux      | `chimera/main`, `chimera/user` |

## Sending a change

1. Fork the [packages repository](https://github.com/UniversalRepository/packages) and make your change in the directory for your distribution.
2. Build the package to check it works, either [natively](/wiki/build/native) or [in a container](/wiki/build/container).
3. Open a pull request.

To report a problem with a package or ask for a new one, open an issue on the same repository.
