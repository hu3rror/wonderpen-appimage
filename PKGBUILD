# Maintainer: hu3rror <hu3rror@protonmail.com>
# Former Maintainer: ventusliberum <dafeinayius@gmail.com>

pkgname=wonderpen-appimage
_pkgname=wonderpen
pkgver=2.1.4
_pkgver=6308
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
sha256sums=('851578ae2cd218596fac628e4bacec68c0f37f7bbdb09c91ee0324965861ba96'
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
    install -Dm755 "${srcdir}/${_filename}" "$pkgdir/opt/appimages/${_pkgname}.AppImage"
    install -Dm755 "${srcdir}/${_pkgname}.sh" "${pkgdir}/usr/bin/${_pkgname}"
    install -Dm644 "${srcdir}/squashfs-root/${_pkgname}.desktop" "${pkgdir}/usr/share/applications/${_pkgname}.desktop"
    install -Dm644 "${srcdir}/squashfs-root/${_pkgname}.png" "${pkgdir}/usr/share/icons/${_pkgname}.png"
}
