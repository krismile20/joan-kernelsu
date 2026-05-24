## Summary

KernelSU Next boot image for LG V30 H930 (`joan`) on LineageOS 22.2 nightly `20260524`.

- KernelSU Next `v3.2.0 legacy (33129)` for non-GKI Linux 4.4
- Based on LineageOS `android_kernel_lge_msm8998` branch `lineage-22.2`
- Verified booting on LG-H930 with KernelSU Next Manager reporting active root
- Legacy KernelSU `v0.9.5` image is kept as a rollback option

## Assets

- `kernelsu-next-boot.img`
- `kernelsu-next-boot.img.sha256`
- optional rollback: `kernelsu-boot-v0.9.5.img`
- optional rollback SHA256: `kernelsu-boot-v0.9.5.img.sha256`

SHA256:

```text
80d4d430491ab54e271d60d579d6ea66f197ebc59ecdc5aba677fa7dffbf7b57  kernelsu-next-boot.img
```

## Flash

Use fastbootd, not classic bootloader fastboot:

```bash
adb reboot fastboot
fastboot flash boot kernelsu-next-boot.img
fastboot reboot
```

Install KernelSU Next Manager `v3.2.0 (33129)`.

## Rollback

Flash the official `boot.img` from the same LineageOS build:

```bash
adb reboot fastboot
fastboot flash boot boot.img
fastboot reboot
```
