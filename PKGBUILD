# Maintainer: Happ-proxy <support@happ.su>
# Contributor: styler199809

pkgname=happ-desktop-bin
pkgver=1.5.2
pkgrel=1
pkgdesc="Happ - Proxy utility for convenient proxy server management, powered by Xray core"
arch=('x86_64')
url="https://github.com/Happ-proxy/happ-desktop"
license=('custom')
depends=('gtk3' 'libnotify' 'nss' 'libxss' 'libxtst' 'xdg-utils' 'at-spi2-atk' 'libdrm' 'mesa' 'alsa-lib')
provides=('happ-desktop')
conflicts=('happ-desktop')
options=('!strip' '!emptydirs')
source=("${pkgname}-${pkgver}.deb::https://github.com/Happ-proxy/happ-desktop/releases/download/${pkgver}/Happ.linux.x64.deb")
sha256sums=('305bf4439fb79a3e1ff09602d38f577bdd1f929c5ce4838dd89dade6e27da2c7')

package() {
    # Extract the deb package contents
    cd "${srcdir}"
    bsdtar -xf "${pkgname}-${pkgver}.deb"
    
    # Find and extract the data tarball (handles data.tar.gz, data.tar.xz, data.tar.zst, etc.)
    local data_tar
    data_tar=$(ls data.tar.* 2>/dev/null | head -n1)
    if [[ -z "${data_tar}" ]]; then
        error "Could not find data.tar.* in the .deb package"
        return 1
    fi
    bsdtar -xf "${data_tar}" -C "${pkgdir}/"
    
    # Fix permissions
    chmod -R g-w "${pkgdir}"
    
    # Install license file if present
    if [[ -f "${pkgdir}/usr/share/doc/happ/copyright" ]]; then
        install -Dm644 "${pkgdir}/usr/share/doc/happ/copyright" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    fi
}
