# Maintainer: hu3rror <hu3rror@protonmail.com>
# Contributor: ventusliberum <dafeinayius@gmail.com>

pkgname=wonderpen-appimage
_pkgname=wonderpen
pkgver=2.3.5
_pkgver=7074
pkgrel=1
pkgdesc="A professional writing app with a focused mode and markdown support"
arch=("x86_64")
url="https://www.tominlab.com/en/wonderpen"
license=(custom)
provides=('wonderpen')
conflicts=('wonderpen')
options=(!strip)
source=("https://file.tominlab.com/WonderPen/${pkgver%.*}/WonderPen_linux_x86_64_${pkgver}(${_pkgver}).AppImage"
	'wonderpen.sh')
sha256sums=('492c1f8801c232fa0902ebf0df6f82a44050f57880ff679747490c59abf2ee6b'
	'e9d4b90a89dad8de88c49346fff51e3813a7f1503ab3d058b87cf647d0946a10')
noextract=('wonderpen.AppImage')
_filename="WonderPen_linux_x86_64_${pkgver}(${_pkgver}).AppImage"

prepare() {
	cd "${srcdir}"
	chmod +x ${_filename}
	./${_filename} --appimage-extract
	sed -i "s,Exec=AppRun,Exec=/usr/bin/${_pkgname} %F,g" "squashfs-root/${_pkgname}.desktop"
}

package() {
	install -Dm755 "${srcdir}/${_filename}" "${pkgdir}/opt/appimages/${_pkgname}.AppImage"
	install -Dm755 "${srcdir}/${_pkgname}.sh" "${pkgdir}/usr/bin/${_pkgname}"
	install -Dm644 "${srcdir}/squashfs-root/${_pkgname}.desktop" "${pkgdir}/usr/share/applications/${_pkgname}.desktop"
	install -Dm644 "${srcdir}/squashfs-root/${_pkgname}.png" "${pkgdir}/usr/share/icons/${_pkgname}.png"
}
