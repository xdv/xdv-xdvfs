# xdvfs_inode

- Source: `xdv-xdvfs/src/xdvfs_inode.ds`
- Kind: Library Module
- Summary: XDVFS Inode Management

## Purpose
XDVFS Inode Management

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsInode` | 9 | 5 |

## API By Forge
### XdvFsInode

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `is_valid_inode` | `inode_num: UInt64` | `(none)` | Performs is valid inode operation. |
| `K` | `allocate_inode` | `(none)` | `(none)` | Performs allocate inode operation. |
| `K` | `get_inode` | `inode_num: UInt64` | `(none)` | Performs get inode operation. |
| `K` | `write_inode` | `inode_num: UInt64` | `(none)` | Performs write inode operation. |
| `K` | `free_inode` | `inode_num: UInt64` | `(none)` | Performs free inode operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `TYPE_REGULAR` | `UInt16` | `1` |
| `TYPE_DIRECTORY` | `UInt16` | `2` |
| `TYPE_SYMLINK` | `UInt16` | `3` |
| `ROOT_INODE` | `UInt64` | `2` |
| `FIRST_DYNAMIC_INODE` | `UInt64` | `16` |
| `MAX_INODE_NUMBER` | `UInt64` | `1048576` |
| `INODE_OK` | `UInt32` | `0` |
| `INODE_FAIL` | `UInt32` | `1` |
| `INODE_INVALID` | `UInt64` | `0` |

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a production xdv-xdvfs library module intended for filesystem runtime integration.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = is_valid_inode(2);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
