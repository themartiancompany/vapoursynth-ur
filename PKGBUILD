# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: sl1pkn07 <sl1pkn07@gmail.com>
# Contributor: jackoneill <cantabile.desu@gmail.com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg="vapoursynth"
pkgname="${_pkg}"
pkgver=R70
pkgrel=2
pkgdesc='A video processing framework with the future in mind'
arch=(
  'x86_64'
  'arm'
  'armv7l'
  'armv6l'
  'aarch64'
  'mips'
  'i686'
  'pentium4'
)
url="http://www.${_pkg}.com"
license=(
  LGPL2.1
  custom:OFL
)
depends=(
  "libzimg.so"
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
)
makedepends=(
  "cython"
  "git"
  "${_py}-sphinx"
)
provides=(
  "${_py}-${_pkg}=${pkgver}"
)
conflicts=(
  "${_py}-${_pkg}"
)
_tag="03c8b6719f202b162284f53efc5b50632f70f72e"
_http="https://github.com"
_ns="${_pkg}"
_url="${_http}/${_ns}/${_pkg}"
source=(
  "git+${_url}.git#tag=${_tag}"
  "${_pkg}.xml"
)
b2sums=(
  '73fd9204744ceaa5c280986dfe2916533cdf0fc844313228f2d4a08ac1de8a9e7035f2c944655b566b9bae43ced53c33d411f54addfe07db199592a875df6b51'
  'feae23a22f8589177f30c36bdf21bab93d55a786194d3e0e958537016630d075b82178f60ac840f30ae316a8f87d3fb01f371211f62d1fee9850ee5063561747'
)

pkgver() {
  cd \
    "${_pkg}"
  git \
    describe \
    --tags
}

prepare() {
  cd \
    "${_pkg}"
  ./autogen.sh
}

build() {
  cd \
    "${_pkg}"
  ./configure \
    --prefix=/usr \
    --disable-static
  sed \
    -i \
    -e \
      's/ -shared / -Wl,-O1,--as-needed\0/g' \
      libtool
  make
}

package() {
  cd \
    "${_pkg}"
  make \
    DESTDIR="${pkgdir}" \
    install
  install \
    -Dm644 \
    src/core/ter-116n.ofl.txt \
    -t \
    "${pkgdir}/usr/share/licenses/${_pkg}/"
  install \
    -Dm644 \
    "../${_pkg}.xml" \
    -t \
    "${pkgdir}/usr/share/mime/packages/"
}

# vim: ts=2 sw=2 et:
