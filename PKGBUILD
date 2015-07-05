# Maintainer: Christian Neukirchen <chneukirchen@gmail.com>
# Maintainer of byacc: Jaroslav Lichtblau <dragonlord@aur.archlinux.org>
# Contributor: ecst <elecst 4t gmail d0t com>
# Contributor: Abel Stern <abel.stern AT gmail.com>
# Contributor: Anton Bazhenov <anton.bazhenov at gmail>

pkgname=byacc-noconflict
_pkgname=byacc
pkgver=20141006
pkgrel=1
pkgdesc="Non-conflicting version of byacc not providing bison/yacc"
arch=('i686' 'x86_64')
url="http://invisible-island.net/byacc/"
license=('custom')
depends=('glibc')
source=(ftp://invisible-island.net/$_pkgname/$_pkgname-$pkgver.tgz
        ftp://invisible-island.net/$_pkgname/$_pkgname-$pkgver.tgz.asc)
md5sums=('62d58192f2995f24cef41a7cb8ec9ba3'
         'SKIP')
sha256sums=('391b0ac550e94920a86960c6973ec539784dc84849e7c2bb1645ae6d8178b14d'
            'SKIP')

build() {
  cd ${srcdir}/$_pkgname-$pkgver

  ./configure --prefix=/usr --mandir=/usr/share/man
  make
}

package() {
  cd ${srcdir}/$_pkgname-$pkgver
  make DESTDIR=${pkgdir} install

  # License
  sed -n "/is distributed/,/distributed freely/p" README > COPYING
  install -Dm644 COPYING ${pkgdir}/usr/share/licenses/$pkgname/COPYING

  # Rename
  cd ${pkgdir}/usr/bin
  mv yacc byacc
  cd ${pkgdir}/usr/share/man/man1
  mv yacc.1 byacc.1
}
