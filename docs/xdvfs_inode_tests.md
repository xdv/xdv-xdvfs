# xdvfs_inode_tests

- Source: `xdv-xdvfs/src/xdvfs_inode_tests.ds`
- Kind: Test Module
- Summary: XDVFS - Inode Tests

## Purpose
XDVFS - Inode Tests

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsInodeTests` | 0 | 6 |

## API By Forge
### XdvFsInodeTests

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `test_inode_types` | `(none)` | `(none)` | Performs test inode types operation. |
| `K` | `test_root_inode` | `(none)` | `(none)` | Performs test root inode operation. |
| `K` | `test_allocate_inode` | `(none)` | `(none)` | Performs test allocate inode operation. |
| `K` | `test_get_inode` | `(none)` | `(none)` | Performs test get inode operation. |
| `K` | `test_write_inode` | `(none)` | `(none)` | Performs test write inode operation. |
| `K` | `test_free_inode` | `(none)` | `(none)` | Performs test free inode operation. |

#### Constants
- No constants declared in this forge.

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a test/validation module for xdv-xdvfs parser/runtime checks.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = test_inode_types();
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
