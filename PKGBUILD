# Maintainer: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: sl1pkn07 <sl1pkn07@gmail.com>
# Contributor: jackoneill <cantabile.desu@gmail.com>

pkgname=vapoursynth
pkgver=R29
pkgrel=1
pkgdesc='A video processing framework with the future in mind'
arch=('i686' 'x86_64')
url='http://www.vapoursynth.com/'
license=('LGPL2.1' 'custom:OFL')
depends=('gcc-libs' 'glibc' 'imagemagick' 'libass' 'python' 'shared-mime-info'
         'tesseract'
         'libzimg.so')
makedepends=('cython' 'python-sphinx' 'yasm')
install='vapoursynth.install'
source=("vapoursynth-${pkgver}.tar.gz::https://github.com/vapoursynth/vapoursynth/archive/${pkgver}.tar.gz"
        'vapoursynth.xml')
sha256sums=('5a2e37f3a9a5dc60f55a301b222df75a580ccf319b099a3e421e2334ef8cbde6'
            '8e51579547d20cd7cb9618a47b3ac508423d09d76649bf038d0ab9acb850b068')

build() {
  cd vapoursynth-${pkgver}

  ./autogen.sh
  ./configure \
    --prefix='/usr' \
    --enable-imwri \
    --disable-static
  make
}

package() {
  cd vapoursynth-${pkgver}

  make DESTDIR="${pkgdir}" install

  install -dm 755 "${pkgdir}"/usr/share/{licenses/vapoursynth,mime/packages}
  install -m 644 ofl.txt "${pkgdir}"/usr/share/licenses/vapoursynth/
  install -m 644 ../vapoursynth.xml "${pkgdir}"/usr/share/mime/packages/
}

# vim: ts=2 sw=2 et:
