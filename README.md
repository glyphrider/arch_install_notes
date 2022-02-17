*Arch Linux*
_installation notes_

# Boot the installation media

I'm hoping there's no trouble here. But depending on BIOS settings you might have to tweak something on your computer before this will work.

# Get on the 'net

If you're wired (with DHCP services on your network) you should be good to go, thanks to some intelligent default behavior with the installation media.

If you're using WiFi, things get a little tricky (but it isn't terrible).

## iwd (iNet Wireless Daemon)

You'll need to use iwd and `iwctl` to configure your wireless adapter. So, launch `iwctl`.

```
root@archiso ~ # iwctl
NetworkConfigurationEnabled: disabled
StateDirectory: /var/lib/iwd
Version: 1.20
[iwd]# device list
```
This will show the available wireless devices. Mine showed up as `wlan0`.
```
[iwd]# station wlan0 scan
[iwd]# station wlan0 get-networks
```
This will show the available WiFi networks. Mine included the network `demo`.
```
[iwd]# station wlan0 connect demo
Type the network passphrase for demo psk
Passphrase:
```
I entered the PSK (pre-shared key) passphrase, and after a moment the application responded with... nothing. That means it worked. If it didn't work, you would have seen `Operation failed`
