# xdvfs_q_types

- Source: `xdv-xdvfs/src/xdvfs_q_types.ds`
- Kind: Library Module
- Summary: XDVFS Q-Domain Types

## Purpose
XDVFS Q-Domain Types

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsQTypes` | 6 | 7 |

## API By Forge
### XdvFsQTypes

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `q_available` | `(none)` | `(none)` | Performs q available operation. |
| `K` | `q_get_error` | `(none)` | `(none)` | Performs q get error operation. |
| `K` | `q_create` | `parent_inode: UInt64, name: Str, qubit_count: UInt32, coherence_ns: UInt64` | `(none)` | Performs q create operation. |
| `K` | `q_open` | `path: Str` | `(none)` | Performs q open operation. |
| `K` | `q_read` | `file: UInt64` | `(none)` | Performs q read operation. |
| `K` | `q_write` | `file: UInt64` | `(none)` | Performs q write operation. |
| `K` | `q_close` | `file: UInt64` | `(none)` | Performs q close operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `FILE_TYPE` | `UInt16` | `8` |
| `DOMAIN` | `UInt8` | `1` |
| `DOMAIN_NOT_AVAILABLE` | `UInt32` | `100` |
| `Q_AVAILABLE_FALSE` | `UInt32` | `0` |
| `Q_HANDLE_INVALID` | `UInt32` | `0` |
| `Q_INVALID_ARG` | `UInt32` | `1` |

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a production xdv-xdvfs library module intended for filesystem runtime integration.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = q_available();
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
