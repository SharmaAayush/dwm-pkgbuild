# Maintainer: Piyush Pangtey <gokuvsvegita at gmail dot com>

pkgname=dwm
pkgver=mar19.e301ff8
pkgrel=1
_tagver="mar19"
pkgdesc="DWM by suckless"
arch=('x86_64')
url="https://dwm.suckless.org"
license=('MIT')
depends=('freetype2' 'libx11' 'libxcb' 'libxft')
makedepends=('make')
source=(
    "dwm::git+https://github.com/pangteypiyush/dwm"
)
sha256sums=(
    'SKIP'
)

pkgver() {
  cd "${pkgname}"
  printf "%s.%s" "$(git describe --tags)" "$(git rev-parse --short HEAD)"
}

prepare() {
	cd $pkgname
	git checkout $_tagver
}

build() {
    make -C "$pkgname"
}

package() {
    make -C "$pkgname" PREFIX="usr/" DESTDIR="$pkgdir/" install
    install -Dm644 "$pkgname/LICENSE" "$pkgdir/usr/share/doc/$pkgname/LICENSE"
    install -Dm644 "$pkgname/README" "$pkgdir/usr/share/doc/$pkgname/README"
}
