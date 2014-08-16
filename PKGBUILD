# Maintainer: Maxime Gauduin <alucryd@gmail.com>
# Contributor: sl1pkn07 <sl1pkn07@gmail.com>
# Contributor: jackoneill <cantabile.desu@gmail.com>

pkgname=vapoursynth
pkgver=R24
pkgrel=1
pkgdesc='A video processing framework with the future in mind'
arch=('i686' 'x86_64')
url='http://www.vapoursynth.com/'
license=('LGPL2.1' 'custom:OFL')
depends=('ffmpeg' 'python' 'tesseract')
makedepends=('cython' 'python-sphinx' 'waf' 'yasm')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/${pkgname}/${pkgname}/archive/${pkgver}.tar.gz")
sha256sums=('74920a3ae9f2a1ac65e509ba6531ee7c3c9e9b94f1b683f17764cd4d2022c7cf')

build() {
  cd ${pkgname}-${pkgver}

  waf configure --prefix='/usr' --enable-examples
  waf $MAKEFLAGS build
  python setup.py build
}

package() {
  cd ${pkgname}-${pkgver}

  waf install --destdir="${pkgdir}"
  python setup.py install --root="${pkgdir}" --optimize='1'

  install -dm 755 "${pkgdir}"/usr/share/licenses/${pkgname}
  install -m 644 ofl.txt "${pkgdir}"/usr/share/licenses/${pkgname}/
}

# vim: ts=2 sw=2 et:
