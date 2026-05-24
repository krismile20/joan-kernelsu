# LG V30 (joan / H930) - KernelSU Next

Kernel with **KernelSU Next v3.2.0 legacy** for **LineageOS 22.2** (`lineage-22.2-20260524-nightly-joan`) on the LG V30 `joan` / H930.

This build targets the legacy **Linux 4.4.302 non-GKI** kernel. The original KernelSU `v0.9.5` build is kept only as a rollback image; the current boot image uses KernelSU Next because upstream KernelSU no longer supports non-GKI kernels after `v0.9.5`.

## Files

This repository contains scripts and patches to reproduce the KernelSU Next-enabled kernel source:

- `prepare-source.sh` - clones the LineageOS kernel, integrates KernelSU Next, and applies local patches
- `build-kernel.sh` - builds `Image.gz-dtb`
- `repack-boot.sh` - repacks an official `boot.img` with the rebuilt kernel
- `patches/` - small fixes needed for local clang builds

The ready-to-flash image is not stored in git. GitHub releases should publish it as a release asset:

- `kernelsu-next-boot.img`
- SHA256: `80d4d430491ab54e271d60d579d6ea66f197ebc59ecdc5aba677fa7dffbf7b57`

## Flash

On the LG V30, classic bootloader fastboot may disconnect while transferring the boot image. Use fastbootd:

```bash
adb reboot fastboot
fastboot flash boot kernelsu-next-boot.img
fastboot reboot
```

KernelSU Next Manager: `v3.2.0 (33129)`.

## Rollback

Flash the saved legacy KernelSU image or the original `boot.img` from the same LineageOS build through fastbootd:

```bash
adb reboot fastboot
fastboot flash boot kernelsu-boot-v0.9.5.img
fastboot reboot
```

## Build

Required tools: `clang`, `bc`, `make`, `mkbootimg`, `unpack_bootimg`, an AArch64 cross compiler, and an ARM32 EABI linker such as `arm-none-eabi-binutils`.

```bash
./prepare-source.sh
./build-kernel.sh
cp /path/to/official/boot.img stock-boot.img
./repack-boot.sh
```

## Sources and Base

- Kernel: `LineageOS/android_kernel_lge_msm8998` (`lineage-22.2`)
- KernelSU Next: `KernelSU-Next/KernelSU-Next` branch `legacy` (`v3.2.0-legacy`)
- Official base boot image: `lineage-22.2-20260524-nightly-joan`
