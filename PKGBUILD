# Maintainer: Happ Proxy Team <support@happ.su>
pkgname=happ-desktop-bin
pkgver=1.5.2
pkgrel=1
pkgdesc="Happ proxy utility desktop client (prebuilt binary)"
arch=('x86_64')
url="https://github.com/Happ-proxy/happ-desktop"
license=('custom')
depends=('openssl')
optdepends=('systemd: manage the bundled happd service')
provides=('happ')
conflicts=('happ')
source=("${pkgname}-${pkgver}.deb::${url}/releases/download/${pkgver}/Happ.linux.x64.deb")
sha256sums=('305bf4439fb79a3e1ff09602d38f577bdd1f929c5ce4838dd89dade6e27da2c7')
# Binaries are prebuilt; avoid stripping to prevent breaking shipped artifacts.
options=(!strip)

package() {
  bsdtar -xf "${srcdir}/${pkgname}-${pkgver}.deb" -C "${srcdir}"

  local data_archive
  data_archive="$(find "${srcdir}" -maxdepth 1 -type f -regextype posix-extended -regex '.*data\.tar\.(gz|xz|zst|bz2|lzma)' -print -quit)"
  if [[ -z "${data_archive}" ]]; then
    error "Data archive missing or uses unsupported compression format in downloaded package."
    return 1
  fi

  if ! bsdtar -xf "${data_archive}" -C "${pkgdir}"; then
    error "Failed to extract data archive: ${data_archive}"
    return 1
  fi

  if ! install -d "${pkgdir}/usr/share/licenses/${pkgname}"; then
    error "Failed to create license directory"
    return 1
  fi

  local core_license="${pkgdir}/opt/happ/bin/core/LICENSE"
  local tun_license="${pkgdir}/opt/happ/bin/tun/LICENSE"

  if [[ -f "${core_license}" ]]; then
    if ! install -m644 "${core_license}" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.core"; then
      error "Failed to install core license file"
      return 1
    fi
  fi

  if [[ -f "${tun_license}" ]]; then
    if ! install -m644 "${tun_license}" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.tun"; then
      error "Failed to install tun license file"
      return 1
    fi
  fi
}
