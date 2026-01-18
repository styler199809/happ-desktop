# Maintainer: Your Name <your.email@example.com>
pkgname=happ-desktop
pkgver=2.0.0
pkgrel=1
pkgdesc="Happ - Proxy utility powered by Xray core"
arch=('x86_64')
url="https://github.com/Happ-proxy/happ-desktop"
license=('unknown')
depends=('qt6-base' 'qt6-declarative' 'qt6-svg' 'qt6-wayland' 'systemd' 'glib2' 'libcap' 'krb5' 'xz' 'lz4' 'dbus' 'libgcrypt')
provides=('happ')
conflicts=('happ')
options=('!strip')
source=("${pkgname}-${pkgver}.deb::https://github.com/Happ-proxy/happ-desktop/releases/download/${pkgver}/Happ.linux.x64.deb")
sha256sums=('05f4328c711aee061c6e702f5a1ef1c6ef18181774129a59e3b41212682b0d74')

package() {
    # Extract the .deb package
    bsdtar -xf "${srcdir}/${pkgname}-${pkgver}.deb"
    bsdtar -xf data.tar.zst -C "${pkgdir}"
    
    # Create necessary directories if they don't exist
    install -dm755 "${pkgdir}/usr/bin"
    
    # Create symlink to main executable
    ln -s /opt/happ/bin/Happ "${pkgdir}/usr/bin/happ"
    
    # Ensure correct permissions for executables
    chmod +x "${pkgdir}/opt/happ/bin/Happ"
    chmod +x "${pkgdir}/opt/happ/bin/happd"
    chmod +x "${pkgdir}/opt/happ/bin/happ-tcping"
    chmod +x "${pkgdir}/opt/happ/bin/core/xray"
    chmod +x "${pkgdir}/opt/happ/bin/tun/sing-box"
    chmod +x "${pkgdir}/opt/happ/bin/tun2/tun2proxy-bin"
    chmod +x "${pkgdir}/opt/happ/bin/tun2/udpgw-server"
    chmod +x "${pkgdir}/opt/happ/bin/antifilter/antifilter"
}
