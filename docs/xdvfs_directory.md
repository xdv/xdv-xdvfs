# xdvfs_directory

- Source: `xdv-xdvfs/src/xdvfs_directory.ds`
- Kind: Library Module
- Summary: XDVFS Directory Operations

## Purpose
XDVFS Directory Operations

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsDirectory` | 9 | 9 |

## API By Forge
### XdvFsDirectory

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `is_valid_dir_inode` | `inode: UInt64` | `(none)` | Performs is valid dir inode operation. |
| `K` | `mkdir` | `parent_inode: UInt64, name: Str, perms: UInt16` | `(none)` | Performs mkdir operation. |
| `K` | `rmdir` | `parent_inode: UInt64, name: Str` | `(none)` | Performs rmdir operation. |
| `K` | `opendir` | `inode: UInt64` | `(none)` | Performs opendir operation. |
| `K` | `readdir` | `dir: UInt64` | `(none)` | Performs readdir operation. |
| `K` | `closedir` | `dir: UInt64` | `(none)` | Performs closedir operation. |
| `K` | `lookup` | `parent_inode: UInt64, name: Str` | `(none)` | Performs lookup operation. |
| `K` | `add_dir_entry` | `parent_inode: UInt64, name: Str, child_inode: UInt64` | `(none)` | Performs add dir entry operation. |
| `K` | `remove_dir_entry` | `parent_inode: UInt64, name: Str` | `(none)` | Performs remove dir entry operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `FILE_TYPE_DIR` | `UInt8` | `2` |
| `FILE_TYPE_FILE` | `UInt8` | `1` |
| `ROOT_INODE` | `UInt64` | `2` |
| `FIRST_DYNAMIC_INODE` | `UInt64` | `16` |
| `DIR_OK` | `UInt32` | `0` |
| `DIR_FAIL` | `UInt32` | `1` |
| `DIR_ENTRY_NOT_FOUND` | `UInt64` | `0` |
| `DEFAULT_DIR_OFFSET` | `UInt64` | `1` |
| `DEFAULT_READDIR_OFFSET` | `UInt64` | `1` |

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a production xdv-xdvfs library module intended for filesystem runtime integration.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = is_valid_dir_inode(2);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
