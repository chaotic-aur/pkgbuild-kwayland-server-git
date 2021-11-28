# Maintainer: zan <zan@420blaze.it>

pkgname=kwayland-server-git
_name=${pkgname%-git}
pkgver=5.20.80
pkgrel=1
pkgdesc='Wayland Server Components built on KDE Frameworks '
arch=(x86_64)
url='https://invent.kde.org/plasma/kwayland-server'
license=(LGPL)
depends=(qt5-base)
makedepends=(git extra-cmake-modules-git plasma-wayland-protocols-git wayland-protocols kwayland doxygen qt5-tools)
conflicts=(kwayland-server)
provides=(kwayland-server)
groups=(kf5-git)
source=("git+https://invent.kde.org/plasma/$_name.git")
md5sums=('SKIP')

pkgver() {
  cd $_name
  _ver="$(cat CMakeLists.txt | grep -m1 'set(PROJECT_VERSION' | cut -d '"' -f2 | tr - .)"
  echo "${_ver}.r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S $_name
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}



