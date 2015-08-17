# $Id: PKGBUILD,v 1.12 2003/11/06 08:26:13 dorphell Exp $
# Maintainer: Marty_Stoopid <>
# Contributor: Marty_Stoopid <>
pkgname=pysshfs
pkgver=0.2
pkgrel=7
pkgdesc="GUI for sshfs"
arch=('i686' 'x86_64')
url="https://github.com/dprevite/pysshfs"
license=('GPL')
#groups=
#provides=
depends=('python2-pexpect' 'pygtk' 'gtk2' 'sshfs')
makedepends=()
#conflicts=()
#replaces=()
install=pysshfs.install
source=(pysshfs
		  pysshfs.py
		  pysshfs.patch
		  pysshfs.desktop
		  pysshfs.png
		  example.profil)
md5sums=('d6bda8b31a228aabe0e7c4acdc8d6a03'
			'3a0441243ec3004f1d70d66d1bca9d5a'
			'1cc158daa8ad7e94b911d677604eeb30'
			'ca1337ef3775fa50989699c4a009d362'
			'65237c06c7ce8892824b67b914f4df35'
			'7f4ab614190f7faaa5dce7e0f8f6f851')
package() {
# Select language
sed -i 's/"fuse.sshfs" and "user=%s"/"fuse.sshfs" or "user=%s"/g' pysshfs.py
ENV_LANG=`env | grep LANG= | cut -d = -f 2`
	if [[ $ENV_LANG == 'fr_FR.UTF-8' ]]
		then patch < ../pysshfs.patch
	fi

# Install the executables
  install -Dm644 pysshfs.py "${pkgdir}/usr/bin/pysshfs.py"
  install -Dm644 pysshfs "${pkgdir}/usr/bin/pysshfs"  
  chmod +x ${pkgdir}/usr/bin/pysshfs.py
  chmod +x ${pkgdir}/usr/bin/pysshfs

# Install the .desktop file
  install -Dm644 pysshfs.desktop "${pkgdir}/usr/share/applications/pysshfs.desktop"

# Install the icon
  install -Dm644 pysshfs.png "${pkgdir}/usr/share/pixmaps/pysshfs.png"

# Install the example.profil
  install -Dm644 example.profil "${pkgdir}/usr/share/pysshfs/example.profil"

# Change the ownership to root
  chown -R root:root ${pkgdir}/*
}