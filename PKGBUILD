## $Id$
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>
# Contributor: Bart Ribbers <bribbers@disroot.org>
# Contributor: Alexey Andreyev (aa13q) <aa13q@ya.ru>

pkgname=nemo-qml-plugin-systemsettings-git
pkgver=0.5.46.r0.g92572a1
pkgrel=1
pkgdesc="System settings plugin for Nemo Mobile"
arch=('x86_64' 'aarch64')
url="https://git.sailfishos.org/mer-core/nemo-qml-plugin-systemsettings"
license=('BSD')
depends=('qt5-base' 'qt5-declarative' 'nemo-qml-plugin-dbus' 'qt5-mlocale-git' 'nemo-qml-plugin-models-git' 'libconnman-qt-git' 'qt5-mlite-git' 'sailfish-user-managerd-git')
makedepends=('git')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=('git+https://git.sailfishos.org/mer-core/nemo-qml-plugin-systemsettings.git'
        '0002-Remove-developer-mode.patch'
        '0003-Remove-broken-certificatemodel.patch'
)
md5sums=('SKIP' 'SKIP' 'SKIP')

pkgver() {
    cd "$srcdir/${pkgname%-git}"
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
    cd "$srcdir/${pkgname%-git}"
    patch -p1 --input="${srcdir}/0002-Remove-developer-mode.patch"
    patch -p1 --input="${srcdir}/0003-Remove-broken-certificatemodel.patch"
}

build() {
    cd "$srcdir/${pkgname%-git}"
    qmake
    make
}

package() {
    cd "$srcdir/${pkgname%-git}"
    make INSTALL_ROOT="$pkgdir/" install
    cd "$pkgdir"
    rm -rf opt
}
