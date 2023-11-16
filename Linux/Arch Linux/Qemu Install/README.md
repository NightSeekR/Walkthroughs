# Virt-Manager & Qemu Install

### Installation

> 1. Update Arch Linux Operating System
```bash
# Update using Pacman
$ sudo pacman -Syyu
```

> 2. Install Qemu, KVM & Virt-Manager Dependancies
```bash
# Make sure you install qemu-desktop, this allows you to use QXL Graphics Driver
$ sudo pacman -S qemu-desktop virt-manager virt-viewer dnsmasq vde2 bridge-utils openbsd-netcat ebtables iptables libguestfs
```
> 3. Enable Libvirt Group & Add your User to the Group
```bash
# Edit libvirtd.conf 
$ nano /etc/libvirt/libvirtd.conf

# Uncomment Both Entries
unix_sock_group = "libvirt" 
unix_sock_rw_perms = "0770" 

# Add your User to the Libvirt Group
$ sudo usermod -aG libvirt $(whoami)
$ newgrp libvirt
```
> 4. Enable Libvirtd Service for Startup
```bash
# Enable libvirtd.service as a startup service
$ sudo systemctl enable libvirtd.service
```

> 5. Post-Reboot Enable & Autostart Default Network for Virt-Manager
```bash
# Enable Virtual Network Interface Cards (NIC)
$ sudo virsh net-start default
$ sudo virsh net-autostart default

# Reboot System
$ reboot
```
