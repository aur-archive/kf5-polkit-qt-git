# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kf5-polkit-qt-git
pkgver=v0.103.0.3.g4ed9c3f
pkgrel=1
pkgdesc='Qt wrapper around polkit-1 client libraries'
arch=('i686' 'x86_64')
url='http://phonon.kde.org/'
license=('LGPL')
depends=('qtx11extras-git' 'qtsvg-git' 'polkit')
makedepends=('cmake' 'extra-cmake-modules-git' 'git')
provides=('kf5-polkit-qt')
conflicts=('kf5-polkit-qt')
options=('debug')
source=(git://anongit.kde.org/polkit-qt-1.git#branch=qt5)
md5sums=('SKIP')

pkgver() {
  cd polkit-qt-1
  git describe --always | sed 's|-|.|g' 
}

prepare() {
  mkdir -p build
}

build() {
  export LD_LIBRARY_PATH=/opt/qt-git/lib

  cd build
  cmake ../polkit-qt-1 \
    -DCMAKE_PREFIX_PATH=/opt/qt-git/lib/cmake \
    -DCMAKE_BUILD_TYPE=RelWithDebInfo \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DLIB_INSTALL_DIR=lib
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
