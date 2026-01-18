pkgname=happ-desktop-bin
pkgver=1.5.2
pkgrel=1
pkgdesc="Happ proxy utility desktop client (prebuilt binary)"
arch=('x86_64')
url="https://github.com/Happ-proxy/happ-desktop"
license=('custom')
depends=('openssl' 'systemd')
provides=('happ')
conflicts=('happ')
source=("${pkgname}-${pkgver}.deb::https://github.com/Happ-proxy/happ-desktop/releases/download/${pkgver}/Happ.linux.x64.deb")
sha256sums=('305bf4439fb79a3e1ff09602d38f577bdd1f929c5ce4838dd89dade6e27da2c7')
options=(!strip)

package() {
  bsdtar -xf "${srcdir}/${pkgname}-${pkgver}.deb" -C "${srcdir}" || return 1
  bsdtar -xf "${srcdir}/data.tar.zst" -C "${pkgdir}" || return 1

  install -d "${pkgdir}/usr/share/licenses/${pkgname}"

  local core_license="${pkgdir}/opt/happ/bin/core/LICENSE"
  local tun_license="${pkgdir}/opt/happ/bin/tun/LICENSE"

  [[ -f "${core_license}" ]] && install -m644 "${core_license}" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.core"
  [[ -f "${tun_license}" ]] && install -m644 "${tun_license}" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.tun"
}
