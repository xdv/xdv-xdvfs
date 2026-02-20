# xdvfs_storage_device

- Source: `xdv-xdvfs/src/xdvfs_storage_device.ds`
- Kind: Library Module
- Summary: XDVFS Standard Storage Hardware Layer

## Purpose
XDVFS Standard Storage Hardware Layer

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvFsStorageDevice` | 17 | 11 |

## API By Forge
### XdvFsStorageDevice

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `probe_standard_storage` | `(none)` | `(none)` | Performs probe standard storage operation. |
| `K` | `enumerate_block_devices` | `(none)` | `(none)` | Performs enumerate block devices operation. |
| `K` | `normalize_device_handle` | `device_handle: UInt64` | `(none)` | Performs normalize device handle operation. |
| `K` | `device_exists` | `device_handle: UInt64` | `(none)` | Performs device exists operation. |
| `K` | `identify_block_device` | `device_handle: UInt64` | `(none)` | Performs identify block device operation. |
| `K` | `get_device_bus` | `device_handle: UInt64` | `(none)` | Performs get device bus operation. |
| `K` | `get_logical_sector_size` | `device_handle: UInt64` | `(none)` | Performs get logical sector size operation. |
| `K` | `get_physical_sector_size` | `device_handle: UInt64` | `(none)` | Performs get physical sector size operation. |
| `K` | `read_sectors` | `device_handle: UInt64, lba: UInt64, count: UInt32` | `(none)` | Performs read sectors operation. |
| `K` | `write_sectors` | `device_handle: UInt64, lba: UInt64, count: UInt32` | `(none)` | Performs write sectors operation. |
| `K` | `flush_storage_cache` | `device_handle: UInt64` | `(none)` | Performs flush storage cache operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `BUS_ATA_PIO` | `UInt32` | `1` |
| `BUS_AHCI` | `UInt32` | `2` |
| `BUS_NVME` | `UInt32` | `3` |
| `BUS_USB_MASS_STORAGE` | `UInt32` | `4` |
| `BUS_VIRTIO_BLOCK` | `UInt32` | `5` |
| `DEVICE_CLASS_NONE` | `UInt32` | `0` |
| `DEVICE_CLASS_BLOCK` | `UInt32` | `1` |
| `SECTOR_SIZE_512` | `UInt32` | `512` |
| `SECTOR_SIZE_4096` | `UInt32` | `4096` |
| `STORAGE_OK` | `UInt32` | `0` |
| `STORAGE_FAIL` | `UInt32` | `1` |
| `STORAGE_INVALID_DEVICE` | `UInt32` | `2` |
| `STORAGE_INVALID_TRANSFER` | `UInt32` | `3` |
| `DEFAULT_DEVICE_HANDLE` | `UInt64` | `1` |
| `MAX_STANDARD_BLOCK_DEVICES` | `UInt32` | `64` |
| `MAX_TRANSFER_SECTORS` | `UInt32` | `4096` |
| `ZERO_SECTORS` | `UInt32` | `0` |

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- This is a production xdv-xdvfs library module intended for filesystem runtime integration.
- Generated docs are synchronized from source signatures/constants.

## Example (DPL)
```dust
let status = probe_standard_storage();
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
