# xdvfs_mount

- Source: `xdv-xdvfs/src/xdvfs_mount.ds`
- Kind: Library Module
- Summary: XDVFS Mount + Hardware Integration Operations

## Purpose
XDVFS Mount + Hardware Integration Operations

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsMount` | 18 | 8 |

## API By Forge
### XdvFsMount

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `is_supported_mount_flags` | `flags: UInt32` | `(none)` | Performs is supported mount flags operation. |
| `K` | `mount` | `device: Str, mount_point: Str, fs_type: Str, flags: UInt32` | `(none)` | Performs mount operation. |
| `K` | `unmount` | `mount_point: Str` | `(none)` | Performs unmount operation. |
| `K` | `remount` | `mount_point: Str, flags: UInt32` | `(none)` | Performs remount operation. |
| `K` | `sync_filesystem` | `handle: UInt64` | `(none)` | Performs sync filesystem operation. |
| `K` | `check_filesystem` | `device: Str` | `(none)` | Performs check filesystem operation. |
| `K` | `format_filesystem` | `device: Str` | `(none)` | Performs format filesystem operation. |
| `K` | `get_fs_stats` | `handle: UInt64` | `(none)` | Performs get fs stats operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `MOUNT_FLAGS_RDONLY` | `UInt32` | `1` |
| `MOUNT_FLAGS_NOEXEC` | `UInt32` | `2` |
| `MOUNT_FLAGS_NOSUID` | `UInt32` | `4` |
| `MOUNT_FLAGS_NODEV` | `UInt32` | `8` |
| `MOUNT_FLAGS_SYNC` | `UInt32` | `16` |
| `FS_KIND_XDVFS` | `UInt32` | `1` |
| `FS_KIND_FAT32` | `UInt32` | `2` |
| `FS_KIND_EXT2` | `UInt32` | `3` |
| `PARTITION_STYLE_MBR` | `UInt32` | `1` |
| `PARTITION_STYLE_GPT` | `UInt32` | `2` |
| `SUPERBLOCK_OK` | `UInt32` | `1` |
| `DEFAULT_BLOCK_SIZE` | `UInt32` | `4096` |
| `DEFAULT_INODE_SIZE` | `UInt32` | `256` |
| `DEFAULT_DEVICE_HANDLE` | `UInt64` | `1` |
| `DEFAULT_TOTAL_BLOCKS` | `UInt64` | `16384` |
| `INVALID_RESULT` | `UInt32` | `0` |
| `MOUNT_OK` | `UInt32` | `0` |
| `MOUNT_FAIL` | `UInt32` | `1` |

## Runtime Dependencies
- Detected dependency call usage:
- `create_superblock(...)`
- `detect_partition_table(...)`
- `enumerate_partitions(...)`
- `finalize_format(...)`
- `flush_storage_cache(...)`
- `format_xdvfs(...)`
- `get_boot_partition(...)`
- `normalize_device_handle(...)`
- `prepare_format_context(...)`
- `probe_standard_storage(...)`
- `validate_superblock(...)`

## Integration Notes
- This is a production xdv-xdvfs library module intended for filesystem runtime integration.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = is_supported_mount_flags(0);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
