# Setup Process

## Installing KVM and Virtualization Tools

The first step in building the homelab was installing the required KVM/QEMU and virtualization management packages on the Ubuntu host system.

![Install KVM Packages](../screenshots/01-install-kvm-packages.png)

## Adding User to libvirt Group

To allow the current user to manage virtual machines without requiring root privileges, the user was added to the `libvirt` group using the following command:

```bash
sudo usermod -aG libvirt $USER
```

After this change, a system reboot is required for the new group permissions to take effect.

![Add User to libvirt Group](../screenshots/02-add-user-to-libvirt-group.png)

## Rebooting the Host System

After modifying group membership, the host system was rebooted to apply the changes.

![Reboot Host](../screenshots/03-reboot-after-libvirt-config.png)

## Verifying KVM Installation

The virtualization stack was verified by checking libvirt functionality and loaded KVM kernel modules.

![Verify virsh](../screenshots/04-verify-libvirt-with-virsh.png)

![Verify KVM Modules](../screenshots/05-verify-kvm-kernel-modules.png)

## Creating the Virtual Machine

The virtual machine was created using virt-manager by selecting the option to create a new VM.

![Create VM](../screenshots/07-create-new-virtual-machine.png)

## ISO Detection Issue

During the setup process, virt-manager failed to automatically detect the Kali Linux ISO.

![ISO Detection Error](../screenshots/08-iso-detection-error.png)

## Manual OS Selection

To resolve this issue, automatic OS detection was disabled and Debian 12 was selected manually, since Kali is Debian-based.

![Manual Debian Selection](../screenshots/09-manual-debian-selection.png)

## Customizing VM Configuration

Before starting the installation, the option to customize the virtual machine configuration was enabled.

This allows adjusting hardware settings such as RAM, CPU, and storage before booting the installer.

![Customize VM](../screenshots/10-customize-vm-before-install.png)

## Kali Linux Installation

The installation was performed using the graphical installer provided by Kali Linux.

![Kali Installer](../screenshots/11-kali-graphical-installer.png)

## Updating the System

After installation, the Kali Linux system was updated to ensure all packages were up to date.

```bash
sudo apt update && sudo apt upgrade -y
```

![Update Kali](../screenshots/12-update-kali-system.png)

## Installing Guest Agents

To improve integration between the host and the virtual machine (such as better display handling and performance), guest agent tools were installed.

```bash
sudo apt install qemu-guest-agent spice-vdagent -y
```

![Install Guest Agents](../screenshots/13-install-guest-agents.png)

## Enabling Guest Services

The guest agent service was enabled and started to allow proper communication between host and guest.

```bash
sudo systemctl enable --now qemu-guest-agent
```

![Enable Guest Services](../screenshots/14-enable-guest-services.png)

## Verifying Guest Agent Status

The service status was verified to ensure it was running correctly.

![Guest Agent Running](../screenshots/17-guest-services-running.png)

## Final Result

The virtual machine was successfully installed and configured, with Kali Linux running smoothly inside the KVM environment.

![Kali Desktop](../screenshots/15-kali-desktop-running.png)

![VM Running](../screenshots/16-vm-running-in-virt-manager.png)
