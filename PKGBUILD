# Maintainer: Christian Hesse <mail@eworm.de>
# Contributor: Antonio Rojas <arojas@archlinux.org>

pkgbase=packagekit-qt
pkgname=('packagekit-qt4' 'packagekit-qt5')
pkgver=0.9.5
pkgrel=3
arch=('i686' 'x86_64')
url='http://www.packagekit.org/'
license=('LGPL')
depends=('packagekit')
validpgpkeys=('163EB50119225DB3DF8F49EA17ACBA8DFA970E17') # Richard Hughes
source=("http://www.freedesktop.org/software/PackageKit/releases/PackageKit-Qt-${pkgver}.tar.xz"{,.asc})
sha256sums=('f4fb60b82d845d887de57ef44481301f966291912116e416d981156faf3620f0'
            'SKIP')

build() {
	mkdir -p "${srcdir}/"{packagekit-qt4,packagekit-qt5}

	cd "${srcdir}/packagekit-qt4/"

  	cmake ../PackageKit-Qt-${pkgver} \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DCMAKE_BUILD_TYPE=Release \
		-DCMAKE_INSTALL_LIBDIR=lib
	make

	cd "${srcdir}/packagekit-qt5/"

  	cmake ../PackageKit-Qt-${pkgver} \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DCMAKE_BUILD_TYPE=Release \
		-DCMAKE_INSTALL_LIBDIR=lib \
		-DUSE_QT5=ON
	make
}

package_packagekit-qt4() {
	pkgdesc='Qt4 bindings for PackageKit'
	depends+=('qt4')

	cd "${srcdir}/packagekit-qt4/"
	make DESTDIR="${pkgdir}" install
}

package_packagekit-qt5() {
	pkgdesc='Qt5 bindings for PackageKit'
	depends+=('qt5-base')

	cd "${srcdir}/packagekit-qt5/"
	make DESTDIR="${pkgdir}" install
}
