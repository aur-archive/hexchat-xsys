# Maintainer: TingPing <tingping@tingping.se>
# Contributor: Gökmen Görgen <gkmngrgn_gmail.com>
pkgname=hexchat-xsys
pkgver=2.2.0
pkgrel=1
pkgdesc="Sysinfo plugin without audacious for Hexchat"
url="http://dev.gentoo.org/~chainsaw/xsys"
depends=('hexchat' 'pciutils')
arch=('i686' 'x86_64')
source=(http://dev.gentoo.org/~chainsaw/xsys/download/xsys-$pkgver.tar.bz2 xchat-xsys-archlinux.patch no-audacious.patch)
md5sums=('d57def00f96c7389ab593c009595f6f4' '01e5839f8980ba5b3ce7c0aae743ba36' '588e5f6d9037a07385079a5cf6ee2dbe')
license=('GPL')

build() {
  cd $srcdir/xsys-$pkgver
  patch -p1 -i ../no-audacious.patch
  sed -i -e "s:/usr/share/misc/:/usr/share/hwdata/:" Makefile
  sed -i -e "s:-O2 -Wall:${CFLAGS} -Wall:" Makefile
  sed -i -e "s:#BUTTON:BUTTON:" Makefile
  sed -i -e "s:# FOR AUDACIOUS # ::g" Makefile
  patch -p1 -i ../xchat-xsys-archlinux.patch
  make
  install -D "xsys-$pkgver.so" "$pkgdir/usr/lib/hexchat/plugins/xsys.so"
}
