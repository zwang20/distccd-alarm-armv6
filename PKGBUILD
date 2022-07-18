pkgbase='distccd-alarm'
pkgname='distccd-alarm-armv6l'
pkgver=10.2.0
pkgrel=1
pkgdesc="An x-tools & distcc services package for Arch Linux ARM"
arch=('x86_64')
license=('GPL')
depends=('distcc')
options=('libtool' 'emptydirs' '!strip')
source=('distccd-armv6h.conf' 'distccd-armv6h.service' 'https://archlinuxarm.org/builder/xtools/10.2.0/x-tools6h.tar.xz')
b2sums=('076560b79622e7c51eb7cb63b466828db6463177d087ab9819f35b5a0d02be0baf40aaeb2362a8523fcf16b9c3c9337649196fefe7e08df2019e3e6fcce4a40b' '1a888890a268f6c34d9efddd130248847864763ba179eeb319047a1302497a4878b89c42b666040f3dd8604b944285fd401358ffc07c648ce24c212a9feeb0b0' '18a7f068fca55e4340b6042feb8aee59e2d1d8f3d39e214401c80dcd18452fd732f6e2cb33e8b1f05533b2b5c58f2a0f459426728f3b22db70cba46556be3ff6')

install -d "${pkgdir}/usr/bin"
ln -sf /usr/bin/distccd "${pkgdir}/usr/bin/distccd-armv6h"
install -d "${pkgdir}/usr/local/x-tools-armv6h"
cp -ar "${srcdir}/x-tools6h" "${pkgdir}/usr/local/x-tools-armv6h"
install -Dm0644 "${srcdir}/distccd-armv6h.service" "${pkgdir}/usr/lib/systemd/system/distccd-armv6h.service"
install -Dm0644 "${srcdir}/distccd-armv6h.conf" "${pkgdir}/etc/conf.d/distccd-armv6h"
