# xdvfs_k_file

- Source: `xdv-xdvfs/src/xdvfs_k_file.ds`
- Kind: Library Module
- Summary: XDVFS K-Domain File Operations

## Purpose
XDVFS K-Domain File Operations

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsKFile` | 12 | 7 |

## API By Forge
### XdvFsKFile

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `is_supported_open_flags` | `flags: UInt32` | `(none)` | Performs is supported open flags operation. |
| `K` | `k_create` | `parent_inode: UInt64, name: Str, perms: UInt16` | `(none)` | Performs k create operation. |
| `K` | `k_open` | `path: Str, flags: UInt32` | `(none)` | Performs k open operation. |
| `K` | `k_read` | `file: UInt64, count: UInt32` | `(none)` | Performs k read operation. |
| `K` | `k_write` | `file: UInt64, data_size: UInt32` | `(none)` | Performs k write operation. |
| `K` | `k_close` | `file: UInt64` | `(none)` | Performs k close operation. |
| `K` | `k_delete` | `parent_inode: UInt64, name: Str` | `(none)` | Performs k delete operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `FILE_TYPE` | `UInt16` | `1` |
| `DOMAIN` | `UInt8` | `0` |
| `O_RDONLY` | `UInt32` | `0` |
| `O_WRONLY` | `UInt32` | `1` |
| `O_RDWR` | `UInt32` | `2` |
| `O_CREAT` | `UInt32` | `64` |
| `O_APPEND` | `UInt32` | `1024` |
| `FILE_OK` | `UInt32` | `0` |
| `FILE_FAIL` | `UInt32` | `1` |
| `FILE_HANDLE_INVALID` | `UInt64` | `0` |
| `FILE_HANDLE_BASE` | `UInt64` | `2` |
| `MIN_INODE` | `UInt64` | `2` |

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a production xdv-xdvfs library module intended for filesystem runtime integration.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = is_supported_open_flags(0);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
