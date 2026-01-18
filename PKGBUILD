# Maintainer: Your Name <your.email@example.com>
pkgname=happ-desktop
pkgver=1.5.2
pkgrel=1
pkgdesc="Happ - Proxy Utility powered by Xray core with support for modern protocols"
arch=('x86_64')
url="https://github.com/Happ-proxy/happ-desktop"
license=('unknown')
depends=('glibc')
optdepends=(
    'libnotify: for desktop notifications'
    'libappindicator-gtk3: for system tray icon support'
)
source=("${pkgname}-${pkgver}.deb::https://github.com/Happ-proxy/happ-desktop/releases/download/v${pkgver}/Happ.linux.x64.deb")
sha256sums=('SKIP')
noextract=("${pkgname}-${pkgver}.deb")

package() {
    cd "${srcdir}"
    
    # Extract the .deb package
    bsdtar -xf "${pkgname}-${pkgver}.deb"
    bsdtar -xf data.tar.xz -C "${pkgdir}"
    
    # Fix permissions
    find "${pkgdir}" -type d -exec chmod 755 {} \;
    find "${pkgdir}" -type f -exec chmod 644 {} \;
    
    # Make binaries executable
    if [ -d "${pkgdir}/usr/bin" ]; then
        find "${pkgdir}/usr/bin" -type f -exec chmod 755 {} \;
    fi
    
    if [ -d "${pkgdir}/opt" ]; then
        find "${pkgdir}/opt" -type f -name "happ*" -exec chmod 755 {} \;
        find "${pkgdir}/opt" -type f -name "*.so*" -exec chmod 755 {} \;
    fi
}
