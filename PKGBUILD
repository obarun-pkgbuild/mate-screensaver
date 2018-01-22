# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://git.archlinux.org/svntogit/community.git/tree/trunk?h=packages/mate-screensaver
# 						Contributor: Martin Wimpress <code@flexion.org>

pkgname=mate-screensaver
pkgver=1.18.2
pkgrel=2
pkgdesc='Screensaver for MATE'
url="https://mate-desktop.org"
arch=('x86_64')
license=('GPL')
depends=('libmatekbd' 'libnotify' 'libxss' 'mate-desktop' 'mate-menus' 'mate-session-manager')
makedepends=('intltool')
optdepends=('rss-glx: Really slick screensavers')
groups=('mate-extra')
conflicts=('mate-screensaver-gtk3')
replaces=('mate-screensaver-gtk3')
source=("https://pub.mate-desktop.org/releases/${pkgver%.*}/${pkgname}-${pkgver}.tar.xz")
sha256sums=('57f820c1b2898f65fc73b0d8003b372fe558620358a9bc12892501ceb53eea0f')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
    cd ${pkgname}-${pkgver}
    ./configure \
        --prefix=/usr \
        --libexecdir=/usr/lib/${pkgname} \
        --sysconfdir=/etc \
        --with-xscreensaverdir=/usr/share/xscreensaver/config \
        --with-xscreensaverhackdir=/usr/lib/xscreensaver \
        --with-mit-ext \
        --with-libnotify \
        --enable-locking \
        --with-console-kit \
        --without-systemd
    make
}

package() {
    cd ${pkgname}-${pkgver}
    make DESTDIR="${pkgdir}" install
}
