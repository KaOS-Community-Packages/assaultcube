pkgname=assaultcube
pkgver=1.2.0.2
pkgrel=1
pkgdesc='A realistic team oriented multiplayer FPS based on the Cube engine'
arch=('x86_64')
url='http://assault.cubers.net/'
license=('ZLIB' 'custom')
depends=('sdl' 'sdl_mixer' 'sdl_image' 'openal' 'zlib' 'gcc-libs' 'libgl' 'desktop-file-utils' 'glu' 'curl')
makedepends=('mesa' 'clang')
source=("http://downloads.sourceforge.net/actiongame/AssaultCube_v${pkgver}.tar.bz2"
        "http://downloads.sourceforge.net/actiongame/AssaultCube_v${pkgver}.source.tar.bz2"
        'assaultcube'
        'assaultcube-server'
        'assaultcube.desktop'
        'assaultcube.png')
md5sums=('a052fc79dca4ecae0f15d9a953f1e2ad'
         '7ec6c6a5f8fc0c2e3bec886c08f3b8c8'
         'd658ad3ee476bfe92afa5b5a04a7b4f5'
         '553e2c3b38c4d13e5d77c23efd51a6a6'
         'a37dfbe8263f4ef8fe41120196194eae'
         'f688c59ecee2ebc5c589720aa1480765')
install=assaultcube.install

build() {
  cd AssaultCube_v${pkgver}.source/source/src

  make
}

package() {
  cd AssaultCube_v${pkgver}.source/source/src
  install -Dm755 ac_client ${pkgdir}/usr/bin/ac_client
  install -Dm755 ac_server ${pkgdir}/usr/bin/ac_server

  cd ${srcdir}/AssaultCube_v${pkgver}
  mkdir -p ${pkgdir}/usr/share/assaultcube
  cp -rf config packages docs mods ${pkgdir}/usr/share/assaultcube
  install -Dm644 ${srcdir}/assaultcube.png ${pkgdir}/usr/share/pixmaps/assaultcube.png
  install -Dm644 ${srcdir}/assaultcube.desktop ${pkgdir}/usr/share/applications/assaultcube.desktop
  install -Dm644 docs/package_copyrights.txt ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
  install -Dm755 ${srcdir}/assaultcube ${pkgdir}/usr/bin/assaultcube
  install -Dm755 ${srcdir}/assaultcube-server ${pkgdir}/usr/bin/assaultcube-server
}

# vim: sw=2:ts=2 et: