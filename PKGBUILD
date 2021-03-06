# $Id$
# Maintainer: Massimiliano Torromeo <massimiliano.torromeo@gmail.com>
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Ralf Schmitt <ralf@systemexit.de>

pkgbase=python-greenlet
pkgname=(python3-greenlet python2-greenlet)
pkgver=0.4.12
pkgrel=1
pkgdesc="Lightweight in-process concurrent programming"
license=("MIT")
arch=('x86_64')
url="http://pypi.python.org/pypi/greenlet"
makedepends=('python3-setuptools' 'python2-setuptools')
source=("https://files.pythonhosted.org/packages/source/g/greenlet/greenlet-${pkgver}.tar.gz")
sha512sums=('f3bf0f82b6e3bc687fc9b89469339cfb05e64518d1e49bc96066e8d47b8559f1c1aa53692cd25d839437a2f1b81df6fd9a4509a1b4063ec4ce1d97b73842e9f6')

prepare() {
    cp -a greenlet-$pkgver{,-py2}
}

build() {
	cd "$srcdir"/greenlet-$pkgver
	python3 setup.py build

    cd "$srcdir"/greenlet-$pkgver-py2
    python2 setup.py build
}

check() {
    cd "$srcdir"/greenlet-$pkgver
    python3 setup.py test

    cd "$srcdir"/greenlet-$pkgver-py2
    python2 setup.py test
}

package_python3-greenlet() {
    depends=('python3')

    cd greenlet-$pkgver
    python3 setup.py install -O1 --root="$pkgdir"
    install -Dm0644 LICENSE.PSF "$pkgdir"/usr/share/licenses/$pkgname/LICENSE.PSF
}

package_python2-greenlet() {
    depends=('python2')

	cd greenlet-$pkgver-py2
	python2 setup.py install -O1 --root="$pkgdir"
	install -Dm0644 LICENSE.PSF "$pkgdir"/usr/share/licenses/$pkgname/LICENSE.PSF
}
