# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# The following guidelines are specific to BZR, GIT, HG and SVN packages.
# Other VCS sources are not natively supported by makepkg yet.

# Maintainer: Michal Knapik
_pkgname=interception-compose
pkgname=${_pkgname}-git # '-bzr', '-git', '-hg' or '-svn'
pkgver=r2.4fa1e8e
pkgrel=1
pkgdesc="Map tab or backslash to Menu/Compose key"
arch=('x86_64')
url="https://github.com/mknapik/interception-compose"
license=('MIT')
groups=()
depends=()
makedepends=('git' 'cmake' 'gcc') # 'bzr', 'git', 'mercurial' or 'subversion'	
provides=("${_pkgname}")
conflicts=("${_pkgnam}")
replaces=()
backup=()
options=()
install=
source=("$_pkgname::git+https://github.com/mknapik/interception-compose.git#branch=master")
noextract=()
md5sums=('SKIP')

# Please refer to the 'USING VCS SOURCES' section of the PKGBUILD man page for
# a description of each element in the source array.

pkgver() {
	cd "$srcdir/${_pkgname}"
# VERSION='VER_NUM.rREV_NUM.HASH', or a relevant subset in case VER_NUM or HASH
# Git, no tags available
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
	cd "$srcdir/${_pkgname}"
    mkdir -p ${pkgdir}/usr/local/bin
    cmake -Bbuild -H.
    make -C build
    cp build/compose ${pkgdir}/usr/local/bin/interception-compose
    cp build/caps2leftctrl+esc ${pkgdir}/usr/local/bin/interception-caps2leftctrl+esc
}
