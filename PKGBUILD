# Maintainer: William Sandström <w.sandstrom@gmail.com>
_pkgroot=typesense
pkgname="${_pkgroot}-bin"
pkgver=29.0
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
            '3110ab9de7492be4db1ba728fe118905bd8ac3679876eec0011603b5e1b3681c')
sha256sums_x86_64=('043d2a13574454a5543f03b67cc3b448c5e2c06f5d0f444c9c0ce45598ad14a0')
sha256sums_aarch64=('ced8c2c8adb7efcb60f724fd0fa3eba08365313e46c942041fc76e1e2bc24361')

prepare() {
    cd "${srcdir}"
    _apikey=$(head -c 32 /dev/urandom | base64 | tr -dc 'a-zA-Z0-9' | head -c 32)
    sed -i "s/api-key = changeme/api-key = ${_apikey}/" typesense-server.ini
}

package() {
    cd "${srcdir}"
    install -D -m 0755 typesense-server "${pkgdir}/usr/bin/typesense-server"
    install -D -m 0644 typesense.sysusers "${pkgdir}/usr/lib/sysusers.d/typesense.conf"
    install -D -m 0644 typesense.tmpfiles "${pkgdir}/usr/lib/tmpfiles.d/typesense.conf"
    install -D -m 0644 typesense-server.service "${pkgdir}/usr/lib/systemd/system/typesense-server.service"
    install -D -m 0640 typesense-server.ini "${pkgdir}/etc/typesense/typesense-server.ini"
}
