# Maintainer: Runnytu < runnytu at gmail dot com >
# OldMaintainer: Alexey Kharlamov <der@2-47.ru>
# Contributor: David Dufberg Tøttrup <david at dufberg dot se>
# Contributor: Jordi De Groof <jordi(dot)degroof(at)gmail(dot)com>
# Contributor: pyther <pyther@pyther.net>
# Contributor: z3ntu <WEI16416@spengergasse.at>

pkgname=packettracer
pkgver=7.3.1
pkgrel=1
pkgdesc="Cisco PacketTracer 7.3.1 installation package"
arch=( 'x86_64' )
depends=('openssl>=1.0' 'dbus' 'icu' 'glib2' 'libxml2' 'libjpeg-turbo' 'nss' 'libxss')
options=('!strip' '!emptydirs')
url="https://www.netacad.com/courses/packet-tracer"
install=${pkgname}.install
license=('custom')

source=('local://PacketTracer_731_amd64.deb'
	'packettracer.sh'
	'packettracer.install')
sha512sums=('3fe369ef8cd1e0429422e58ce42d1b4288143e49cdf06e1c0bb15cb0b75a0d0fe0fcdaccdf244cb466cb700644ea8d792672f5a8caef3d307d5c071a97d5d42d'
	    '3246843441207d66ccffd0717aa85a7bf828842c2c337d1527597bdf57cc2f9966c75c764aa22f9cb6a331e6268dd64af0da7ce4cc89725d418fc54e163230f2'
	    'f062eff669c2b821a95db3cb3750944ea8a601e8608baf1d867c3a62e367e46e7222b8cefc7d7936248f6f670b7a67c23cc2d391ff59d485723401942a2f8e9d')

package() {

	tar xf data.tar.xz -C "${pkgdir}"
	chown -R 0:0 ${pkgdir}
	mv ${pkgdir}/opt/pt/ ${pkgdir}/opt/packettracer/

	mkdir -p "${pkgdir}/usr/bin/"
	ln -s /opt/packettracer/packettracer "${pkgdir}/usr/bin/packettracer"

	ln -s /usr/lib/libdouble-conversion.so "${pkgdir}/opt/packettracer/bin/libdouble-conversion.so.1"

	sed 's/\/opt\/pt/\/opt\/packettracer/' -i "${pkgdir}/opt/packettracer/linguist"
	sed 's/\/opt\/pt/\/opt\/packettracer/' -i "${pkgdir}/opt/packettracer/packettracer"
	sed 's/\/opt\/pt/\/opt\/packettracer/' -i "${pkgdir}/usr/share/applications/cisco-pt7.desktop"
	sed 's/\/opt\/pt/\/opt\/packettracer/' -i "${pkgdir}/usr/share/applications/cisco-ptsa7.desktop"
	sed -e "\$aCategories=Application;Network;" -i "${pkgdir}/usr/share/applications/cisco-pt7.desktop"
	sed -e "\$aCategories=Application;Network;" -i "${pkgdir}/usr/share/applications/cisco-ptsa7.desktop"
	sed -e "\$aNoDisplay=true" -i "${pkgdir}/usr/share/applications/cisco-ptsa7.desktop"

	install -D -m755 "${srcdir}/packettracer.sh" "${pkgdir}/etc/profile.d/packettracer.sh"

	install -D -m644 "${pkgdir}/opt/packettracer/saves/Switch/IE_2000/upgrade_downgrade_license_on_ie2000.pkt" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
	install -D -m644 "${pkgdir}/opt/packettracer/help/default/copyrights.htm" "${pkgdir}/usr/share/licenses/${pkgname}/COPYRIGHT"

}
