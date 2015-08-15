# Maintainer: enderst <enderst@gmail.com>
# Contributor: troxy <aurpkg.20.troxor at spamgourmet dot com>
pkgname=dirvish
pkgver=1.2.1
pkgrel=9
pkgdesc="A fast,disk based, rotating network backup system."
arch=('i686' 'x86_64')
url="http://www.dirvish.org"
license=('OSL-2.0')
depends=(perl rsync perl-getopt-mixed perl-time-modules perl-time-period)
source=(http://www.dirvish.org/dirvish-$pkgver.tgz)
md5sums=('9035fdff055527882ea180c16c2f1bec')

package() {

  
  cd "$srcdir/$pkgname-$pkgver"
  mkdir -p $pkgdir/usr/bin
  mkdir -p $pkgdir/etc/dirvish
  mkdir -p $pkgdir/usr/share/man/man5
  mkdir -p $pkgdir/usr/share/man/man8

  for f in dirvish dirvish-runall dirvish-expire dirvish-locate
  do
    echo "#!`which perl`" > $f
	echo -e "\$CONFDIR = \"/etc/dirvish\";\n" >> $f
    cat $f.pl >>$f
    cat loadconfig.pl >>$f
    install -m 755 $f $pkgdir/usr/bin/$f || return 1
  done

  for f in dirvish.8 dirvish-runall.8 dirvish-expire.8 dirvish-locate.8 
  do
    install -m 644 $f $pkgdir/usr/share/man/man8/$f || return 1
  done
  install -m 644 dirvish.conf.5 $pkgdir/usr/share/man/man5/dirvish.conf.5 || return 1

}

