# Contributor: DaNiMoTh <jjdanimoth@gmail.com>
# Contributor: Andrea Scarpino <bash.lnx@gmail.com>
# Contributor: Gereon Schomber
# Maintainer: Alex Belanger (nitrix) <i.caught.air@gmail.com>

pkgname=libace
pkgver=6.0.7
pkgrel=1
pkgdesc="Framework that provides many components and patterns for developing high-performance, distributed real-time and embedded systems."
url="http://www.cs.wustl.edu/~schmidt/ACE.html"
license=('custom')
arch=('i686' 'x86_64')
depends=('gcc')
options=(!libtool)
conflicts=('ace')
source=(http://download.dre.vanderbilt.edu/previous_versions/ACE-${pkgver}.tar.gz
        license.txt)

build() {
  export ACE_ROOT=$srcdir/ACE_wrappers
  cd $ACE_ROOT
  echo '#include "ace/config-linux.h"' > ace/config.h
  echo 'INSTALL_PREFIX = /usr
  include $(ACE_ROOT)/include/makeinclude/platform_linux.GNU' > include/makeinclude/platform_macros.GNU
  cd ace
  make || return 1
}
package() {
  cd $srcdir/ACE_wrappers/ace
  make DESTDIR="$pkgdir/" install
}
sha1sums=('6d20e63d213b0cb30df9d313143f2f6d91ea824c'
          'b21054d0aa546fabe4bb0c2769401314d4a5bfe3')
