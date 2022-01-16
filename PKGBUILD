# Maintainer: Max Fierke <max@maxfierke.com>

pkgname=clockworkpi-a06-fan-daemon
pkgver=20$(date +%y%m%d)
pkgrel=1
pkgdesc="ClockworkPi DevTerm A06 fan daemon"
arch=('any')
url="https://github.com/clockworkpi/DevTerm/tree/main/Code/devterm_fan_daemon_cpi_a06"
license=('LGPL-2.1')
install=${pkgname}.install
depends=('python')
source=(
    'https://github.com/clockworkpi/DevTerm/raw/main/Code/devterm_fan_daemon_cpi_a06/temp_fan_daemon_a06.py'
    'clockworkpi-a06-fan-daemon.service'
)
sha256sums=('c495ca4b212b849b05e1e48d8766bc340da8d1eb36e49d4b3b9411396742149a'
            'da71738ea259854b234331eb595404459963d47e733d900294773c999ff716a9')

package() {
    echo "Installing clockworkpi-a06-fan-daemon files"

    # Replace fan-on temperature w/ 55C, rather than 70C which doesn't seem to be enough to avoid overheating
    sed -i 's/MAX_TEMP=70000/MAX_TEMP=55000/' "${srcdir}/temp_fan_daemon_a06.py"

    install -Dm644 "${srcdir}/temp_fan_daemon_a06.py" "${pkgdir}/usr/share/clockworkpi-a06-fan-daemon/bin/temp_fan_daemon_a06.py"
    install -Dm644 "${srcdir}/clockworkpi-a06-fan-daemon.service" "${pkgdir}/etc/systemd/system/clockworkpi-a06-fan-daemon.service"
}
