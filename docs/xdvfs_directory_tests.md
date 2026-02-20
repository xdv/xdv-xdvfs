# xdvfs_directory_tests

- Source: `xdv-xdvfs/src/xdvfs_directory_tests.ds`
- Kind: Test Module
- Summary: XDVFS - Directory Tests

## Purpose
XDVFS - Directory Tests

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsDirectoryTests` | 0 | 11 |

## API By Forge
### XdvFsDirectoryTests

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `test_file_type_dir` | `(none)` | `(none)` | Performs test file type dir operation. |
| `K` | `test_file_type_file` | `(none)` | `(none)` | Performs test file type file operation. |
| `K` | `test_root_inode` | `(none)` | `(none)` | Performs test root inode operation. |
| `K` | `test_mkdir` | `(none)` | `(none)` | Performs test mkdir operation. |
| `K` | `test_rmdir` | `(none)` | `(none)` | Performs test rmdir operation. |
| `K` | `test_opendir` | `(none)` | `(none)` | Performs test opendir operation. |
| `K` | `test_readdir` | `(none)` | `(none)` | Performs test readdir operation. |
| `K` | `test_closedir` | `(none)` | `(none)` | Performs test closedir operation. |
| `K` | `test_lookup` | `(none)` | `(none)` | Performs test lookup operation. |
| `K` | `test_add_dir_entry` | `(none)` | `(none)` | Performs test add dir entry operation. |
| `K` | `test_remove_dir_entry` | `(none)` | `(none)` | Performs test remove dir entry operation. |

#### Constants
- No constants declared in this forge.

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a test/validation module for xdv-xdvfs parser/runtime checks.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = test_file_type_dir();
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
