# xdvfs_format

- Source: `xdv-xdvfs/src/xdvfs_format.ds`
- Kind: Library Module
- Summary: XDVFS Formatter Core

## Purpose
XDVFS Formatter Core

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsFormat` | 24 | 10 |

## API By Forge
### XdvFsFormat

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `is_valid_format_geometry` | `block_size: UInt32, inode_size: UInt32` | `(none)` | Performs is valid format geometry operation. |
| `K` | `prepare_format_context` | `device_handle: UInt64, block_size: UInt32, inode_size: UInt32` | `(none)` | Performs prepare format context operation. |
| `K` | `write_boot_record` | `device_handle: UInt64` | `(none)` | Performs write boot record operation. |
| `K` | `write_superblock` | `device_handle: UInt64` | `(none)` | Performs write superblock operation. |
| `K` | `initialize_inode_table` | `device_handle: UInt64` | `(none)` | Performs initialize inode table operation. |
| `K` | `initialize_data_region` | `device_handle: UInt64` | `(none)` | Performs initialize data region operation. |
| `K` | `write_kernel_slot` | `device_handle: UInt64` | `(none)` | Performs write kernel slot operation. |
| `K` | `write_preload_payload` | `device_handle: UInt64` | `(none)` | Performs write preload payload operation. |
| `K` | `format_xdvfs` | `device_handle: UInt64, block_size: UInt32, inode_size: UInt32` | `(none)` | Performs format xdvfs operation. |
| `K` | `finalize_format` | `device_handle: UInt64` | `(none)` | Performs finalize format operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `FS_KIND_XDVFS` | `UInt32` | `1` |
| `FS_KIND_FAT32` | `UInt32` | `2` |
| `FS_KIND_EXT2` | `UInt32` | `3` |
| `DEFAULT_BLOCK_SIZE` | `UInt32` | `4096` |
| `DEFAULT_INODE_SIZE` | `UInt32` | `256` |
| `DEFAULT_IMAGE_SIZE_MB` | `UInt32` | `64` |
| `FORMAT_OK` | `UInt32` | `0` |
| `FORMAT_FAIL` | `UInt32` | `1` |
| `SUPERBLOCK_LBA` | `UInt64` | `8` |
| `KERNEL_IMAGE_LBA` | `UInt64` | `32` |
| `PRELOAD_PAYLOAD_LBA` | `UInt64` | `128` |
| `INODE_TABLE_LBA` | `UInt64` | `64` |
| `DATA_REGION_LBA` | `UInt64` | `1024` |
| `BOOT_RECORD_LBA` | `UInt64` | `0` |
| `ONE_SECTOR` | `UInt32` | `1` |
| `INODE_TABLE_SECTORS` | `UInt32` | `32` |
| `DATA_REGION_SECTORS` | `UInt32` | `64` |
| `KERNEL_SLOT_SECTORS` | `UInt32` | `64` |
| `PRELOAD_SLOT_SECTORS` | `UInt32` | `128` |
| `INVALID_LBA` | `UInt64` | `0` |
| `MIN_BLOCK_SIZE` | `UInt32` | `512` |
| `MAX_BLOCK_SIZE` | `UInt32` | `65536` |
| `MIN_INODE_SIZE` | `UInt32` | `128` |
| `MAX_INODE_SIZE` | `UInt32` | `1024` |

## Runtime Dependencies
- Detected dependency call usage:
- `flush_storage_cache(...)`
- `write_sectors(...)`

## Integration Notes
- This is a production xdv-xdvfs library module intended for filesystem runtime integration.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = is_valid_format_geometry(512, 512);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
