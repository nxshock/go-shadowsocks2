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
sha256sums=('b4e9396b121eec140aede426450fb579e67e6ba8b905f91ed022e41233a11456'
	'SKIP'
	'SKIP')

build() {
	cd "$srcdir/$pkgname-$pkgver"
	go build -buildmode=pie -trimpath -ldflags "-s -w"
}

package() {
	install -Dm755 "$srcdir/$pkgname-$pkgver/$pkgname" "$pkgdir/usr/bin/$pkgname"
	install -Dm644 "$srcdir/$pkgname.service" "$pkgdir/usr/lib/systemd/system/$pkgname.service"
	install -Dm644 "$srcdir/$pkgname.sysusers" "$pkgdir/usr/lib/sysusers.d/$pkgname.conf"
}
