# initramfs-tools integration for PPPD(8)

This package runs `pppd` inside of initramfs when booting.

This is particularly useful, for example, to unlock the LUKS-encrypted root 
partition on a remote host that is connected to the Internet via DSL using 
an SSH connection via Dropbear.

## How-to

1. Build the Debian package from this repository using `debuild -b -us -uc`.
2. Install it on the system connected via DSL to the internet.
3. Adjust `/etc/ppp-initramfs/config`:

   * Set `PPPD_PEER` to a existing peer configuration from `/etc/ppp/peers`.
   * Set `PPPD_IFACE` to the network interface connected to the DSL modem.
4. Run `initramfs-tools -k all -u`
