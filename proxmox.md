# Proxmox

## Admin

### Update System

```
apt update && apt dist-upgrade
```

### Clean out old kernels (may not work with Proxmox 5.2)
Check:

```
dpkg -l pve-kernel-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get purge
```


Apply:

```
dpkg -l pve-kernel-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

### Unlock VMs in Proxmox

From: https://www.commandlinefu.com/commands/view/24234/unlock-vms-in-proxmox

    for i in $(qm list | awk '{ print $1 }' | grep -v VMID); do echo "Unlocking:" $i; qm unlock $i; echo "Unlocked"; done

### check health of last reboot/shutdown 

    last -xF reboot shutdown | head


## LXC Containers

## KVM/QEMU Guests

### Windows 10


* [FlexVDI Guest Tools][ref_gt_flexvdi]
* Redhat Guest Tools
* [VMWare Guest Tools][ref_gt_vwware]


#### SPICE

FlexVDI Guest Tools include latest SPICE guest agent usable with Windows 10.

#### VNC

Install the [vmmouse.sys][ref_vmmouse] driver from VMWare Guest Tools to improve mouse accuracy when using VNC. Helpful when SPICE is also in use on the same VM.



### Ubuntu

#### QEMU Guest Tools

#### SPICE Guest Tools

## Support Tools

[ref_gt_flexvdi]: http://depot.flexvdi.com/guest-tools/
[ref_gt_vwware]: https://packages.vmware.com/tools/esx/latest/windows/index.html
[ref_vmmouse]: http://pve-devel.pve.proxmox.narkive.com/LL6pc4iu/vmmouse-is-working-on-windows-too