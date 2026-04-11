# Setup Process

## Installing KVM and Virtualization Tools

The first step in building the homelab was installing the required KVM/QEMU and virtualization management packages on the Ubuntu host system.

![Install KVM Packages](../screenshots/01-install-kvm-packages.png)

## Adding User to libvirt Group

To allow the current user to manage virtual machines without requiring elevated privileges for every operation, the user was added to the `libvirt` group.

![Add User to libvirt Group](../screenshots/02-add-user-to-libvirt-group.png)

## Rebooting the Host System

After modifying group membership, the host system was rebooted to apply the changes.

![Reboot Host](../screenshots/03-reboot-after-libvirt-config.png)

## Verifying KVM Installation

The virtualization stack was verified by checking libvirt functionality and loaded KVM kernel modules.

![Verify virsh](../screenshots/04-verify-libvirt-with-virsh.png)

![Verify KVM Modules](../screenshots/05-verify-kvm-kernel-modules.png)
