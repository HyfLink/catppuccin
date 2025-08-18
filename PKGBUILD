pkgname="catppuccin"
pkgver=0.2.0
pkgrel=1
pkgdesc="catppuccin"
arch=("any")
url="https://catppuccin.com"
license=("MIT")
optdepends=(
    "alacritty"
    "bat"
    "bottom"
    "catppuccin-cursors-latte" "catppuccin-cursors-frappe" "catppuccin-cursors-macchiato" "catppuccin-cursors-mocha"
    "delta"
    "fcitx5-configtool" "fcitx5-gtk" "fcitx5-rime" "catppuccin-fcitx5-git"
    "fuzzel"
    "fzf"
    "imv"
    "kitty"
    "kvantum-theme-catppuccin-git"
    "lsd"
    "mako"
    "mpv"
    "papirus-folders-catppuccin-git"
    "qbittorrent"
    "catppuccin-qt5ct-git"
    "qtcreator"
    "thunderbird"
    "yazi"
)
makedepends=("deno" "just" "catppuccin-whiskers-bin")
source=(
    "git+https://github.com/catppuccin/alacritty"
    "git+https://github.com/catppuccin/bat"
    "git+https://github.com/catppuccin/bottom"
    "git+https://github.com/catppuccin/delta"
    "git+https://github.com/catppuccin/fuzzel"
    "git+https://github.com/catppuccin/fzf"
    "git+https://github.com/catppuccin/imv"
    "git+https://github.com/catppuccin/kitty"
    "git+https://github.com/catppuccin/lsd"
    "git+https://github.com/catppuccin/mako"
    "git+https://github.com/catppuccin/mpv"
    "git+https://github.com/catppuccin/qbittorrent"
    "git+https://github.com/catppuccin/qtcreator"
    "git+https://github.com/catppuccin/thunderbird"
    "git+https://github.com/catppuccin/yazi"
)
sha256sums=(
    "SKIP" # "git+https://github.com/catppuccin/alacritty"
    "SKIP" # "git+https://github.com/catppuccin/bat"
    "SKIP" # "git+https://github.com/catppuccin/bottom"
    "SKIP" # "git+https://github.com/catppuccin/delta"
    "SKIP" # "git+https://github.com/catppuccin/fuzzel"
    "SKIP" # "git+https://github.com/catppuccin/fzf"
    "SKIP" # "git+https://github.com/catppuccin/imv"
    "SKIP" # "git+https://github.com/catppuccin/kitty"
    "SKIP" # "git+https://github.com/catppuccin/lsd"
    "SKIP" # "git+https://github.com/catppuccin/mako"
    "SKIP" # "git+https://github.com/catppuccin/mpv"
    "SKIP" # "git+https://github.com/catppuccin/qbittorrent"
    "SKIP" # "git+https://github.com/catppuccin/qtcreator"
    "SKIP" # "git+https://github.com/catppuccin/thunderbird"
    "SKIP" # "git+https://github.com/catppuccin/yazi"
)
flavors=("latte" "frappe" "macchiato" "mocha")
accents=("rosewater" "flamingo" "pink" "mauve" "red" "maroon" "peach" "yellow" "green" "teal" "sky" "sapphire" "blue" "lavender")

build() {
    cd "$srcdir/alacritty"   && whiskers alacritty.tera
    cd "$srcdir/bat"         && deno task build
    cd "$srcdir/bottom"      && just build
    cd "$srcdir/delta"       && whiskers delta.tera
    cd "$srcdir/fuzzel"      && just build
    cd "$srcdir/fzf"         && whiskers templates/bash-zsh.tera
    cd "$srcdir/kitty"       && just build
    cd "$srcdir/lsd"         && whiskers lsd.tera
    cd "$srcdir/mako"        && just build
    cd "$srcdir/mpv"         && whiskers mpv.tera
    cd "$srcdir/qbittorrent" && just package
    cd "$srcdir/thunderbird" && env -S deno run --allow-read --allow-write --allow-env build.ts
    cd "$srcdir/yazi"        && just build
}

