# xdvfs_block_alloc

- Source: `xdv-xdvfs/src/xdvfs_block_alloc.ds`
- Kind: Library Module
- Summary: XDVFS Block Allocator

## Purpose
XDVFS Block Allocator

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsBlockAlloc` | 14 | 5 |

## API By Forge
### XdvFsBlockAlloc

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `init_allocator` | `total_blocks: UInt64` | `(none)` | Performs init allocator operation. |
| `K` | `domain_base` | `domain: UInt8` | `(none)` | Performs domain base operation. |
| `K` | `get_free_block_count` | `alloc: UInt64, domain: UInt8` | `(none)` | Performs get free block count operation. |
| `K` | `allocate_block` | `alloc: UInt64, domain: UInt8` | `(none)` | Performs allocate block operation. |
| `K` | `free_block` | `alloc: UInt64, block_num: UInt64, domain: UInt8` | `(none)` | Performs free block operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `DOMAIN_K` | `UInt8` | `0` |
| `DOMAIN_Q` | `UInt8` | `1` |
| `DOMAIN_PHI` | `UInt8` | `2` |
| `ALLOCATOR_INVALID` | `UInt64` | `0` |
| `BLOCK_INVALID` | `UInt64` | `0` |
| `BLOCK_FREE_OK` | `UInt32` | `0` |
| `BLOCK_FREE_FAIL` | `UInt32` | `1` |
| `RESERVED_METADATA_BLOCKS` | `UInt64` | `1024` |
| `K_DOMAIN_BASE_BLOCK` | `UInt64` | `2048` |
| `Q_DOMAIN_BASE_BLOCK` | `UInt64` | `1048576` |
| `PHI_DOMAIN_BASE_BLOCK` | `UInt64` | `2097152` |
| `K_DOMAIN_RESERVE` | `UInt64` | `256` |
| `Q_DOMAIN_RESERVE` | `UInt64` | `512` |
| `PHI_DOMAIN_RESERVE` | `UInt64` | `512` |

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a production xdv-xdvfs library module intended for filesystem runtime integration.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = init_allocator(1);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
