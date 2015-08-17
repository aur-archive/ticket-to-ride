# Maintainer: Capi Etheriel <barraponto AT gmail DOT com>

pkgname=ticket-to-ride
_pkgname=TicketToRide
pkgver=1.6.2_453
pkgrel=1
pkgdesc="Digital version of popular board game Ticket to Ride."
arch=('i686' 'x86_64')
url="http://www.daysofwonder.com/tickettoride/en/"
license=("custom:commercial")
depends=("java-runtime>=6" "libgl")
optdepends=("hicolor-icon-theme")

if [ "${CARCH}" = "x86_64" ]; then
  _gamepkg="${_pkgname}_${pkgver//_/-}_amd64.deb"
  md5sums=("9d2ba7316ee6b60724e9569434ffe097")
else
  _gamepkg="${_pkgname}_${pkgver//_/-}_i386.deb"
  md5sums=("d5c5f8cbcc2c0019310073e5bebbf9e4")
fi

source=("$_gamepkg::hib://$_gamepkg" "ticket-to-ride-egrep.patch")
md5sums+=('70cc22e03334679b1fb4e2c1875bd3f6')
noextract=($_gamepkg)

build() {
  ar p "${_gamepkg}" data.tar.gz | tar zx -C "${srcdir}"
  patch -Np1 -i "${srcdir}/ticket-to-ride-egrep.patch"
}

package() {
  cp -ra $srcdir/opt $pkgdir/opt
  cp -ra $srcdir/usr $pkgdir/usr
}
