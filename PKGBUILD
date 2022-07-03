# Maintainer: Vitor Barbosa <vitorqb@gmail.com>
pkgname=pmwrap
pkgver=0.2.3
pkgrel=1
epoch=
pkgdesc="Password Manager Wrapper"
arch=(any)
url="https://github.com/vitorqb/pmwrap"
license=('GPL')
groups=()
depends=()
makedepends=("go")
checkdepends=()
optdepends=("dmenu")
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=("$pkgname-$pkgver.tar.gz::${url}/archive/refs/tags/${pkgver}.tar.gz")
noextract=()
md5sums=('11fbbe8277dc20c26425aea5c9f9d0cc')
validpgpkeys=()

_gopkg="${url#https://}"
_gobuild=build/src/$_gopkg

export CGO_CPPFLAGS="${CPPFLAGS}"
export CGO_CFLAGS="${CFLAGS}"
export CGO_CXXFLAGS="${CXXFLAGS}"
export CGO_LDFLAGS="${LDFLAGS}"
export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"

prepare() {
  mkdir -p "$(dirname $_gobuild)"
  cp -a "$srcdir/$pkgname-$pkgver" $_gobuild
}

build() {
  export GOCACHE="$srcdir/cache"
  export GOPATH="$srcdir/build"
  go install $_gopkg@$pkgver
}

package() {
  install -Dm755 build/bin/pmwrap -t "$pkgdir/usr/bin"
}
