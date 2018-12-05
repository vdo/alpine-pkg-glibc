# Maintainer: Benjamin Baessler <athlon@xunit.de>

pkgname="glibc"
pkgver="2.28"
_pkgrel="0"
pkgrel="1"
pkgdesc="GNU C Library compatibility layer"
arch="aarch64"
url="https://github.com/sgerrand/alpine-pkg-glibc"
license="GPL"
source="http://mirror.archlinuxarm.org/aarch64/core/glibc-2.28-4-aarch64.pkg.tar.xz
nsswitch.conf
ld.so.conf"
subpackages="$pkgname-bin $pkgname-dev $pkgname-i18n"
triggers="$pkgname-bin.trigger=/lib:/usr/lib:/usr/glibc-compat/lib"

package() {
  mkdir -p "$pkgdir/lib" "$pkgdir/lib64" "$pkgdir/usr/glibc-compat/lib/locale" "$pkgdir"/etc
  mkdir "$srcdir"/bin
  cp -a "$srcdir"/usr/* "$pkgdir/usr/glibc-compat/"
  cp -a "$srcdir"/etc "$pkgdir/usr/glibc-compat/"
  cp -a "$srcdir"/bin "$pkgdir/usr/glibc-compat/"
  cp "$srcdir"/nsswitch.conf "$pkgdir"/etc/nsswitch.conf
  cp "$srcdir"/ld.so.conf "$pkgdir"/etc/ld.so.conf
  rm "$pkgdir"/usr/glibc-compat/etc/rpc
  rm -rf "$pkgdir"/usr/glibc-compat/bin
  rm -rf "$pkgdir"/usr/glibc-compat/lib/gconv
  rm -rf "$pkgdir"/usr/glibc-compat/lib/getconf
  rm -rf "$pkgdir"/usr/glibc-compat/lib/audit
  rm -rf "$pkgdir"/usr/glibc-compat/share
  ln -s /usr/glibc-compat/lib/ld-linux-aarch64.so.1 ${pkgdir}/lib/ld-linux-aarch64.so.1
  ln -s /usr/glibc-compat/lib/ld-linux-aarch64.so.1 ${pkgdir}/lib64/ld-linux-aarch64.so.1
  ln -s /usr/glibc-compat/etc/ld.so.cache ${pkgdir}/etc/ld.so.cache
}

bin() {
  depends="$pkgname libgcc"
  mkdir -p "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/bin "$subpkgdir"/usr/glibc-compat
}

i18n() {
  depends="$pkgname-bin"
  arch="noarch"
  mkdir -p "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/share "$subpkgdir"/usr/glibc-compa
}

sha256sums="961b92a242e042bdf089f7f3442d911bcbd22e99068978deb845b02ec40e3181  glibc-2.28-4-aarch64.pkg.tar.xz
3be94785355b4b363d1268f133e198323441eafa6017b2b1fed32ae279d685c7  nsswitch.conf
f8eec838bace59c29a5dc04550f60e3c7ba9f3a9df7b14dae36349ad90152e00  ld.so.conf"

