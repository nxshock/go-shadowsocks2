# Maintainer: NXShock <nxshock@gmail.com>

pkgname=go-shadowsocks2
pkgver=0.1.0
pkgrel=0
pkgdesc="Next-generation Shadowsocks in Go"
arch=('x86_64' 'aarch64')
url="https://github.com/shadowsocks/$pkgname"
license=('APACHE')
makedepends=('git' 'go')
backup=("usr/lib/systemd/system/$pkgname.service")
options=("!strip")
source=("https://github.com/shadowsocks/$pkgname/archive/v$pkgver.tar.gz"
	"$pkgname.service")
sha256sums=('ad291d0349c07b60edc45d460e2e75dee55a03591534a266e5de8a7f25bc27bc'
	'33fb4a1a20980b1294e469bb368d45efa7287c40ac011eb528b18f807676a900')

build() {
	cd "$srcdir/$pkgname-$pkgver"
	go build -ldflags "-s -w"
}

package() {
	install -Dm755 "$srcdir/$pkgname-$pkgver/$pkgname" "$pkgdir/usr/bin/$pkgname"
	install -Dm644 "$srcdir/$pkgname.service" "$pkgdir/usr/lib/systemd/system/$pkgname.service"
}
