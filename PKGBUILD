# Maintainer: Gustavo Alvarez <sl1pkn07@gmail.com>

pkgname=konversation-git
pkgver=1.6.master.5004.r8097.8efbd55
pkgrel=1
pkgdesc="A user friendly IRC client for KDE. (GIT Version)"
arch=('x86_64' 'i686')
url="http://konversation.kde.org"
makedepends=('git' 'extra-cmake-modules' 'kdoctools' 'python')
depends=('knotifyconfig' 'kemoticons' 'kparts' 'kidletime' 'qca-qt5' 'hicolor-icon-theme')
optdepends=('python: python scripting support')
conflicts=('konversation')
provides=('konversation')
license=('GPL2' 'FDL')
install=konversation-git.install
source=('git://anongit.kde.org/konversation')
sha1sums=('SKIP')

pkgver() {
  cd konversation
  _ver="$(cat src/version.h | grep "#define KONVI_VERSION" | cut -d '"' -f2 | tr - .).$(cat src/commit.h | grep "#define COMMIT" | cut -d ' ' -f3)"
  echo "$(echo ${_ver}).r$(git rev-list --count HEAD).$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../konversation \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DBUILD_TESTING=OFF
  make
}

package() {
  make -C build DESTDIR="${pkgdir}" install
}
