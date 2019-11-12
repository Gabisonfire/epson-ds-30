# Maintainer: Muflone http://www.muflone.com/contacts/english/
# Contributor: 0strodamus <0strodamus at cox dot net>
# Contributor: ItsTheSource <itsthesource at gmail dot com>

pkgname=iscan-plugin-ds-30
pkgver=1.0.1
pkgrel=2
pkgdesc="EPSON Image Scan! plugin for Epson scanners (WorkForce DS-30)"
arch=('x86_64')
url="http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX"
license=('custom:AVASYSPL')
depends=('iscan' 'iscan-data')
_plugin=${pkgname/iscan-plugin-/}
_iscan_ver=2.30.4
_plugin_rel=1
_file_ver=1.0.1
source_x86_64=("iscan-ds-30-bundle-2.30.4.x64.deb.tar.gz")
sha256sums_x86_64=('818536ea9631ceaf86acacf04c515bdddffdd3533ad228b78f8b707f60378646')
install="${pkgname}.install"

_filearch=x64
_debarch=amd64

build() {
  cd "iscan-${_plugin}-bundle-${_iscan_ver}.${_filearch}.deb/plugins"
  bsdtar -xf "${pkgname}_${_file_ver}-${_plugin_rel}_${_debarch}.deb"
  bsdtar -xf data.tar.gz
  gzip -fkd "usr/share/doc/${pkgname}/NEWS.gz"
}

package() {
  cd "iscan-${_plugin}-bundle-${_iscan_ver}.${_filearch}.deb/plugins/usr"
  # Install plugins
  install -m 755 -d "${pkgdir}/usr/lib/iscan"
  install -m 644 -t "${pkgdir}/usr/lib/iscan" "lib/iscan/lib${pkgname}.so.0.0.0"
  ln -s "lib${pkgname}.so.0.0.0" "${pkgdir}/usr/lib/iscan/lib${pkgname}.so"
  ln -s "lib${pkgname}.so.0.0.0" "${pkgdir}/usr/lib/iscan/lib${pkgname}.so.0"
  # Install documentation
  install -m 755 -d "${pkgdir}/usr/share/doc/${pkgname}"
  install -m 644 -t "${pkgdir}/usr/share/doc/${pkgname}" "share/doc/${pkgname}/NEWS"
  # Install licenses
  install -m 755 -d "${pkgdir}/usr/share/licenses/${pkgname}"
}
