pkgname=dummy-sudo
pkgver=999.0
pkgrel=1
pkgdesc="Dummy package to satisfy sudo dependency for base-devel"
arch=('any')
provides=('sudo')
conflicts=('sudo')
depends=('doas')

package() {
  # Create the package directory structure
  install -dm755 "${pkgdir}/usr/bin"
  
  # Create a symbolic link from /usr/bin/sudo to /usr/bin/doas
  ln -s $(which doas) "${pkgdir}/usr/bin/sudo"
}
