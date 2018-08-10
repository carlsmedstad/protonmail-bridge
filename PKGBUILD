# Maintainer: aimileus <me at aimileus dot nl>
pkgname=protonmail-bridge
_pkgver=1.0.5
_pkgrel=1
pkgver="${_pkgver}.${_pkgrel}"
pkgrel=1
pkgdesc="Application to use IMAP/SMTP with your paid ProtonMail account"
arch=('x86_64')
url="https://protonmail.com/bridge/"
license=('custom' 'MIT')
depends=(
  'libsecret'
  'gnome-keyring'
  'qt5-svg'
  'qt5-declarative'
  'qt5-multimedia'
  'ttf-dejavu'
)
options=('!strip')
source=("https://protonmail.com/download/protonmail-bridge_${_pkgver}-${_pkgrel}_amd64.deb")
sha256sums=('d4f5cffda8952cbae4a08ae9d69cdce79101c351411cff1c3823c6c40a254ebb')

prepare() {
	tar xvJf data.tar.xz

	mv usr/share/applications/Desktop-Bridge.desktop \
		usr/share/applications/protonmail-bridge.desktop
	sed -i "s|Icon=/usr/share/icons/protonmail/Desktop-Bridge.svg|Icon=protonmail-bridge|" \
                usr/share/applications/protonmail-bridge.desktop

	# Don't pollute /usr/share/icons
	mv usr/share/icons/protonmail/Desktop-Bridge.svg \
		usr/share/icons/hicolor/scalable/apps/protonmail-bridge.svg
        rmdir usr/share/icons/protonmail
}

package() {
        cp -r usr/ "$pkgdir"
	install -Dm644 "$pkgdir"/usr/lib/protonmail/bridge/{eula.txt,LICENSE} \
		-t "$pkgdir/usr/share/licenses/$pkgname"
}
