# Maintainer: Ary Kleinerman <kleinerman at gmail dot com>
#
pkgname=yubico-authenticator
pkgver=6.1.0
pkgdesc="Yubico Authenticator is a cross-platform application for managing your YubiKey's second factor credentials."
arch=('x86_64')
url="https://developers.yubico.com/yubioath-desktop/"
license=('GPL')
depends=('ccid')
pkgrel=1

source=(
    "https://developers.yubico.com/yubioath-desktop/Releases/yubico-authenticator-${pkgver}-linux.tar.gz"{,.sig}
)

validpgpkeys=(
    '20EE325B86A81BCBD3E56798F04367096FBA95E8'
)

sha256sums=(
    'be686148475d642027d6126ea0984578aa2c22a179a565dc24b81b72ea457417'
    '06340f0f9aea9a6f4f9984124c566dc6f5f65fc4ce2b92e8891664bdd230a5f4'
)

prepare() {
    sed -i 's|\(Exec="\)@EXEC_PATH|\1/opt/yubico-authenticator|' "${srcdir}"/yubico-authenticator-"${pkgver}"-linux/linux_support/com.yubico.authenticator.desktop
    sed -i 's|\(Icon=\)@EXEC_PATH/linux_support/|\1|' "${srcdir}"/yubico-authenticator-"${pkgver}"-linux/linux_support/com.yubico.authenticator.desktop
}

package() {
    mkdir -p "$pkgdir/opt/yubico-authenticator"
    ls -1 "${srcdir}"/yubico-authenticator-"${pkgver}"-linux | grep -v "linux_support\|desktop_integration.sh\|README.adoc" | xargs -I{} cp -r "${srcdir}"/yubico-authenticator-"${pkgver}"-linux/{} "$pkgdir/opt/yubico-authenticator"
    install -Dm644 "${srcdir}"/yubico-authenticator-"${pkgver}"-linux/linux_support/com.yubico.authenticator.desktop "${pkgdir}"/usr/share/applications/com.yubico.authenticator.desktop
    install -Dm644 "${srcdir}"/yubico-authenticator-"${pkgver}"-linux/linux_support/com.yubico.yubioath.png "${pkgdir}"/usr/share/pixmaps/com.yubico.yubioath.png
}
