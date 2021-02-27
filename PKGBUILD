# Maintainer: NXShock <nxshock@gmail.com>

pkgname=go-shadowsocks2
pkgver=0.1.4
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
sha256sums=('67442d32fecf4564dd0fb1d444da2c03a268441b240dbe6cba471d0c52bece3b'
	'SKIP'
	'SKIP')

build() {
	cd "$srcdir/$pkgname-$pkgver"
	go build -buildmode=pie -ldflags "-s -w"
}

package() {
	install -Dm755 "$srcdir/$pkgname-$pkgver/$pkgname" "$pkgdir/usr/bin/$pkgname"
	install -Dm644 "$srcdir/$pkgname.service" "$pkgdir/usr/lib/systemd/system/$pkgname.service"
	install -Dm644 "$srcdir/$pkgname.sysusers" "$pkgdir/usr/lib/sysusers.d/$pkgname.conf"
}
