# Contributor: Andre Klitzing <andre () incubo () de>
#              Sebastian Jeworutzki <sebastian.jeworutzki () rub () de>

pkgname=pgrouting
pkgver=1.05
pkgrel=1
pkgdesc="Adds routing functionality to PostGIS/PostgreSQL"
arch=('i686' 'x86_64')
url="http://pgrouting.postlbs.org"
license=('GPL')
depends=('postgis' 'gcc-libs')
makedepends=('cmake>=2.3' 'boost>=1.47')
source=(http://download.osgeo.org/pgrouting/source/$pkgname-$pkgver.tar.gz includes.patch)

sha1sums=('582b37eebf86416ca8936e2f3992b5319abc5325'
          'aebc2d216fee86883175b166e4a92c62c3d7ef00')

build() {
  cd $srcdir/$pkgname-$pkgver
  mv cmake/CMakeList.txt cmake/CMakeLists.txt
  patch -p0 -i $srcdir/includes.patch || return 1
  # TSP needs package GAUL and DD needs CGAL
  #cmake . -DWITH_TSP=ON -DWITH_DD=ON
  cmake . || return 1
  make || return 1
  make DESTDIR=$pkgdir install || return 1
}
