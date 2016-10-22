# Maintainer: Sven Karsten Greiner <sven@sammyshp.de>
pkgname=xss-lock-extended-git
pkgver=v0.3.0.r5.23439f7
pkgrel=1
pkgdesc="Use external locker as X screen saver"
arch=('i686' 'x86_64')
url="https://github.com/SammysHP/xss-lock-extended"
license=('MIT')
depends=('xcb-util' 'systemd')
makedepends=('cmake' 'python-docutils' 'git')
optdepends=('bash-completion: for bash completion')
provides=('xss-lock')
conflicts=('xss-lock')
source=("$pkgname::git+https://github.com/SammysHP/${pkgname%-git}.git")
md5sums=('SKIP')

pkgver() {
    cd "$pkgname"
    printf "%s" "$(git describe --long | sed 's/\([^-]*-\)g/r\1/;s/-/./g')"
}

build() {
    cd "$pkgname"
    cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=Release
    make
}

package() {
    cd "$pkgname"
    make DESTDIR="$pkgdir" install
    install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/"$pkgname"/LICENSE
}
