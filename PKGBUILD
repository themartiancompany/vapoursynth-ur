# Maintainer: Maxime Gauduin <alucryd@gmail.com>
# Contributor: sl1pkn07 <sl1pkn07@gmail.com>
# Contributor: jackoneill <cantabile.desu@gmail.com>

pkgname=vapoursynth
pkgver=R24
pkgrel=2
pkgdesc='A video processing framework with the future in mind'
arch=('i686' 'x86_64')
url='http://www.vapoursynth.com/'
license=('LGPL2.1' 'custom:OFL')
depends=('ffmpeg' 'python' 'shared-mime-info' 'tesseract')
makedepends=('cython' 'python-sphinx' 'waf' 'yasm')
install="${pkgname}.install"
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/${pkgname}/${pkgname}/archive/${pkgver}.tar.gz"
        "${pkgname}.xml")
sha256sums=('74920a3ae9f2a1ac65e509ba6531ee7c3c9e9b94f1b683f17764cd4d2022c7cf'
            '8e51579547d20cd7cb9618a47b3ac508423d09d76649bf038d0ab9acb850b068')

build() {
  cd ${pkgname}-${pkgver}

  waf configure --prefix='/usr'
  waf $MAKEFLAGS build
  python setup.py build
}

package() {
  cd ${pkgname}-${pkgver}

  waf install --destdir="${pkgdir}"
  python setup.py install --root="${pkgdir}" --optimize='1'

  install -dm 755 "${pkgdir}"/usr/share/{licenses/${pkgname},mime/packages}
  install -m 644 ofl.txt "${pkgdir}"/usr/share/licenses/${pkgname}/
  install -m 644 ../${pkgname}.xml "${pkgdir}"/usr/share/mime/packages/
}

# vim: ts=2 sw=2 et:
