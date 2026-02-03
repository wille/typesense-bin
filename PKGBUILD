# Maintainer: William Sandström <w.sandstrom@gmail.com>
_pkgroot=typesense
pkgname="${_pkgroot}-bin"
pkgver=30.1
pkgrel=1
pkgdesc="A fast, typo-tolerant search engine for building delightful search experiences."
arch=('x86_64' 'aarch64')
url="https://github.com/typesense/typesense"
license=('GPL3')
provides=("${_pkgroot}")
backup=('etc/typesense/typesense-server.ini')
source=('typesense.sysusers' 'typesense.tmpfiles' 'typesense-server.service' 'typesense-server.ini')
source_x86_64=("https://dl.typesense.org/releases/${pkgver}/${_pkgroot}-server-${pkgver}-linux-amd64.tar.gz")
source_aarch64=("https://dl.typesense.org/releases/${pkgver}/${_pkgroot}-server-${pkgver}-linux-arm64.tar.gz")
sha256sums=('ef4b613a67e00db11e419fbbbab704c878fd9cc91ac9b55bb47d13ffe4326c31'
            'be5d6252e0239e98f30273ae272aa101385b4fe51d00abdd3534eb3d50658528'
            'efd39e4aaa4acd14c0eece9b4090781939972d4ee5303e86162752d96706aac0'
            '55596bc915fd5e89712a53f6ceb66b486570b972014f09f18bb5fa72e27b5410')
sha256sums_x86_64=('4a1c9ce33efa70b26e24a043bd48792856212845ee0061ea6b9f8a2b7ad76c89')
sha256sums_aarch64=('39212289689b763ae219f322cb87d977b751662f5856b68543bccdaa448200ae')

package() {
    cd "${srcdir}"
    install -D -m 0755 typesense-server "${pkgdir}/usr/bin/typesense-server"
    install -D -m 0644 typesense.sysusers "${pkgdir}/usr/lib/sysusers.d/typesense.conf"
    install -D -m 0644 typesense.tmpfiles "${pkgdir}/usr/lib/tmpfiles.d/typesense.conf"
    install -D -m 0644 typesense-server.service "${pkgdir}/usr/lib/systemd/system/typesense-server.service"
    install -D -m 0640 typesense-server.ini "${pkgdir}/etc/typesense/typesense-server.ini"
}
