# Maintainer: Daniel Maslowski <info@orangecms.org>
# Co-Maintainer: Ke Liu <specter119@gmail.com>

pkgname=python-libmamba
pkgver=1.5.8
_srcver=2024.03.25
_name=mamba-$_srcver
pkgrel=1
pkgdesc="The fast cross-platform package manager"
arch=('any')
url="https://github.com/mamba-org/mamba"
license=('BSD')
depends=(
  'cmake>=3.18'
  'python>=3.7'
  'python-scikit-build>=0.13'
  'python-setuptools>=42'
  'python-ninja'
  'python-wheel'
)
makedepends=('python-setuptools')
provides=('python-libmamba')
#options=(!emptydirs)
#backup=(etc/conda/condarc)
source=(
  $_name-$pkgver.tar.gz::$url/archive/refs/tags/$_srcver.tar.gz
)
sha512sums=('93263defae3a5ef0cd4ea16b1a9ac2bcdc63e0091043d6975fb2d4d9b5430eed224a33dcf4336e7967646b80204ce17f1190be31c2ca2b6725d424ee5f5c13bc')

prepare() {
  cd $srcdir/${_name}
}

build() {
  cd $srcdir/${_name}/libmambapy
  python setup.py build
}

package() {
  cd $srcdir/${_name}/libmambapy
  python setup.py install --root=$pkgdir --optimize=1 --skip-build
 
  install -Dm 644 LICENSE $pkgdir/usr/share/licenses/${pkgname}/LICENSE.txt
}
