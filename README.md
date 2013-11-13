# Flight Computer Build and Config


Kernel config and environment config for the flight computer.


Packages to install:

 - `crda`
 - `net-tools`
 - `wpasupplicant`


Directories:

 - `kernel`: kernel build config
 - `linux`: important files to move over after the kernel built


What are these config files?

 - `/etc/inittab`: we add one getty for a last-resort serial console

        T1:23:respawn:/sbin/getty -L ttyS1 115200 vt100

 - `/etc/rc.local`: FC-specific stuff to run at boot time

 - `/etc/ethers`: hard-coded Ethernet MAC addresses, to avoid ARP lookups that might cause telemetry to fail; read by `arp --file` in `/etc/rc.local`

 - `/etc/default/crda`: enable using Wi-Fi channels that are legal in the US but not elsewhere

 - `/etc/udev/rules.d/99-flight-computer.rules`: configure hardware as soon as the kernel has the right drivers ready
