# $Id: PKGBUILD,v 1.0 2009/08/10 01:45:02 BaSh Exp $
# Maintainer: Kirurgs <kirurgs@one.lv>
# Contributor: Kirurgs <kirurgs@one.lv>

pkgname=networkmanager-pptp-git
pkgver=20090810
pkgrel=1
pkgdesc='Developement pptp plugin for networkmanager'
arch=('i686' 'x86_64')
url="http://www.gnome.org/projects/NetworkManager/"
license=('GPL')
depends=('pptpclient' 'network-manager-applet-git')
makedepends=('pkgconfig' 'gnome-common' 'intltool')
conflicts=('networkmanager-pptp')
source=()

_gitroot="git://git.gnome.org/network-manager-pptp"
_gitname="network-manager-pptp"

build() {
  msg "Connecting to git.freedesktop.org GIT server...."

  if [ -d ${srcdir}/$_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  cp -r ${srcdir}/$_gitname ${srcdir}/$_gitname-build
  cd ${srcdir}/$_gitname-build

  ./autogen.sh --prefix=/usr --sysconfdir=/etc || return 1

  make -j3 || return 1
  make -j3 DESTDIR=$pkgdir install || return 1

  rm -rf ${srcdir}/$_gitname-build
}
