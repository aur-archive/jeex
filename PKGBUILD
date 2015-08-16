# Maintainer: boenki <boenki at gmx dot de>
# Contributor: carstene1ns <url/mail: arch carsten-teibes de>

pkgname=jeex
pkgver=12.6.1
pkgrel=3
pkgdesc="GTK+ Hex Editor"
arch=('i686' 'x86_64')
url="http://www.hds619.net/?ref=projects&sub=jeex"
license=('GPL3')
depends=('gtk2')
backup=(etc/jeex.rc)
source=("http://www.hds619.net/data/jeex/jeex-pkg/jeex-$pkgver.tar.bz2")
md5sums=('7a6035de61d04b0dabb4b31fc356ac52')

prepare() {
  sed -i '21a#include <string.h>' "jeex-${pkgver:0:4}/src/plugin.c"
}

build() {
  cd "jeex-${pkgver:0:4}"
  ./configure --prefix=/usr --sysconfdir=/etc
  make
}

check() {
  cd "jeex-${pkgver:0:4}"
  make check
}

package() {
  cd "jeex-${pkgver:0:4}"
  make DESTDIR="$pkgdir" install

  # fix directories
  cd "$pkgdir/usr/share"
  mv jeex/applications .
  mv jeex/icons pixmaps

  ln -sf ../jeex/images/jeex.png pixmaps/jeex.png
}