package() {
    destDir="$pkgdir/usr/share/catppuccin"
    install -Ddvm755 $destDir

    alacrittyDir="$destDir/alacritty"
    install -dvm755 $alacrittyDir
    install -m644 "$srcdir/alacritty/README.md" $alacrittyDir

    batDir="$destDir/bat"
    install -dvm755 $batDir
    install -m644 "$srcdir/bat/README.md" $batDir

    bottomDir="$destDir/bottom"
    install -dvm755 $bottomDir
    install -m644 "$srcdir/bottom/README.md" $bottomDir

    deltaDir="$destDir/delta"
    install -dvm755 $deltaDir
    install -m644 "$srcdir/delta/README.md" $deltaDir
    install -m644 "$srcdir/delta/catppuccin.gitconfig" $deltaDir

    fuzzelDir="$destDir/fuzzel"
    install -dvm755 $fuzzelDir
    install -m644 "fuzzel/README.md" $fuzzelDir

    fzfDir="$destDir/fzf"
    install -dvm755 $fzfDir
    install -m644 "$srcdir/fzf/README.md" $fzfDir

    imvDir="$destDir/imv"
    install -dvm755 $imvDir
    install -m644 "$srcdir/imv/README.md" $imvDir

    kittyDir="$destDir/kitty"
    install -dvm755 $kittyDir
    install -m644 "$srcdir/kitty/README.md" $kittyDir

    lsdDir="$destDir/lsd"
    install -dvm755 $lsdDir
    install -m644 "$srcdir/lsd/README.md" $lsdDir

    makoDir="$destDir/mako"
    install -dvm755 $makoDir
    install -m644 "$srcdir/mako/README.md" $makoDir

    mpvDir="$destDir/mpv"
    install -dvm755 $mpvDir
    install -m644 "$srcdir/mpv/README.md" $mpvDir

    qbittorrentDir="$destDir/qbittorrent"
    install -dvm755 $qbittorrentDir
    install -m644 "$srcdir/qbittorrent/README.md" $qbittorrentDir

    qtcreatorDir="$pkgdir/usr/share/qtcreator"
    install -Ddvm755 "$qtcreatorDir/themes"
    install -Ddvm755 "$qtcreatorDir/styles"
    install -m644 "$srcdir/qtcreator/README.md" $qtcreatorDir

    thunderbirdDir="$pkgdir/usr/lib/thunderbird/extensions/"
    install -Ddvm755 $thunderbirdDir

    yaziDir="$destDir/yazi"
    install -dvm755 $yaziDir
    install -m644 "$srcdir/yazi/README.md" $yaziDir

    for flavor in ${flavors[@]}; do
        install -m644 "$srcdir/alacritty/catppuccin-$flavor.toml" $alacrittyDir
        install -m644 "$srcdir/bat/themes/Catppuccin ${flavor^}.tmTheme" $batDir
        install -m644 "$srcdir/bottom/themes/$flavor.toml" $bottomDir
        install -m644 "$srcdir/fzf/themes/catppuccin-fzf-$flavor.sh" $fzfDir
        install -m644 "$srcdir/imv/themes/$flavor.config" $imvDir
        install -m644 "$srcdir/kitty/themes/$flavor.conf" $kittyDir
        install -m644 "$srcdir/kitty/themes/diff-$flavor.conf" $kittyDir
        install -Tm644 "$srcdir/lsd/themes/catppuccin-$flavor/colors.yaml" "$lsdDir/catppuccin-$flavor.yaml"
        install -m644 "$srcdir/qbittorrent/dist/catppuccin-$flavor.qbtheme" $qbittorrentDir
        install -m644 "$srcdir/qtcreator/styles/catppuccin-$flavor.xml" "$qtcreatorDir/styles"
        install -m644 "$srcdir/qtcreator/themes/catppuccin-$flavor.creatortheme" "$qtcreatorDir/themes"
        install -m644 "$srcdir/qtcreator/themes/catppuccin-$flavor.figmatokens" "$qtcreatorDir/themes"

        for accent in ${accents[@]}; do
            install -Tm644 "$srcdir/fuzzel/themes/catppuccin-$flavor/$accent.ini" "$fuzzelDir/catppuccin-$flavor-$accent.ini"
            install -m644 "$srcdir/mako/themes/catppuccin-$flavor/catppuccin-$flavor-$accent" $makoDir
            install -Tm644 "$srcdir/mpv/themes/$flavor/$accent.conf" "$mpvDir/catppuccin-$flavor-$accent.conf"
            install -m644 "$srcdir/thunderbird/themes/$flavor/$flavor-$accent.xpi" $thunderbirdDir
            install -m644 "$srcdir/yazi/themes/$flavor/catppuccin-$flavor-$accent.toml" $yaziDir
        done
    done
}
