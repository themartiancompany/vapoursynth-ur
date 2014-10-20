# Maintainer: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: sl1pkn07 <sl1pkn07@gmail.com>
# Contributor: jackoneill <cantabile.desu@gmail.com>

pkgname=vapoursynth
pkgver=R24
pkgrel=4
pkgdesc='A video processing framework with the future in mind'
arch=('i686' 'x86_64')
url='http://www.vapoursynth.com/'
license=('LGPL2.1' 'custom:OFL')
depends=('ffmpeg' 'python' 'shared-mime-info' 'tesseract')
makedepends=('cython' 'python-sphinx' 'yasm')
install='vapoursynth.install'
source=("vapoursynth-${pkgver}.tar.gz::https://github.com/vapoursynth/vapoursynth/archive/${pkgver}.tar.gz"
        'vapoursynth.xml')
sha256sums=('74920a3ae9f2a1ac65e509ba6531ee7c3c9e9b94f1b683f17764cd4d2022c7cf'
            '8e51579547d20cd7cb9618a47b3ac508423d09d76649bf038d0ab9acb850b068')

build() {
  cd vapoursynth-${pkgver}

  ./bootstrap.py
  ./waf configure --prefix='/usr'
  ./waf $MAKEFLAGS build
  python setup.py build
}

package() {
  cd vapoursynth-${pkgver}

  ./waf install --destdir="${pkgdir}"
  python setup.py install --root="${pkgdir}" --optimize='1'

  install -dm 755 "${pkgdir}"/usr/share/{licenses/vapoursynth,mime/packages}
  install -m 644 ofl.txt "${pkgdir}"/usr/share/licenses/vapoursynth/
  install -m 644 ../vapoursynth.xml "${pkgdir}"/usr/share/mime/packages/
}

# vim: ts=2 sw=2 et:
