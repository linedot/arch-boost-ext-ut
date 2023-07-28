# Maintainer: Stepan Nassyr <s.nassyr [at] xcpp [dot] org>
pkgname=boost-ext-ut
pkgver=1.1.9
pkgrel=1

pkgdesc="UT: C++20 μ(micro)/Unit Testing Framework "
arch=('any')
url="https://boost-ext.github.io/ut/"
license=('custom')
depends=()
makedepends=('git' 'cmake' 'gcc')
source=("$pkgname-$pkgver.tar.gz::https://github.com/boost-ext/ut/archive/v$pkgver.tar.gz")
sha512sums=('81a6b80948d3a203534244f62f5f3ac57593083cc0c32484498a7d01d29455f7dcb33e2ec0587609b8dff33a81a5551796d7681d48fd93e817d6d0c31697234e')
_utsrc="ut-${pkgver}"

build() {
    cmake -B build -S "$_utsrc" -Wno-dev \
          -DCMAKE_BUILD_TYPE=None \
          -DCMAKE_INSTALL_PREFIX=/usr \
          -DCMAKE_INSTALL_LIBDIR=lib \
          -DBOOST_UT_BUILD_BENCHMARKS=OFF \
          -DBOOST_UT_ENABLE_RUN_AFTER_BUILD=OFF \
          -DBOOST_UT_BUILD_EXAMPLES=OFF \
          -DCMAKE_PREFIX_PATH="${srcdir}"
    cmake --build build
}

check() {
    ctest --test-dir build
}


package() {
    DESTDIR="$pkgdir" cmake --install build

    install -Dm644 -t "$pkgdir/usr/share/licenses/$pkgname" "$_utsrc/LICENSE.md"
}
