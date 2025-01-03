# Docker Image Codenames

Notes regarding Alpine, Bookworm, Bullseye, Slim, etc..

## Alpine Distribution

* `apk` package manager.

### `alpine` Tag

* Simple and small.
* Uses musl libc and BusyBox.
* `/bin/sh`

## Debian Distribution

* `apt` package manager.

### `buster` Tag

* Debian 10
* Linux Kernel 4.19

### `bullseye` Tag

* Debian 11
* Linux Kernel 5.10

### `bookworm` Tag

* Debian 12
* Linux Kernel 6.1

## Ubuntu Distribution

* `apt` package manager.

### `focal` Tag

* Ubuntu 20.04
* Linux 5.4

### `jammy` Tag

* Ubuntu 22.04
* Linux 5.15

### `noble` Tag

* Ubuntu 24.04
* Linux 6.6

## `slim` Tag

* Debian and Ubuntu can use `slim` as a qualifier.
* Image size reduced from standard images.
* see [`slimify-includes`](https://github.com/debuerreotype/debuerreotype/blob/master/scripts/.slimify-includes) and [`slimify-excludes`](https://github.com/debuerreotype/debuerreotype/blob/master/scripts/.slimify-excludes) for more information.
