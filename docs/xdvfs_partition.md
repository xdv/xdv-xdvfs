# xdvfs_partition

- Source: `xdv-xdvfs/src/xdvfs_partition.ds`
- Kind: Library Module
- Summary: XDVFS Partition Discovery + Table Management

## Purpose
XDVFS Partition Discovery + Table Management

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsPartition` | 16 | 13 |

## API By Forge
### XdvFsPartition

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `normalize_device_handle` | `device_handle: UInt64` | `(none)` | Performs normalize device handle operation. |
| `K` | `is_supported_partition_type` | `partition_type: UInt32` | `(none)` | Performs is supported partition type operation. |
| `K` | `detect_partition_table` | `device_handle: UInt64` | `(none)` | Performs detect partition table operation. |
| `K` | `scan_mbr_partitions` | `device_handle: UInt64` | `(none)` | Performs scan mbr partitions operation. |
| `K` | `scan_gpt_partitions` | `device_handle: UInt64` | `(none)` | Performs scan gpt partitions operation. |
| `K` | `enumerate_partitions` | `device_handle: UInt64` | `(none)` | Performs enumerate partitions operation. |
| `K` | `get_boot_partition` | `device_handle: UInt64` | `(none)` | Performs get boot partition operation. |
| `K` | `create_mbr_partition_table` | `device_handle: UInt64` | `(none)` | Performs create mbr partition table operation. |
| `K` | `create_gpt_partition_table` | `device_handle: UInt64` | `(none)` | Performs create gpt partition table operation. |
| `K` | `create_partition` | `device_handle: UInt64, start_lba: UInt64, sector_count: UInt64, partition_type: UInt32` | `(none)` | Performs create partition operation. |
| `K` | `set_partition_bootable` | `device_handle: UInt64, partition_index: UInt32` | `(none)` | Performs set partition bootable operation. |
| `K` | `layout_mbr_64m` | `(none)` | `(none)` | Performs layout mbr 64m operation. |
| `K` | `layout_gpt_64m` | `(none)` | `(none)` | Performs layout gpt 64m operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `PARTITION_STYLE_NONE` | `UInt32` | `0` |
| `PARTITION_STYLE_MBR` | `UInt32` | `1` |
| `PARTITION_STYLE_GPT` | `UInt32` | `2` |
| `PARTITION_OK` | `UInt32` | `0` |
| `PARTITION_FAIL` | `UInt32` | `1` |
| `MBR_MAX_PARTITIONS` | `UInt32` | `4` |
| `GPT_DEFAULT_PARTITIONS` | `UInt32` | `128` |
| `GPT_BOOT_LAYOUT_PARTITIONS` | `UInt32` | `3` |
| `DEFAULT_IMAGE_SIZE_MB` | `UInt32` | `64` |
| `DEFAULT_ALIGNMENT_LBA` | `UInt64` | `2048` |
| `DEFAULT_BOOT_PARTITION_INDEX` | `UInt32` | `1` |
| `PARTITION_TYPE_XDVFS` | `UInt32` | `227` |
| `PARTITION_TYPE_LINUX` | `UInt32` | `131` |
| `PARTITION_TYPE_FAT32_LBA` | `UInt32` | `12` |
| `DEFAULT_DEVICE_HANDLE` | `UInt64` | `1` |
| `GPT_HINT_DEVICE_HANDLE` | `UInt64` | `2` |

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a production xdv-xdvfs library module intended for filesystem runtime integration.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = normalize_device_handle(1);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
