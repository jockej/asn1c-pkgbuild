# Maintainer: Joakim Jalap joakim.jalap@fastmail.com
pkgname=asn1c-git
pkgver=0.1
pkgrel=1
pkgdesc="Git version of the asn1c ASN.1 compiler."
arch=('i686' 'x86_64')
url="http://lionet.info/asn1c/blog/"
license=('BSD')
groups=()
depends=('perl')
makedepends=('git')
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
source=()
noextract=()
md5sums=()

_gitroot=https://github.com/vlm/asn1c
_gitname=asn1c

build() {

  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  autoreconf -iv
  ./configure --prefix=/usr
  make
}

# check() {
#   cd "$srcdir/$_gitname-build"
#   make check
# }

package() {
  cd "$srcdir/$_gitname-build"
  make DESTDIR="$pkgdir/" install
}

# vim:set ts=2 sw=2 et:
