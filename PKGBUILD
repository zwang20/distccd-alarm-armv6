pkgbase='distccd-alarm'
pkgname='distccd-alarm-armv6'
pkgver=8.1.0
pkgrel=1
pkgdesc="An x-tools & distcc services package for Arch Linux ARM"
arch=('x86_64')
license=('GPL')
depends=('distcc')
options=('libtool' 'emptydirs' '!strip')
source=('distccd-armv6h.conf' 'distccd-armv6h.service' 'https://archlinuxarm.org/builder/xtools/8.1.0-1/x-tools6h.tar.xz')
b2sums=('076560b79622e7c51eb7cb63b466828db6463177d087ab9819f35b5a0d02be0baf40aaeb2362a8523fcf16b9c3c9337649196fefe7e08df2019e3e6fcce4a40b' '1a888890a268f6c34d9efddd130248847864763ba179eeb319047a1302497a4878b89c42b666040f3dd8604b944285fd401358ffc07c648ce24c212a9feeb0b0' '284e0e74c04c3ac991e3a6a9f9c2003fb12988681f98d232d6198f12936ece13916093548481bd3814c75842e3cb1944094ceb7174bd67f7e6e4cbbdbab23ba9')

_package_subarch() {
    # backup configs
    backup=("etc/conf.d/distccd-$1")
    # install symlink to distccd
    install -d "${pkgdir}/usr/bin"
    ln -sf /usr/bin/distccd "${pkgdir}/usr/bin/distccd-$1"
    # copy in toolchain
    install -d "${pkgdir}/usr/local/x-tools-$1"
    cp -ar "${srcdir}/$2" "${pkgdir}/usr/local/x-tools-$1"
    # install services
    install -Dm0644 "${srcdir}/distccd-$1.service" \
       "${pkgdir}/usr/lib/systemd/system/distccd-$1.service"
    # install config
    install -Dm0644 "${srcdir}/distccd-$1.conf" \
       "${pkgdir}/etc/conf.d/distccd-$1"
    
}
package() {
for i in "${!_subarchs[@]}"; do   
    _xtoolsdir="${source[i]##*/}"
    _xtoolsdir="${_xtoolsdir%%.*}"
    eval 'package_distccd-alarm-'${_subarchs[i]}'() {
        _package_subarch '${_subarchs[i]}' '${_xtoolsdir}'
    }'
done
}
