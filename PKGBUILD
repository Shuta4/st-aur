# Maintainer: Shuta4 <shuta4@proton.me>

_pkgname=st
pkgname="s4-$_pkgname"
pkgver=0.8.4
pkgrel=1
pkgdesc="A simple terminal emulator for X custom build"
url="https://github.com/Shuta4/st"
arch=('i686' 'x86_64' 'arm' 'armv7h' 'armv6h' 'aarch64')
license=('MIT')
options=(zipman)
depends=(
	'libx11'
	'libxft'
	'ttf-jetbrains-mono'
	'ttf-joypixels'
)
source=("https://github.com/Shuta4/$_pkgname/archive/refs/tags/$pkgver-$pkgrel.tar.gz")
sha256sums=('31f0610b611ce33f151e103ebbcb029055331f437a3f69d345d753e9325d2cc5')

provides=("${_pkgname}")
conflicts=("${_pkgname}")

prepare() {
  cd "$srcdir/$_pkgname-$pkgver-$pkgrel"
  sed '/tic/d' -i Makefile
}

build() {
  cd "$srcdir/$_pkgname-$pkgver-$pkgrel"
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd "$srcdir/$_pkgname-$pkgver-$pkgrel"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$_pkgname/LICENSE"
  install -Dm644 README.md "$pkgdir/usr/share/doc/$_pkgname/README.md"
  install -Dm644 -t "$pkgdir/user/share/$pkgname" st.info
}
