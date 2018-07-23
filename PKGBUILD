# Maintainer: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: sl1pkn07 <sl1pkn07@gmail.com>
# Contributor: jackoneill <cantabile.desu@gmail.com>

pkgname=vapoursynth
pkgver=R44
pkgrel=2
pkgdesc='A video processing framework with the future in mind'
arch=('x86_64')
url='http://www.vapoursynth.com/'
license=('LGPL2.1' 'custom:OFL')
depends=('libmagick' 'python' 'tesseract'
         'libass.so' 'libavcodec.so' 'libavformat.so' 'libavutil.so' 'libzimg.so')
makedepends=('cython' 'git' 'nasm' 'python-sphinx')
source=("git+https://github.com/vapoursynth/vapoursynth.git#tag=${pkgver}"
        'vapoursynth.xml')
sha256sums=('SKIP'
            '8e51579547d20cd7cb9618a47b3ac508423d09d76649bf038d0ab9acb850b068')

build() {
  cd vapoursynth

  ./autogen.sh
  ./configure \
    --prefix='/usr' \
    --enable-imwri \
    --disable-static
  sed -i -e 's/ -shared / -Wl,-O1,--as-needed\0/g' libtool
  make
}

package() {
  cd vapoursynth

  make DESTDIR="${pkgdir}" install

  install -Dm 644 ofl.txt -t "${pkgdir}"/usr/share/licenses/vapoursynth/
  install -Dm 644 ../vapoursynth.xml -t "${pkgdir}"/usr/share/mime/packages/
}

# vim: ts=2 sw=2 et:
