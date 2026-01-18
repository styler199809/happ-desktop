pkgname=happ-desktop
pkgver=1.5.2
pkgrel=1
pkgdesc="Happ desktop proxy utility"
arch=('x86_64')
url="https://github.com/Happ-proxy/happ-desktop"
license=('custom')
source=("Happ.linux.x64.deb::https://github.com/Happ-proxy/happ-desktop/releases/latest/download/Happ.linux.x64.deb")
sha256sums=('SKIP')

package() {
  bsdtar -xf "${srcdir}/Happ.linux.x64.deb" -C "${srcdir}"
  bsdtar -xf "${srcdir}/data.tar."* -C "${pkgdir}"
}
