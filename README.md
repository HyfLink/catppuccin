# CATPPUCCIN

[Catppuccin] themes for Arch Linux.

[Catppuccin]: https://catppuccin.com

## Install

1. Clone the repository.

```sh
git clone https://github.com/HyfLink/catppuccin.git
```

2. Install the meta package.

```sh
cd catppuccin
# add `--force` option to re-build the package.
makepkg --install
```

3. Install make-dependencies.
```sh
# install from AUR by `paru` or `yay`.
paru -S --asdeps --needed catppuccin-whiskers-bin
# you can uninstall the make-dependencies after installation.
```

4. Install catppuccin theme for specific package.

```sh
# (1) install for specific package (`yazi` for example).
#
# add `--force` option to re-build the package.
makepkg --install --syncdeps --asdeps -D catppuccin-yazi

# (2) or install all packages.
for PACKAGE in $(find . -maxdepth 1 -type d | grep catppuccin); do
    makepkg --syncdeps --install --asdeps -D $PACKAGE
done
```
