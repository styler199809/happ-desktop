pkgname=happ-desktop-bin
pkgver=1.5.2
pkgrel=1
pkgdesc="Happ proxy utility desktop client (prebuilt binary)"
arch=('x86_64')
url="https://github.com/Happ-proxy/happ-desktop"
license=('custom')
depends=('openssl' 'glibc' 'systemd')
provides=('happ')
conflicts=('happ')
source=("https://github.com/Happ-proxy/happ-desktop/releases/download/${pkgver}/Happ.linux.x64.deb")
sha256sums=('305bf4439fb79a3e1ff09602d38f577bdd1f929c5ce4838dd89dade6e27da2c7')
options=(!strip)

package() {
  bsdtar -xf "${srcdir}/Happ.linux.x64.deb" -C "${srcdir}"
  bsdtar -xf "${srcdir}/data.tar.zst" -C "${pkgdir}"

  install -d "${pkgdir}/usr/share/licenses/${pkgname}"
  install -m644 "${pkgdir}/opt/happ/bin/core/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.core"
  install -m644 "${pkgdir}/opt/happ/bin/tun/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.tun"
}
