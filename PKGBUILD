pkgname=terraform-provider-gandi
pkgver=1.0.1
pkgrel=1
pkgdesc="Terraform Gandi provider"
url="https://github.com/tiramiseb/terraform-provider-gandi"
arch=("i686" "x86_64")
license=("MPL2")
makedepends=("go" "git")
_gourl="github.com/tiramiseb"
depends=('terraform')
source=("https://github.com/tiramiseb/${pkgname}/archive/v${pkgver}.tar.gz")
sha256sums=('6b4f15ac0ef2a67d648c8a760ef763626f1915cd24bc78dd7cc85c7b0b3fd45c')

prepare() {
    mkdir -p "$srcdir/src/$_gourl"
    rm -rf "${srcdir}/src/$_gourl/$pkgname"
    mv -f "$pkgname-$pkgver" "$srcdir/src/$_gourl/$pkgname"
    cp ../go.mod ../go.sum "$srcdir/src/$_gourl/$pkgname/"
    msg2 "Fetching dependencies"
    cd "$srcdir/src/$_gourl/$pkgname"
    GOPATH="$srcdir" GOBIN="$srcdir/bin" go get
}


build() {
    msg2 "Build program"
    cd "$srcdir/src/$_gourl/$pkgname"
    GOPATH="$srcdir" GOBIN="$srcdir/bin" PATH="$srcdir/bin:$PATH" go build
}


package() {
    cd "$srcdir/bin"
    install -Dm755 $pkgname "$pkgdir/usr/bin/$pkgname"
}

