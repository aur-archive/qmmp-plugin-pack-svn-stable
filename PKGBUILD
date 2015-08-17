# Maintainer: Andrew Panchenko <panchenkoac at gmail>
pkgname='qmmp-plugin-pack-svn-stable'
_svnname='qmmp-plugin-pack-0.7'
pkgver=3588
pkgrel=1
pkgdesc="Qmmp Plugin Pack - svn version (stable 0.7.x branch)"
arch=('i686' 'x86_64')
url="http://qmmp.ylsoftware.com"
license=('GPL')
depends=("qmmp-svn-stable>=$pkgver")
makedepends=('subversion' 'cmake>=2.8.0' 'yasm')
provides=('qmmp-plugin-pack')
conflicts=('qmmp-plugin-pack')
optdepends=( 'mpg123: for mpg123 plugin' )
source=(${pkgname}::svn+http://qmmp.googlecode.com/svn/branches/${_svnname})
md5sums=('SKIP')

pkgver() {
	cd "$SRCDEST/$pkgname"
	svnversion | tr -d [A-z]
}

build() {
	cd "$srcdir/$pkgname"
	cmake -DCMAKE_INSTALL_PREFIX=/usr -DLIB_DIR=lib -DCMAKE_BUILD_TYPE=RELEASE -DUSE_FFAP:BOOL=TRUE
	make || return 1
}

package() {
	cd "$srcdir/$pkgname"
	make DESTDIR="${pkgdir}" install || return 1
}
