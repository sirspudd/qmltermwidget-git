# Maintainer: Doug Newgard <scimmia at archlinux dot info>

_piver=""

_qmake="qmake"
if [[ -z $_piver ]] && [[ -n $LOCAL_PI_VER ]]; then
  _piver=$LOCAL_PI_VER
fi

if [[ -n "$_piver" ]]; then
  _qmake="/opt/qt-sdk-raspberry-pi${_piver}/bin/qmake"
fi

_pkgname=qmltermwidget
pkgname=$_pkgname-git
pkgrel=2
pkgver=0.1.0.r23.g051e019
pkgdesc='QML port of qtermwidget - development version'
arch=('any')
url='https://github.com/Swordfish90/qmltermwidget'
license=('GPL')
depends=('qt-sdk-raspberry-pi-target-libs')
makedepends=('git' 'qt-sdk-raspberry-pi${_piver}')
provides=("$_pkgname=$pkgver")
conflicts=("$_pkgname" 'cool-retro-term-git<1.0.0RC1.r39')
source=("git://github.com/Swordfish90/qmltermwidget.git")
sha256sums=('SKIP')

pkgver () {
  cd "$srcdir/$_pkgname"

  git describe --tags --long | sed -r 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd "$srcdir/$_pkgname"

  $_qmake
  make
}

package() {
  local temp_pkgdir="$srcdir/refactor_package"
  cd "$srcdir/$_pkgname"
  make INSTALL_ROOT="$pkgdir" install
}
