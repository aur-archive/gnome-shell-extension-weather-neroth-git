# Maintainer: Christian METZLER <neroth@xeked.com>
pkgname=gnome-shell-extension-weather-neroth-git
pkgver=20130214
pkgrel=1
pkgdesc="A simple GNOME Shell extension for displaying weather informations from several cities"
arch=('any')
url="https://github.com/Neroth/gnome-shell-extension-weather"
license=('GPL3')
depends=('glib2' 'gettext' 'pkg-config')
makedepends=('git' 'gnome-common' 'autoconf' 'automake' 'intltool')
conflicts=('gnome-shell-extension-weather-git')
provides=('gnome-shell-extension-weather-git')
install='gschemas.install'

_gitroot="https://github.com/Neroth/gnome-shell-extension-weather"
_gitname="gnome-shell-extension-weather"
build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"

  cd "$srcdir/$_gitname"
  ./autogen.sh --prefix=/usr
  make
}

package() {
  cd "$srcdir/$_gitname"
  make DESTDIR=${pkgdir} install
}
