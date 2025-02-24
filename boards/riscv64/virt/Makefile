# Copyright (C) 2016-2021 Wu Zhangjin <falcon@ruma.tech>
_BASE   := 1
ARCH    := riscv
XARCH   := riscv64
# Use the default setting
CPU     ?=
SMP     ?= 4
MEM     ?= 128M
QEMU    ?= v6.0.0
# Enable QEMU_US=1 for qemu-user-static
QEMU_US ?= 0
LINUX   ?= v5.18.9
BUILDROOT?= 2019.05
NETDEV_LIST := virtio
NETDEV  ?= virtio
SERIAL  ?= ttyS0

# ref: https://wiki.qemu.org/Documentation/9psetup
# 9pnet based network filesystem sharing, aarch64/virt board support both virtio-9p-pci/-virtfs and virtio-9p-device
# But virtio-9p-device requires less kernel options (no need the PCI related parts in features/linux/9pnet/)
# To eanble this function, please make sure the 9pnet feature is enabled: make feature f=9pnet && make kernel-olddefconfig
#
# TODO: add board specific 9pnet options.
#

NET9PDEV ?= virtio-9p-device

# virtio vda: https://wiki.debian.org/Arm64Qemu
ROOTDEV_LIST := /dev/vda /dev/ram0 /dev/nfs
ROOTDEV ?= /dev/vda

FSTYPE  ?= ext2

# fw_jump.elf is from https://github.com/riscv/opensbi
BIOS    ?= $(BSP_BIOS)/opensbi/generic/fw_jump.elf

KRN_ADDR ?= 0x80200000
ORIIMG  ?= arch/$(ARCH)/boot/Image
KIMAGE  ?= $(BSP_KERNEL)/$(LINUX)/Image

ROOTFS  ?= $(BSP_ROOT)/$(BUILDROOT)/rootfs.cpio.gz
HROOTFS ?= $(BSP_ROOT)/$(BUILDROOT)/rootfs.$(FSTYPE)

#XKCLI   ?= earlycon=sbi
QTOOL[OS_trusty]   ?= $(BSP_QEMU)/$(QEMU)/bin/qemu-system-$(XARCH)
QTOOL[OS_focal]   ?= $(BSP_QEMU)/$(QEMU)/bin/qemu-system-$(XARCH)

# external toolchain, please download it while: make toolchain
# Available CCORI: bootlin, gnu-mcu-eclipse
CCORI[OS_trusty]   ?= gnu-mcu-eclipse
CCORI[OS_focal]    ?= internal
