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
    # Extract the deb package (ar extracts the .deb, then bsdtar extracts data.tar.*)
    cd "${srcdir}"
    bsdtar -xf "${pkgname}-${pkgver}.deb"
    bsdtar -xf data.tar.* -C "${pkgdir}/"
    
    # Fix permissions
    chmod -R g-w "${pkgdir}"
    
    # Install license file if present
    if [[ -f "${pkgdir}/usr/share/doc/happ/copyright" ]]; then
        install -Dm644 "${pkgdir}/usr/share/doc/happ/copyright" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    fi
}
