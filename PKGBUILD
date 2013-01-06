# Maintainer: Gerald Dachs <gda[at]dachsweb[dot]de>
pkgname=vdr-dynamite
pkgver=20130106
_gitver=914af249
_vdrapi=1.7.35
pkgrel=1yavdr1
pkgdesc="turns the dvbdevices into hotpluggable devices"
url="http://projects.vdr-developer.org/projects/show/plg-dynamite"
arch=('x86_64' 'i686')
license=('GPL2')
depends=('gcc-libs' "vdr-api=${_vdrapi}")
optdepends=()
_plugname=$(echo $pkgname | sed 's/vdr-//g')
replaces=("vdr-plugin-$_plugname")
conflicts=("vdr-plugin-$_plugname")
source=("http://projects.vdr-developer.org/git/vdr-plugin-$_plugname.git/snapshot/vdr-plugin-$_plugname-$_gitver.tar.bz2"
        "makefile.diff")
md5sums=('5e7673df92747412c7c30692cc9b8388'
         'efcc03bebe44c2536f516d6baf541d40')

package() {
  cd "${srcdir}/vdr-plugin-${_plugname}-${_gitver}"

  patch -p1 -i ${srcdir}/makefile.diff

  mkdir -p $pkgdir/usr/lib/vdr/plugins
  make CFLAGS="$(pkg-config vdr --variable=cflags)" \
       CXXFLAGS="$(pkg-config vdr --variable=cxxflags)" \
       VDRDIR="/usr/include/vdr" \
       LIBDIR="$pkgdir/$(pkg-config vdr --variable=libdir)" \
       LOCALEDIR="$pkgdir/$(pkg-config vdr --variable=locdir)"
}

