# XDVFS - Cross-Domain Virtualizer File System

Version: 0.3.0  
Status: Active  
Language: Dust Programming Language (DPL)

## Overview

XDVFS is the native filesystem stack for XDV OS. It remains fully written in DPL and is designed around a hardware-aware block layer for standard storage devices.

Supported storage classes in the K-domain path:

- ATA/AHCI SATA block devices
- NVMe block devices
- USB mass storage class block devices
- VirtIO block devices

The Q and Phi domain filesystem paths remain type-aware stubs until domain-native hardware/runtime support is enabled.

## Source Layout

`src/xdvfs_errors.ds`  
Error model and canonical filesystem return codes.

`src/xdvfs_superblock.ds`  
Superblock constants and validation.

`src/xdvfs_inode.ds`  
Inode model and inode-level operations.

`src/xdvfs_block_alloc.ds`  
Block allocator interfaces.

`src/xdvfs_k_file.ds`  
K-domain file operations.

`src/xdvfs_directory.ds`  
Directory operations.

`src/xdvfs_storage_device.ds`  
Standard hardware storage abstraction and sector I/O hooks.

`src/xdvfs_partition.ds`  
MBR/GPT detection, scanning, and partition management hooks.

`src/xdvfs_format.ds`  
xdvfs formatting pipeline over block devices.

`src/xdvfs_mount.ds`  
Mount/check/format orchestration.

## Build

```bash
dust check xdv-xdvfs/src
```

## Companion Utilities

Industry-standard partitioning and formatting tool workflows are implemented in the independent workspace:

`../xdv-xdvfs-utils`

That workspace provides DPL tools aligned with:

- fdisk/parted-style partition management
- mkfs-style filesystem creation
- fsck-style filesystem consistency checks
- blkid/lsblk-style storage probing and reporting
