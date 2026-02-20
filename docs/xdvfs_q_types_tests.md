# xdvfs_q_types_tests

- Source: `xdv-xdvfs/src/xdvfs_q_types_tests.ds`
- Kind: Test Module
- Summary: XDVFS - Q-Domain Types Tests

## Purpose
XDVFS - Q-Domain Types Tests

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsQTypesTests` | 0 | 10 |

## API By Forge
### XdvFsQTypesTests

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `test_q_file_type` | `(none)` | `(none)` | Performs test q file type operation. |
| `K` | `test_q_domain` | `(none)` | `(none)` | Performs test q domain operation. |
| `K` | `test_domain_not_available` | `(none)` | `(none)` | Performs test domain not available operation. |
| `K` | `test_q_available_returns_false` | `(none)` | `(none)` | Performs test q available returns false operation. |
| `K` | `test_q_get_error` | `(none)` | `(none)` | Performs test q get error operation. |
| `K` | `test_q_create_returns_error` | `(none)` | `(none)` | Performs test q create returns error operation. |
| `K` | `test_q_open_returns_error` | `(none)` | `(none)` | Performs test q open returns error operation. |
| `K` | `test_q_read_returns_error` | `(none)` | `(none)` | Performs test q read returns error operation. |
| `K` | `test_q_write_returns_error` | `(none)` | `(none)` | Performs test q write returns error operation. |
| `K` | `test_q_close_returns_error` | `(none)` | `(none)` | Performs test q close returns error operation. |

#### Constants
- No constants declared in this forge.

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a test/validation module for xdv-xdvfs parser/runtime checks.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = test_q_file_type();
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
