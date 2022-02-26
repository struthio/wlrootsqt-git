pkgname=wlrootsqt
_pkgname=wlrootsqt
pkgver=49.d86600b
pkgrel=1
pkgdesc='A Qt-based wrapper for various wayland protocols.'
arch=('aarch64' 'x86_64')
url="https://gitlab.com/wlrootsqt/wlrootsqt.git"
license=(MIT)
depends=('qt5-base' 'wlroots' 'qt5-wayland')
makedepends=('git' 'meson' 'ninja')
source=("git+https://gitlab.com/wlrootsqt/wlrootsqt.git")
md5sums=('SKIP')

pkgver() {
  cd $_pkgname
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

prepare() {
  arch-meson --buildtype=release "$_pkgname" .build
}

build() {
  ninja -C .build -k 0 -j $(nproc)
}

package() {
  DESTDIR="$pkgdir" ninja -C .build -d explain install
  install -Dm644 "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
