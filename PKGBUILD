pkgname=st
provides=('st')
pkgver=9978cd1
pkgrel=1
pkgdesc="Daniel's fork of st. A simple virtual terminal emulator for X."
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft' 'libxext' 'xorg-fonts-misc')
makedepends=('ncurses' 'git')
url="http://st.suckless.org"

source=('git+https://github.com/doza-daniel/st.git')

sha256sums=('SKIP')

pkgver() {
    cd $srcdir/st
    echo $(git rev-parse --short master)
}

prepare() {
    cd $srcdir/st
    # skip terminfo which conflicts with nsurses
    sed -i '/tic /d' Makefile
}

build() {
    cd $srcdir/st
    make
}

package() {
    cd $srcdir/st
    make PREFIX=/usr DESTDIR="$pkgdir" TERMINFO="$pkgdir/usr/share/terminfo" install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/st/LICENSE"
    install -Dm644 README "$pkgdir/usr/share/doc/st/README"
}
