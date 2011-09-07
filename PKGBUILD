# $Id: PKGBUILD 51616 2011-07-12 10:59:49Z spupykin $
# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Maintainer: Vesa Kaihlavirta <vegai@iki.fi>
# Contributor: Sebastian Sareyko <public@nooms.de>

pkgname=addresses
pkgver=0.4.6
pkgrel=8
pkgdesc="A versatile address book application for GNUstep"
arch=('i686' 'x86_64')
url="http://giesler.biz/bjoern/en/sw_addr.html"
license=('LGPL')
depends=('gnustep-back' 'gnustep-base' 'gnustep-gui')
makedepends=('gnustep-make' 'gcc-objc')
#source=(http://giesler.biz/bjoern/downloads/Addresses-$pkgver.tar.gz)
source=(http://arch.p5n.pp.ru/~sergej/dl/Addresses-$pkgver.tar.gz)
md5sums=('2d6b6bf9a1578a5b3a13cb0bd2c60fad')

build() {
  . /etc/profile.d/GNUstep.sh
  cd $srcdir/Addresses-$pkgver
  sed -i -e 's|Versions/A|Versions/0|g' {Test,AddressManager}/GNUmakefile
  make
}

package() {
  . /etc/profile.d/GNUstep.sh
  cd $srcdir/Addresses-$pkgver
  make GNUSTEP_INSTALLATION_DIR=$pkgdir/usr/lib/GNUstep INSTALL_ROOT_DIR=$pkgdir install
  # buggy install scripts
  cd $pkgdir/usr/lib/GNUstep/Library/Headers/
  rm AddressBook
  ln -sf Addresses AddressBook
  cd $pkgdir/usr/lib/GNUstep/Library/
  mv * ..
  cd .. && rmdir Library
}
