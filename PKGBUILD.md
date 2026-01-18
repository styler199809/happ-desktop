# PKGBUILD for Arch Linux

This directory contains the PKGBUILD file for building an Arch Linux package of Happ Desktop.

## About

Happ is a proxy utility powered by the Xray core, supporting multiple modern protocols including VLESS (Reality), VMess, Trojan, Shadowsocks, and Socks.

## Building the Package

To build and install the package:

```bash
# Clone this repository
git clone https://github.com/styler199809/happ-desktop.git
cd happ-desktop

# Build the package
makepkg -si
```

The `makepkg` command will:
1. Download the pre-built .deb package from GitHub releases
2. Verify the SHA256 checksum
3. Extract and package the contents for Arch Linux
4. Install the package (with `-i` flag)

## Installation Locations

After installation:
- Main application: `/opt/happ/`
- Executable symlink: `/usr/bin/happ`
- Desktop entry: `/usr/share/applications/Happ.desktop`
- Icon: `/usr/share/icons/hicolor/256x256/apps/happ.png`
- Systemd service: `/etc/systemd/system/happd.service`

## Starting the Application

After installation, you can:
- Launch from the application menu
- Run from terminal: `happ`
- Start the systemd service: `sudo systemctl start happd`

## Publishing to AUR

Before publishing to the Arch User Repository (AUR):

1. Update the maintainer information in the PKGBUILD file:
   ```bash
   # Maintainer: Your Name <your.email@example.com>
   ```

2. Generate the .SRCINFO file:
   ```bash
   makepkg --printsrcinfo > .SRCINFO
   ```

3. Follow the AUR submission guidelines at https://wiki.archlinux.org/title/AUR_submission_guidelines

## Updating the Package

When a new version is released:

1. Update the `pkgver` variable in PKGBUILD
2. Update the `sha256sums` with the new checksum from the release
3. Regenerate .SRCINFO: `makepkg --printsrcinfo > .SRCINFO`
4. Test the build: `makepkg -f`

## Dependencies

The package requires:
- qt6-base
- qt6-declarative
- qt6-svg
- qt6-wayland
- systemd
- glib2
- libcap
- krb5
- xz
- lz4
- dbus
- libgcrypt

## License

This package uses a 'custom' license as it bundles components with different licenses. The Xray core component uses the Mozilla Public License 2.0.

## Links

- Project homepage: https://github.com/Happ-proxy/happ-desktop
- Releases: https://github.com/Happ-proxy/happ-desktop/releases
