# Troubleshooting

## ISO Detection Issue in virt-manager

### Problem
During the virtual machine setup, virt-manager failed to automatically detect the Kali Linux ISO.

### Cause
The automatic OS detection feature does not always recognize Kali Linux correctly.

### Solution
The issue was resolved by disabling automatic OS detection and manually selecting Debian 12, since Kali Linux is Debian-based.

![ISO Detection Error](../screenshots/08-iso-detection-error.png)

![Manual OS Selection](../screenshots/09-manual-debian-selection.png)

---

## Display Resolution Issues

### Problem
After installing Kali Linux, the display resolution did not adjust correctly, causing black borders and poor scaling.

### Cause
Missing guest integration tools between the host and the virtual machine.

### Solution
Installed the required guest agents:

```bash
sudo apt install qemu-guest-agent spice-vdagent -y
```

Then enabled the service:

```bash
sudo systemctl enable --now qemu-guest-agent
```

---

## Mouse Alignment Issues

### Problem
The mouse cursor inside the virtual machine did not align correctly with the host cursor.

### Cause
Lack of proper display and input integration between host and guest.

### Solution
Installing `spice-vdagent` resolved the issue and synchronized the mouse behavior.

---

## Notes

These issues are common when working with KVM/QEMU and were resolved as part of the learning process while building this homelab.
