# Release Notes - kernelsu-next-joan-20260524

## Target

- Device: LG V30 H930 (`joan`)
- ROM: LineageOS 22.2 nightly `20260524`
- Kernel: Linux `4.4.302-perf+`
- KernelSU Next: `v3.2.0 legacy (33129)`
- SELinux: Enforcing

## Assets

Upload these files to the GitHub Release, not to git history:

- `kernelsu-next-boot.img`
- `kernelsu-next-boot.img.sha256`
- optional rollback: `kernelsu-boot-v0.9.5.img`
- optional rollback SHA256: `kernelsu-boot-v0.9.5.img.sha256`

Current SHA256:

```text
80d4d430491ab54e271d60d579d6ea66f197ebc59ecdc5aba677fa7dffbf7b57  kernelsu-next-boot.img
085689d5441c831d2f33a71c387f69fd4b00af12fe4e4c99ed042737cf611375  kernelsu-boot-v0.9.5.img
```

## Install

Use fastbootd. Classic bootloader fastboot can disconnect on this device while sending `boot.img`.

```bash
adb reboot fastboot
fastboot flash boot kernelsu-next-boot.img
fastboot reboot
```

Install KernelSU Next Manager `v3.2.0 (33129)`.

## Rollback

Download the official `boot.img` from the matching LineageOS build and flash it through fastbootd:

```bash
adb reboot fastboot
fastboot flash boot boot.img
fastboot reboot
```

## Known Notes

- This is not a GKI kernel.
- Upstream `tiann/KernelSU` is capped at `v0.9.5` for this kernel; the current build uses KernelSU Next `legacy` instead.
- `fastboot boot kernelsu-next-boot.img` is not recommended on LG V30; flash through fastbootd.
