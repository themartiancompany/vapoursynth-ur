# Maintainer: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: sl1pkn07 <sl1pkn07@gmail.com>
# Contributor: jackoneill <cantabile.desu@gmail.com>

pkgname=vapoursynth
pkgver=R64
pkgrel=1
pkgdesc='A video processing framework with the future in mind'
arch=(x86_64)
url=http://www.vapoursynth.com/
license=(
  LGPL2.1
  custom:OFL
)
depends=(
  libzimg.so
  python
)
makedepends=(
  cython
  git
  python-sphinx
)
_tag=3c3271769030d3f9ce8f84df7bccb7c2db3e33c0
source=(
  git+https://github.com/vapoursynth/vapoursynth.git#tag=${_tag}
  vapoursynth.xml
)
b2sums=('SKIP'
        'feae23a22f8589177f30c36bdf21bab93d55a786194d3e0e958537016630d075b82178f60ac840f30ae316a8f87d3fb01f371211f62d1fee9850ee5063561747')

pkgver() {
  cd vapoursynth
  git describe --tags
}

prepare() {
  cd vapoursynth
  ./autogen.sh
}

build() {
  cd vapoursynth
  ./configure \
    --prefix=/usr \
    --disable-static
  sed -i -e 's/ -shared / -Wl,-O1,--as-needed\0/g' libtool
  make
}

package() {
  cd vapoursynth

  make DESTDIR="${pkgdir}" install

  install -Dm 644 src/core/ter-116n.ofl.txt -t "${pkgdir}"/usr/share/licenses/vapoursynth/
  install -Dm 644 ../vapoursynth.xml -t "${pkgdir}"/usr/share/mime/packages/
}

# vim: ts=2 sw=2 et:
