# xdvfs_phi_types_tests

- Source: `xdv-xdvfs/src/xdvfs_phi_types_tests.ds`
- Kind: Test Module
- Summary: XDVFS - Phi-Domain Types Tests

## Purpose
XDVFS - Phi-Domain Types Tests

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsPhiTypesTests` | 0 | 11 |

## API By Forge
### XdvFsPhiTypesTests

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `test_phi_file_type` | `(none)` | `(none)` | Performs test phi file type operation. |
| `K` | `test_phi_domain` | `(none)` | `(none)` | Performs test phi domain operation. |
| `K` | `test_domain_not_available` | `(none)` | `(none)` | Performs test domain not available operation. |
| `K` | `test_phi_available_returns_false` | `(none)` | `(none)` | Performs test phi available returns false operation. |
| `K` | `test_phi_get_error` | `(none)` | `(none)` | Performs test phi get error operation. |
| `K` | `test_phi_compute_admissibility` | `(none)` | `(none)` | Performs test phi compute admissibility operation. |
| `K` | `test_phi_create_returns_error` | `(none)` | `(none)` | Performs test phi create returns error operation. |
| `K` | `test_phi_open_returns_error` | `(none)` | `(none)` | Performs test phi open returns error operation. |
| `K` | `test_phi_read_returns_error` | `(none)` | `(none)` | Performs test phi read returns error operation. |
| `K` | `test_phi_write_returns_error` | `(none)` | `(none)` | Performs test phi write returns error operation. |
| `K` | `test_phi_close_returns_error` | `(none)` | `(none)` | Performs test phi close returns error operation. |

#### Constants
- No constants declared in this forge.

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a test/validation module for xdv-xdvfs parser/runtime checks.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = test_phi_file_type();
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
