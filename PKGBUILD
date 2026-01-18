# Maintainer: Update with your name and email before publishing to AUR
pkgname=happ-desktop
pkgver=2.0.0
pkgrel=1
pkgdesc="Happ - Proxy utility powered by Xray core"
arch=('x86_64')
url="https://github.com/Happ-proxy/happ-desktop"
license=('custom')
depends=('qt6-base' 'qt6-declarative' 'qt6-svg' 'qt6-wayland' 'systemd' 'glib2' 'libcap' 'krb5' 'xz' 'lz4' 'dbus' 'libgcrypt')
provides=('happ')
conflicts=('happ')
options=('!strip')
source=("${pkgname}-${pkgver}.deb::https://github.com/Happ-proxy/happ-desktop/releases/download/${pkgver}/Happ.linux.x64.deb")
sha256sums=('05f4328c711aee061c6e702f5a1ef1c6ef18181774129a59e3b41212682b0d74')

package() {
    cd "${srcdir}"
    
    # Extract the .deb package (preserves original permissions)
    bsdtar -xf "${pkgname}-${pkgver}.deb"
    
    # Extract the data archive (supports different compression formats)
    bsdtar -xf data.tar.* -C "${pkgdir}"
    
    # Note: The symlink from /usr/bin/happ to /opt/happ/bin/Happ is already
    # included in the .deb package, so no additional setup is needed
}
