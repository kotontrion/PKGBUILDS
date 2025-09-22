# Maintainer:
# Contributor: Gabriele Musco <gabmus@disroot.org>

_pkgname="blueprint-compiler"
pkgname="$_pkgname-git"
pkgver=0.18.0.r29.g3ee03cf
pkgrel=1
pkgdesc="A markup language for GTK user interfaces"
url="https://gitlab.gnome.org/jwestman/blueprint-compiler"
license=('LGPL-3.0-or-later')
arch=('any')

depends=(
  'libgirepository'
  'python'
  'python-gobject'
)
makedepends=(
  'git'
  'meson'
)
checkdepends=(
  'libadwaita'
  'xorg-server-xvfb'
)

provides=("$_pkgname=$pkgver")
conflicts=("$_pkgname")

_pkgsrc="$_pkgname"
source=("$_pkgsrc"::"git+$url.git")
sha256sums=('SKIP')

pkgver() {
  cd "$_pkgsrc"
  git describe --long --tags --abbrev=7 \
    | sed -E 's/^[^0-9]*//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  arch-meson "$_pkgsrc" build
  meson compile -C build
}

check() {
  dbus-run-session xvfb-run \
    -s '-screen 0 1920x1080x24 -nolisten local' \
    meson test -C build --print-errorlogs
}

package() {
  meson install -C build --destdir "$pkgdir"
}
