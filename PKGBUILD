pkgname=17g-live-installer
pkgver=4.1
pkgrel=2
pkgdesc="GUI Installation Tool for GNU/Linux"
arch=('x86_64')
url="https://github.com/killajoe/17g"
license=('GPL3')
depends=('git' 'python-pillow' 'python-pyparted' 'python-cairo' 'python-gobject' 'python-yaml' 'rsync' 'gettext' 'grub')
makedepends=()
source=("https://github.com/killajoe/17g/archive/refs/tags/4.1.tar.gz")
md5sums=('23cf4b79209506c2585852e7518fe705')

prepare() {
    cd "${srcdir}"

    echo "" > ${srcdir}/17g-${pkgver}/live-installer/branding/hosts

    #install -m644 ${srcdir}/config.yaml ${srcdir}/17g-${pkgver}/live-installer/configs/config.yaml
    #install -m644 ${srcdir}/live.yaml ${srcdir}/17g-${pkgver}/live-installer/configs/live.yaml
    #cp -r ${srcdir}/slides ${srcdir}/17g-${pkgver}/live-installer/branding
}

package() {
    cd "${srcdir}"/17g-${pkgver}

    make
    make DESTDIR=${pkgdir} install

    install -d ${pkgdir}/usr/lib/systemd/system/
    install -d ${pkgdir}/etc/xdg/autostart/
    
    install -m644 17g.service ${pkgdir}/usr/lib/systemd/system/17g.service
    install -m775 live-installer.desktop ${pkgdir}/etc/xdg/autostart/live-installer.desktop
}
