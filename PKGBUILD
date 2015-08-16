# Maintainer: dtw <dibble.at.thewrecker.dot.net>

pkgname=lrmi
pkgver=0.10
pkgrel=2
pkgdesc="Library for calling real mode BIOS routines under Linux"
arch=('i686')
url="http://sourceforge.net/projects/lrmi"
license=('MIT')
depends=('glibc')
makedepends=()
source=(http://downloads.sourceforge.net/$pkgname/$pkgname-$pkgver.tar.gz lrmi.patch LICENSE)
md5sums=('fc1d9495e8f4563fca471bb65f34a5da' 'cf6f7ea81f5e87be60bebdf7544eda2e' 'be32f188c975ecc5b2f032df68a5760e')

build() {
  cd $startdir/src/$pkgname-$pkgver

  patch -p1 < $srcdir/lrmi.patch
  make || return 1
  
  mkdir -p $startdir/pkg/usr/{lib,include,bin}
  install -m 755 liblrmi.so.0.10 $startdir/pkg/usr/lib/liblrmi.so.0.10
  rm -f $startdir/pkg/usr/lib/liblrmi.so
  ln -sf /usr/lib/liblrmi.so.0.10 $startdir/pkg/usr/lib/liblrmi.so.0
  ln -sf /usr/lib/liblrmi.so.0 $startdir/pkg/usr/lib/liblrmi.so
  install -m 644 lrmi.h $startdir/pkg/usr/include/lrmi.h
  install -m 755 vbetest $startdir/pkg/usr/bin/vbetest

  install -Dm644 ${srcdir}/LICENSE ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
}
