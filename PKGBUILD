# Maintainer: Knut Ahlers <knut at ahlers dot me>
# Contributor: Andrew Steinke <rkcf@rkcf.me>

pkgname=eslint-plugin-vue
pkgver=9.31.0
pkgrel=1
pkgdesc='Official ESLint plugin for Vue.js'
arch=('any')
url='https://github.com/vuejs/eslint-plugin-vue'
license=('MIT')
depends=('eslint')
makedepends=('npm')
source=("http://registry.npmjs.org/$pkgname/-/$pkgname-$pkgver.tgz")
sha256sums=('0a8c6146bd5f5242edbfe61cb9f06f3ea89016f33158aea503654630b7e7ad26')
noextract=($pkgname-$pkgver.tgz)

package() {
	install -dm 755 "$pkgdir/usr/lib"
	npm install -g --prefix "$pkgdir"/usr "$srcdir"/$pkgname-$pkgver.tgz

	# Fix permissions
	find "$pkgdir/usr" -type d -exec chmod 755 '{}' +

	# Remove files that conflict with `eslint`:
	rm -rf "$pkgdir/usr/lib/node_modules/eslint"
	rm -rf "$pkgdir/usr/bin"

	install -dm755 "${pkgdir}/usr/share/licenses/${pkgname}"
	ln -s ../../../lib/node_modules/$pkgname/LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
