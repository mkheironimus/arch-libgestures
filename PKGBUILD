# Maintainer: Felix Golatofski <contact@xdfr.de>
# Contributor: Thomas Sowell <tom@fancydriving.org>
# Contributor: Joseph Riches

pkgname=libgestures
pkgdesc="Chromium OS gestures library"
pkgver=2.1.14
pkgrel=6
arch=(i686 x86_64)
url="https://github.com/galliumos/libgestures"
license=('custom:chromiumos')
provides=('libgestures=$pkgver')
depends=('jsoncpp')
makedepends=('git')
source=("https://launchpad.net/~eugenesan/+archive/ubuntu/ppa/+sourcefiles/libgestures/$pkgver-1ubuntu2~eugenesan~xenial3/libgestures_$pkgver.orig.tar.gz"
	"cmath_everywhere.patch"
	"class_memaccess_noerror.patch"
	"cmath_add.patch"
	"int_in_bool.patch")
sha256sums=('e19aed2ae404871b0ee6272129a3f4c413ca004dd7dd81af87c7cc596d6d94e5'
            '4ce7bd11ba4b5aa4b5328f5c4a4dd6f59e283427ebd73a462ee526f6779f63d9'
            'db56ab1d0375765fe5ffe3bec72e6e7f662b035155fdc62f1f7e2c9ae3f01989'
	    '12a806fc26e98d9fe370d5274186a23ac8bd7377ced231fbcff27e06be787bf9'
	    '4a805529f12868c8baf7a9d1041cc94a7e1e35c4fbb5eb0da85e522825fb3cbe')

prepare() {
  cd "$srcdir/$pkgname-master"
  patch -p1 < $srcdir/cmath_everywhere.patch
  patch -p1 < $srcdir/class_memaccess_noerror.patch
  patch -p0 < $srcdir/cmath_add.patch
  patch -p0 < $srcdir/int_in_bool.patch
}

build() {
  cd "$srcdir/$pkgname-master"
  make
}

package() {
  make -C "$srcdir/$pkgname-master" DESTDIR="${pkgdir}" install
  rm -fr ${pkgdir}/etc

  install -m 644 -D ${srcdir}/${pkgname}-master/LICENSE ${pkgdir}/usr/share/license/${pkgname}/LICENSE
}
