# Maintainer: Norbert Preining <norbert@preining.info>
pkgname=plasma5-gamemode
pkgver=0.0.1
pkgrel=1
pkgdesc="Gamemode UI for the Plasma5 Desktop"
provides=("plasma-gamemode")
conflicts=("plasma-gamemode")
arch=('x86_64')
url="https://invent.kde.org/detiam/plasma-gamemode"
license=('MIT' 'BSD-3-Clause' 'GPL-2.0-only' 'GPL-3.0-only' 'LGPL-3.0-only' 'CC0-1.0')
depends=(
  'kirigami2'
  'gcc-libs'
  'gamemode'
  'fontconfig'
  'qt5-base>=5.15.0'
  'kcoreaddons5>=5.82'
  'kdbusaddons5>=5.82'
  'ki18n5>=5.82'
  'kdeclarative5>=5.82'
  'kpackage5>=5.82'
  'kservice5>=5.82'
  'plasma-framework5>=5.82')

makedepends=('git' 'pkgconf' 'cmake>=3.16' 'extra-cmake-modules>=5.82')
source=("git+${url}.git")
sha256sums=('SKIP')

build() {
	cmake -B build -S "$srcdir/plasma-gamemode" \
		-DCMAKE_INSTALL_PREFIX='/usr' \
		-DCMAKE_BUILD_TYPE='None' \
		-Wno-dev 
	cmake --build build
}

check() {
	cd build
	ctest --output-on-failure
}

package() {
	DESTDIR="$pkgdir" cmake --install build
	install -Dm 644 -t "${pkgdir}/usr/share/licenses/${pkgname}" "$srcdir/plasma-gamemode"/LICENSES/*
}
