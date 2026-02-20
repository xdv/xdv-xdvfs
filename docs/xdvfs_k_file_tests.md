# xdvfs_k_file_tests

- Source: `xdv-xdvfs/src/xdvfs_k_file_tests.ds`
- Kind: Test Module
- Summary: XDVFS - K-Domain File Tests

## Purpose
XDVFS - K-Domain File Tests

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsKFileTests` | 0 | 9 |

## API By Forge
### XdvFsKFileTests

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `test_file_type` | `(none)` | `(none)` | Performs test file type operation. |
| `K` | `test_domain` | `(none)` | `(none)` | Performs test domain operation. |
| `K` | `test_flags` | `(none)` | `(none)` | Performs test flags operation. |
| `K` | `test_k_create` | `(none)` | `(none)` | Performs test k create operation. |
| `K` | `test_k_open` | `(none)` | `(none)` | Performs test k open operation. |
| `K` | `test_k_read` | `(none)` | `(none)` | Performs test k read operation. |
| `K` | `test_k_write` | `(none)` | `(none)` | Performs test k write operation. |
| `K` | `test_k_close` | `(none)` | `(none)` | Performs test k close operation. |
| `K` | `test_k_delete` | `(none)` | `(none)` | Performs test k delete operation. |

#### Constants
- No constants declared in this forge.

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a test/validation module for xdv-xdvfs parser/runtime checks.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = test_file_type();
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
