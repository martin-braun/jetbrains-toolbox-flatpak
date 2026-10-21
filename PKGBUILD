# Maintainer: Martin Braun
# Contributor: JC (radioactivepb)
# Contributors: JetBrains s.r.o.

pkgname=jetbrains-toolbox-flatpak
pkgver=3.9
pkgrel=1

pkgdesc='JetBrains Toolbox for Linux in Flatpak format'
arch=('x86_64')
url='https://github.com/radioactivepb/jetbrains-toolbox-linux'
license=('LicenseRef-proprietary')

depends=(
    flatpak
    util-linux
)

provides=(
    "jetbrains-toolbox=${pkgver}"
)
conflicts=(
    jetbrains-toolbox
)

install=jetbrains-toolbox-flatpak.install

_flatpak="com.jetbrains.Toolbox-${pkgver}.flatpak"

source=(
    "https://github.com/radioactivepb/jetbrains-toolbox-linux/releases/download/v${pkgver}/${_flatpak}"
    jetbrains-toolbox
    com.jetbrains.Toolbox.desktop
)

noextract=(
    "${_flatpak}"
)

sha256sums=('a21d6561db294a5e8b736ed81479ff97b6a62aef4efa7485aed0516c125b1ac6'
            '37cd9a5534ea2c807967f124ce31457dd6f1cc05e4d61e7e3694dd7876017d68'
            '59ccb287ef3c792d35b43ec921f6ea315bf56edc14695b5f794b36feab022a8a')

package() {
    install -Dm644 "${srcdir}/${_flatpak}" \
        "${pkgdir}/usr/share/${pkgname}/com.jetbrains.Toolbox.flatpak"

    install -Dm755 "${srcdir}/jetbrains-toolbox" \
        "${pkgdir}/usr/bin/jetbrains-toolbox"

    install -Dm644 "${srcdir}/com.jetbrains.Toolbox.desktop" \
        "${pkgdir}/usr/share/applications/com.jetbrains.Toolbox.desktop"

    printf '%s\n' "${pkgver}" > \
        "${pkgdir}/usr/share/${pkgname}/version"
}
