pkgname=terraform-provider-gandi
pkgver=1.1.1
pkgrel=1
pkgdesc="Terraform Gandi provider"
url="https://github.com/tiramiseb/terraform-provider-gandi"
arch=("i686" "x86_64")
license=("MPL2")
makedepends=("go" "git")
_gourl="github.com/tiramiseb"
depends=('terraform')
source=("https://github.com/tiramiseb/${pkgname}/archive/v${pkgver}.tar.gz")
sha256sums=('b9bc76980250504820b4c66bc31d461c7bd1fad48acbbeab5aa33bf788c8816f')

prepare() {
    mkdir -p "$srcdir/src/$_gourl"
    rm -rf "${srcdir}/src/$_gourl/$pkgname"
    mv -f "$pkgname-$pkgver" "$srcdir/src/$_gourl/$pkgname"
    msg2 "Fetching dependencies"
    cd "$srcdir/src/$_gourl/$pkgname"
}


build() {
    msg2 "Build program"
    cd "$srcdir/src/$_gourl/$pkgname"
    GOPATH="$srcdir" GOBIN="$srcdir/bin" PATH="$srcdir/bin:$PATH" make
}


package() {
    cd "$srcdir/bin"
    install -Dm755 $pkgname "$pkgdir/usr/bin/$pkgname"
}
