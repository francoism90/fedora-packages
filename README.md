# fedora-packages

RPM specs for Fedora, built on [COPR](https://copr.fedorainfracloud.org/coprs/francoism/fedora-packages/).

| Package | Upstream |
| --- | --- |
| kora-icon-theme | [bikass/kora](https://github.com/bikass/kora) |

## Install

```sh
sudo dnf copr enable francoism/fedora-packages
sudo dnf install kora-icon-theme
```

On Fedora Atomic, add the repo file to `/etc/yum.repos.d/` and use `rpm-ostree install`.

## Build locally

```sh
make -f .copr/Makefile srpm spec=packages/kora-icon-theme/kora-icon-theme.spec outdir=/tmp
```

Specs based on [c4i0b/fedora-packages](https://github.com/c4i0b/fedora-packages).
