# xdvfs_phi_types

- Source: `xdv-xdvfs/src/xdvfs_phi_types.ds`
- Kind: Library Module
- Summary: XDVFS Phi-Domain Types

## Purpose
XDVFS Phi-Domain Types

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsPhiTypes` | 8 | 8 |

## API By Forge
### XdvFsPhiTypes

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `phi_available` | `(none)` | `(none)` | Performs phi available operation. |
| `K` | `phi_get_error` | `(none)` | `(none)` | Performs phi get error operation. |
| `K` | `phi_compute_admissibility` | `phase: Float64` | `(none)` | Performs phi compute admissibility operation. |
| `K` | `phi_create` | `parent_inode: UInt64, name: Str` | `(none)` | Performs phi create operation. |
| `K` | `phi_open` | `path: Str` | `(none)` | Performs phi open operation. |
| `K` | `phi_read` | `file: UInt64` | `(none)` | Performs phi read operation. |
| `K` | `phi_write` | `file: UInt64` | `(none)` | Performs phi write operation. |
| `K` | `phi_close` | `file: UInt64` | `(none)` | Performs phi close operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `FILE_TYPE` | `UInt16` | `9` |
| `DOMAIN` | `UInt8` | `2` |
| `DOMAIN_NOT_AVAILABLE` | `UInt32` | `100` |
| `PHI_AVAILABLE_FALSE` | `UInt32` | `0` |
| `PHI_HANDLE_INVALID` | `UInt32` | `0` |
| `PHI_INVALID_ARG` | `UInt32` | `1` |
| `PHI_ADMISSIBLE` | `UInt32` | `1` |
| `PHI_NOT_ADMISSIBLE` | `UInt32` | `0` |

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a production xdv-xdvfs library module intended for filesystem runtime integration.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = phi_available();
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
