# Proxmox

## Admin

### Update System

```
apt update && apt dist-upgrade
```

### Clean out old kernels
Check:
```
dpkg -l pve-kernel-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get purge
```


Apply:
```
dpkg -l pve-kernel-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

## LXC Containers

## KVM/QEMU Guests

### Windows 10


* FlexVDI Guest Tools
* Redhat Guest Tools
* VMWare Guest Tools


#### SPICE

FlexVDI Guest Tools include latest SPICE guest agent usable with Windows 10.

#### VNC

Install the vmmouse.sys driver from VMWare Guest Tools to improve mouse accuracy when using VNC. Helpful when SPICE is also in use on the same VM.



### Ubuntu

## Support

