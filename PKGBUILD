# Original author: Thomas Sowell <tom@fancydriving.org>
# Maintained by Joseph Riches

pkgname=libgestures
pkgdesc="Chromium OS gestures library"
pkgver=2.0.3
pkgrel=5
arch=(i686 x86_64)
url="http://github.com/galliumos/libgestures"
license=('custom:chromiumos')
_gitname='libgestures'
provides=('libgestures=$pkgver')
depends=('jsoncpp')
makedepends=('git')

source=("$_gitname::git+https://github.com/galliumos/libgestures.git"
        'finger_metrics_math.patch'
        'immediate_interpreter_bool.patch')

sha256sums=('SKIP'
            'b3b44fa166380ee57b3de48c294944a2e1e276a38d737d02004acb176a613b22'
            '83c1d496ea2a685d54690c503d48f0e8a42c5aa7077b5c1f743b7567a411aa50')

prepare() {
  cp "$startdir"/finger_metrics_math.patch "$srcdir/$_gitname"
  cd "$srcdir/$_gitname"
  patch -p1 < finger_metrics_math.patch
  patch -p1 < "$startdir"/immediate_interpreter_bool.patch
}

build() {
  cd "$srcdir/$_gitname"
  make
}

package() {
  make -C "$srcdir/$_gitname" DESTDIR="${pkgdir}" install
  rm -fr ${pkgdir}/etc

  install -m 644 -D ${srcdir}/${_gitname}/LICENSE ${pkgdir}/usr/share/license/${pkgname}/LICENSE
}
