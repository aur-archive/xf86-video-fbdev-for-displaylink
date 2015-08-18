# Maintainer: Alexander Ost <displaylink-aur at post2 dot 25u dot com>
# Contributor: Arthur L. Andersen <leoc.git at gmail dot com>
#
pkgname=xf86-video-fbdev-for-displaylink
pkgver=dbfe3f839ee00135a7cccf13
pkgrel=4
pkgdesc="Branch of http://cgit.freedesktop.org/xorg/driver/xf86-video-fbdev/ with proposed 
extensions to replace custom DisplayLink driver"
arch=(i686 x86_64)
url="http://git.plugable.com/gitphp/index.php?p=udlfb&a=summary"
license=('GPLv2')
makedepends=(xorg-server-devel)
depends=(libusb)
options=(!distcc)
source=("xf86-video-fbdev.tar::http://git.plugable.com/gitphp/index.php?p=xf86-video-fbdev&a=snapshot&h=dbfe3f839ee00135a7cccf13db5926fb1019abde"
	"000-plugable-042-to-043.patch"
	"001-mibstore.patch" )
md5sums=('3533188e7193ef81a34705c320244c4a'
	 '9f121aeb3dd488e672953de9d9a7a21e'
	 '9defb13a8fcb51a2ffcec786b36766b3')

build() {
ln -sf xf86-video-fbdev $srcdir/$pkgname
cd "$srcdir/$pkgname"
patch -p1 < $srcdir/000-plugable-042-to-043.patch
patch -p1 < $srcdir/001-mibstore.patch
./autogen.sh || return 1
make || return 1
}

package() {
cd "$srcdir/$pkgname"

make DESTDIR="$pkgdir/" install || return 1
} 
