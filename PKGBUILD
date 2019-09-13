# Maintainer: ValHue <vhuelamo at gmail dot com>
#
# Contributor: Christopher Loen <christopherloen at gmail dot com>
# Contributor: MarkZZ <mark dot weiman at markzz dot com>
# Contributer: t3ddy <t3ddy1988 "at" gmail {dot} com>
# Contributor: kriation
#
pkgname="fluxgui"
pkgver=1.2.0
pkgrel=1
pkgdesc="Better lighting for Linux. Open source GUI for xflux"
url="https://justgetflux.com/"
arch=('i686' 'x86_64')
license=('MIT')
depends=('hicolor-icon-theme' 'libindicator-gtk2' 'libappindicator-gtk2'\
         # 'python-libappindicator' 
	 'python-pexpect' 'python-xdg' 'python-gobject'\
         'libappindicator-gtk3'
)
makedepends=('python-pip' 'wget')
conflicts=('xflux' 'xflux-gui-git')
provides=("${pkgname}")
source=("https://github.com/xflux-gui/${pkgname}/archive/v${pkgver}.tar.gz")
sha256sums=('3c230fa7fd5515996849ee775675aad86cb95fdbb824c18425fbdceb076bce63')

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    python ./download-xflux.py
    python setup.py build
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    python setup.py install --prefix=/usr --root="${pkgdir}"/ --optimize=1
    install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    rm "${pkgdir}/usr/share/glib-2.0/schemas/gschemas.compiled"
}

# vim:set ts=4 sw=2 ft=sh et syn=sh ft=sh:
