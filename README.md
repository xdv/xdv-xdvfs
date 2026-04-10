# XDVFS - Cross-Domain Virtualizer File System

Version: 0.3.0  
Status: Active  
Language: Dust Programming Language (DPL)

## Overview

XDVFS is the native filesystem stack for XDV OS. It is written in DPL and built around a hardware-aware block layer for standard storage devices.

Supported storage classes in the K-domain path:

- ATA/AHCI SATA block devices
- NVMe block devices
- USB mass storage class block devices
- VirtIO block devices

Q and Phi paths are hardware-gated. Calls are validated and return `ERR_DOMAIN_NOT_AVAILABLE (100)` when those domain-native hardware paths are unavailable.

## Source Layout

`src/xdvfs_errors.ds`  
Filesystem error model and canonical return codes.

`src/xdvfs_storage_device.ds`  
Standard storage probing, bus mapping, and sector I/O contracts.

`src/xdvfs_partition.ds`  
MBR/GPT detection, scanning, partition creation, and 64MB layouts.

`src/xdvfs_superblock.ds`  
Superblock creation and validation.

`src/xdvfs_block_alloc.ds`  
Domain-aware block allocator contracts.

`src/xdvfs_inode.ds`  
Inode validation, allocation, and lifecycle operations.

`src/xdvfs_directory.ds`  
Directory lifecycle and entry management.

`src/xdvfs_k_file.ds`  
K-domain file create/open/read/write/close/delete operations.

`src/xdvfs_format.ds`  
Formatting pipeline over standard block devices.

`src/xdvfs_mount.ds`  
Mount, remount, sync, fsck, format, and filesystem stats orchestration.

## Build

```bash
dust check xdv-xdvfs/src
```

## 64MB Image Layout

The current image pipeline uses an xdvfs layout tuned for 64MB boot images:

- partition starts at LBA 2048
- superblock at relative LBA 8
- kernel slot at relative LBA 32
- preload payload at relative LBA 128

The preload payload includes `xdv-core`, `xdv-edx`, and `xdv-shell` content.

## Companion Utilities

Industry-standard partitioning and formatting workflows are implemented in:

`../xdv-xdvfs-utils`

That workspace provides DPL tools aligned with:

- fdisk/parted-style partition management
- mkfs-style filesystem creation
- fsck-style filesystem consistency checks
- blkid/lsblk-style storage probing and reporting
