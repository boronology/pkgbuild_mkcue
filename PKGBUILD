# Maintainer: boronology <boronology at gmail.com>
pkgname=mkcue_still
pkgver=1_1
pkgrel=2
pkgdesc="Generate CUE Sheet from CD(Build from original repo)"
arch=('i686' 'x86_64')
url="https://code.google.com/p/abcde/"
license=('GPL')
provides=(mkcue)
conflicts=(mkcue)
source=('https://abcde.googlecode.com/svn/mkcue/source/mkcue_1.orig.tar.gz'
	'https://abcde.googlecode.com/svn/mkcue/binaries/mkcue_1-1_i386.deb')
md5sums=('de082e40baf042e23246d54d28cbcdcc'
         '20656ece15fa8b76cd0c9cf3f15fba53')

build() {
	# prepare man file
	cd ${srcdir}
	tar xvf data.tar.gz

	# make
	cd ${srcdir}/mkcue-1.orig
	./configure --prefix=/usr --mandir=/usr/share/man/man1
	make
}


package() {
	# man page
	mkdir -p ${pkgdir}/usr/share/man/man1
	cp ${srcdir}/usr/share/man/man1/mkcue.1.gz ${pkgdir}/usr/share/man/man1

	# binary
	mkdir -p ${pkgdir}/usr/bin
	cd ${srcdir}/mkcue-1.orig
	make DESTDIR="${pkgdir}" install

	# LICENSEs
	mkdir -p ${pkgdir}/usr/share/licenses/mkcue
	cp ${srcdir}/mkcue-1.orig/COPYING ${pkgdir}/usr/share/licenses/mkcue
	cp ${srcdir}/mkcue-1.orig/AUTHORS ${pkgdir}/usr/share/licenses/mkcue
	
	# Other Document
	mkdir -p ${pkgdir}/usr/share/doc/mkcue
	cp ${srcdir}/mkcue-1.orig/README ${pkgdir}/usr/share/doc/mkcue
}
