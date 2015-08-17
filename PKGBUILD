# Maintainer: Buce <dmbuce@gmail.com>
# Contributor: Buce <dmbuce@gmail.com>
pkgname=pixelmap
pkgver=0.85
pkgrel=3
pkgdesc="An application designed to create bitmap images of Minecraft Beta worlds in various different styles"
url="http://www.minecraftforum.net/topic/69883-pixelmap/"
license=('CC BY-SA')
arch=('i686' 'x86_64')
source=(http://dl.dropbox.com/u/8304300/Minecraft/archive/0.85/PixelMap_Source.tar.gz LICENSE)
depends=('libpng14' 'zlib')
backup=()
md5sums=('c260ae3cbad305f5d63cfa2e13310901' '6fc00c1bb9f2109ae2941cbbc264c908')

_pkgver=${pkgver/./}

build() {
  cd "$srcdir/PixelMap_Source_$_pkgver"
  sed -i 's/-lpng/-lpng14 -lz/; s/#include <png.h>/#include <libpng14\/png.h>/' *
  make
  make DESTDIR="$pkgdir/" install
}

package() {
  cd "$srcdir/PixelMap_Source_$_pkgver"
  install -D -m 755 pixelmap "$pkgdir/usr/bin/pixelmap"
  install -D -m 644 $srcdir/LICENSE "$pkgdir/usr/share/licenses/pixelmap/LICENSE"
}

