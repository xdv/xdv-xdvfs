# xdvfs_errors

- Source: `xdv-xdvfs/src/xdvfs_errors.ds`
- Kind: Library Module
- Summary: XDVFS Error Codes

## Purpose
XDVFS Error Codes

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsErrors` | 18 | 2 |

## API By Forge
### XdvFsErrors

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `is_error` | `code: UInt32` | `UInt32` | Performs is error operation. |
| `K` | `is_domain_error` | `code: UInt32` | `UInt32` | Performs is domain error operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `ERR_OK` | `UInt32` | `0` |
| `ERR_IO` | `UInt32` | `1` |
| `ERR_NO_SPACE` | `UInt32` | `2` |
| `ERR_NOT_FOUND` | `UInt32` | `3` |
| `ERR_PERMISSION` | `UInt32` | `4` |
| `ERR_EXISTS` | `UInt32` | `5` |
| `ERR_NOT_DIRECTORY` | `UInt32` | `6` |
| `ERR_INVALID_HANDLE` | `UInt32` | `7` |
| `ERR_INVALID_ARG` | `UInt32` | `8` |
| `ERR_INVALID_DEVICE` | `UInt32` | `9` |
| `ERR_INVALID_PARTITION` | `UInt32` | `10` |
| `ERR_INVALID_SUPERBLOCK` | `UInt32` | `11` |
| `ERR_INVALID_INODE` | `UInt32` | `12` |
| `ERR_INVALID_BLOCK` | `UInt32` | `13` |
| `ERR_READ_ONLY` | `UInt32` | `14` |
| `ERR_DOMAIN_NOT_AVAILABLE` | `UInt32` | `100` |
| `ERR_INVALID_FILESYSTEM` | `UInt32` | `200` |
| `FLAG_TRUE` | `UInt32` | `1` |

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a production xdv-xdvfs library module intended for filesystem runtime integration.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = is_error(1);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
