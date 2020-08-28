# Maintainer: NXShock <nxshock@gmail.com>

pkgname=go-shadowsocks2
pkgver=0.1.3
pkgrel=0
pkgdesc="Next-generation Shadowsocks in Go"
arch=('x86_64' 'aarch64')
url="https://github.com/shadowsocks/$pkgname"
license=('APACHE')
makedepends=('git' 'go')
backup=("usr/lib/systemd/system/$pkgname.service")
install="$pkgname.install"
options=("!strip")
source=("https://github.com/shadowsocks/$pkgname/archive/v$pkgver.tar.gz"
	"$pkgname.service"
	"$pkgname.sysusers")
sha256sums=('db915214583a273b01658f62b49638438180cc8e7997e6dfe5919bd4e46047c2'
	'SKIP'
	'SKIP')

build() {
	cd "$srcdir/$pkgname-$pkgver"
	go build -ldflags "-s -w"
}

package() {
	install -Dm755 "$srcdir/$pkgname-$pkgver/$pkgname" "$pkgdir/usr/bin/$pkgname"
	install -Dm644 "$srcdir/$pkgname.service" "$pkgdir/usr/lib/systemd/system/$pkgname.service"
	install -Dm644 "$srcdir/$pkgname.sysusers" "$pkgdir/usr/lib/sysusers.d/$pkgname.conf"
}
