# Maintainer: Matthew "zashi" Hiles matthew.hiles at gmail
pkgname=chirp-daily
pkgver=$(date +%Y%m%d)
pkgrel=1
pkgdesc="Daily build for GUI tool for programming ham radios; this pkgbuild is never out of date"
arch=('any')
url="http://chirp.danplanet.com/"
license=('GPL')
depends=('python2-lxml' 'python2-pyserial' 'desktop-file-utils' 'pygtk')
options=(!emptydirs)
conflicts=(chirp)
provides=(chirp)
install=
#source=("http://trac.chirp.danplanet.com/chirp_daily/daily-$pkgver/$pkgname-$pkgver.tar.gz")
source=()

#yes, I know the below defeats the point
#md5sums=$(md5sum $pkgname-$pkgver.tar.gz | cut -f1 -d' ') 

build() {
  LATEST=$(curl -q http://trac.chirp.danplanet.com/chirp_daily/LATEST/ | egrep -o "20[0-9]{6}" | uniq)
  # cd src
  wget http://trac.chirp.danplanet.com/chirp_daily/daily-$LATEST/$pkgname-$LATEST.tar.gz
  tar zxvf $pkgname-$LATEST.tar.gz
}

package() {
  LATEST=$(curl -q http://trac.chirp.danplanet.com/chirp_daily/LATEST/ | egrep -o "20[0-9]{6}" | uniq)
  cd "$pkgname-$LATEST"
  python2 setup.py install --root="$pkgdir/" --optimize=1
}

# vim:set ts=2 sw=2 et:
