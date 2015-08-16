# Maintainer: Mike Swanson <mikeonthecomputer@gmail.com>
# Contributor: Paul Burton <paulburton89@gmail.com>

pkgname=mingw32-sdl_net
pkgver=1.2.8
pkgrel=2
pkgdesc="A small sample cross-platform networking library (mingw32)"
arch=('i686' 'x86_64')
url="http://www.libsdl.org/projects/SDL_net/"
license=('zlib')
depends=('mingw32-sdl')
makedepends=('mingw32-gcc')
options=(!buildflags !strip)
source=(http://www.libsdl.org/projects/SDL_net/release/SDL_net-$pkgver.tar.gz)
sha256sums=('5f4a7a8bb884f793c278ac3f3713be41980c5eedccecff0260411347714facb4')

build() {
  cd "${srcdir}/SDL_net-${pkgver}"

  unset LDFLAGS # mingw-ld chokes on the makepkg default: --hash-style

  PKG_CONFIG_PATH=/usr/i486-mingw32/lib/pkgconfig \
  ./configure --host=i486-mingw32 \
  --prefix=/usr/i486-mingw32 \
  || return 1

  make || return 1
}

package() {
  cd "${srcdir}/SDL_net-${pkgver}"
  make DESTDIR="${pkgdir}" install
}

