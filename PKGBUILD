# Maintainer: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: sl1pkn07 <sl1pkn07@gmail.com>
# Contributor: jackoneill <cantabile.desu@gmail.com>

pkgname=vapoursynth
pkgver=R40
pkgrel=2
pkgdesc='A video processing framework with the future in mind'
arch=('x86_64')
url='http://www.vapoursynth.com/'
license=('LGPL2.1' 'custom:OFL')
depends=('gcc-libs' 'glibc' 'libmagick' 'python' 'tesseract'
         'libass.so' 'libavcodec.so' 'libavformat.so' 'libavutil.so' 'libzimg.so')
makedepends=('cython' 'python-sphinx' 'nasm')
source=("vapoursynth-${pkgver}.tar.gz::https://github.com/vapoursynth/vapoursynth/archive/${pkgver}.tar.gz"
        'vapoursynth.xml')
sha256sums=('a5e4260abff95c4bf33cc7ff3203e8001f7b3be7bb5ccc3a6fc2b18523823e50'
            '8e51579547d20cd7cb9618a47b3ac508423d09d76649bf038d0ab9acb850b068')

build() {
  cd vapoursynth-${pkgver}

  ./autogen.sh
  ./configure \
    --prefix='/usr' \
    --enable-imwri \
    --disable-static
  sed -i -e 's/ -shared / -Wl,-O1,--as-needed\0/g' libtool
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
