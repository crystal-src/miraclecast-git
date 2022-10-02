# Maintainer: Alberto Fanjul <albertofanjul@gmail.com>

pkgname=miraclecast-git
pkgver=301.a1590ec
pkgrel=1
pkgdesc="MiracleCast provides software to connect external monitors to your system via Wifi. It is compatible to Miracast. Link-management works, everything else is still being worked on. Replaces openwfd. Contribute on https://github.com/albfan/aur-miraclecast"
arch=('i686' 'x86_64' 'armv6h' 'armv7h')
url="https://github.com/albfan/miraclecast"
license=('GPL')
depends=(git "systemd>=221" "python3" "glib2")
provides=("miraclecast")
conflicts=("miraclecast")
backup=(etc/dbus-1/system.d/org.freedesktop.miracle.conf)
source=("${pkgname%-git}::git+$url")
md5sums=('SKIP')

build() {
  cd "$srcdir"/"${pkgname%-git}"
  ./autogen.sh
  ./configure --prefix=/usr --sysconfdir=/etc
  make
}

check() {
  cd "$srcdir"/"${pkgname%-git}"
  make -k check
}

package() {
  cd "$srcdir"/"${pkgname%-git}"
  make DESTDIR="$pkgdir/" install
}

pkgver() {
  cd "${srcdir}"/"${pkgname%-git}"
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}
