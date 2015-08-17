# Maintainer: Rikles <style.boubou@gmail.com>
# Contributer: Ghost1227 (ghost1227 at archlinux dot us)
# Custom update by: Cyro

pkgname=stendhal
pkgver=1.12
pkgrel=1
pkgdesc="A fully fledged free open source multiplayer online adventure game (MORPG) developed using the Arianne game system."
arch=('any')
url="http://stendhalgame.org/"
license=('GPL')
depends=('java-runtime')
makedepends=('unzip')
source=(${pkgname}.gif "http://sourceforge.net/projects/arianne/files/${pkgname}/${pkgver}/${pkgname}-${pkgver}.zip")
noextract=("${pkgname}-${pkgver}.zip")
md5sums=('451fa6c20bf71279277bb84bfd80090e'
         '9d99d5c441485880bbe07883e057d1b7')

build() {
  unzip "${srcdir}/${pkgname}-${pkgver}.zip" -d "${srcdir}/${pkgname}-${pkgver}"
}

package(){
  cat > "${srcdir}/${pkgname}" <<EOF
#!/bin/bash
"\$JAVA_HOME/bin/java" -jar '/opt/${pkgname}/${pkgname}-starter.jar'
EOF

  cat > "${srcdir}/${pkgname}.desktop" <<EOF
[Desktop Entry]
Type=Application
Version=1.12
Name=Stendhal
Comment=A fully fledged free open source multiplayer online adventure game (MORPG) developed using the Arianne game system.
Exec=${pkgname}
Terminal=false
Categories=Game;Java;
EOF

  mkdir -p "${pkgdir}/opt/${pkgname}"
  cp -r "${srcdir}/${pkgname}-${pkgver}/"* "${pkgdir}/opt/${pkgname}/"
  install -D -m 755 "${srcdir}/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
  install -D -m 644 "${srcdir}/${pkgname}.desktop" "${pkgdir}/usr/share/applications/${pkgname}.desktop"
  install -D -m 644 "${srcdir}/${pkgname}.gif"     "${pkgdir}/usr/share/pixmaps/${pkgname}.gif"
  chmod 755 "${pkgdir}/opt/${pkgname}/${pkgname}-starter.jar"
}
