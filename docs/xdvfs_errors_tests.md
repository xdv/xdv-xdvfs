# xdvfs_errors_tests

- Source: `xdv-xdvfs/src/xdvfs_errors_tests.ds`
- Kind: Test Module
- Summary: XDVFS - Error Codes Tests

## Purpose
XDVFS - Error Codes Tests

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsErrorsTests` | 0 | 3 |

## API By Forge
### XdvFsErrorsTests

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `test_error_codes` | `(none)` | `(none)` | Performs test error codes operation. |
| `K` | `test_domain_error_codes` | `(none)` | `(none)` | Performs test domain error codes operation. |
| `K` | `test_error_to_string` | `(none)` | `(none)` | Performs test error to string operation. |

#### Constants
- No constants declared in this forge.

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a test/validation module for xdv-xdvfs parser/runtime checks.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = test_error_codes();
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
