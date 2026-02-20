# XDVFS White Paper

Version: 0.3.0  
Status: Active Reference Design  
Language: Dust Programming Language (DPL)

## Abstract

XDVFS (Cross-Domain Virtualizer File System) is the native filesystem stack for XDV OS. It is implemented in DPL and designed as a domain-aware filesystem with a production K-domain path for standard block storage and hardware-gated Q/Phi extension paths. XDVFS provides the formatting, mounting, partition-awareness, inode/directory/file primitives, and boot image profile required by xdv-os.

This document defines the current architecture and operational behavior of `xdv-xdvfs/src` as implemented.

## 1. Design Goals

1. Provide a native filesystem contract for xdv-os that is fully implemented in DPL.
2. Operate on standard block-storage classes in bare-metal and VM environments.
3. Support xdv-os image workflows, including 64MB boot images and preload payloads.
4. Separate stable K-domain runtime functionality from future Q/Phi hardware paths.
5. Expose deterministic status/error contracts suitable for kernel/runtime integration.

## 2. Non-Goals (Current Version)

1. Q-domain and Phi-domain hardware-native file operations are not enabled in the current runtime path.
2. The current storage/partition routines provide deterministic platform contracts and validation behavior, not final hardware-driver microcode.
3. Advanced filesystem features (journaling, snapshots, ACLs, distributed metadata) are outside this version scope.

## 3. Domain Model

XDVFS uses a three-domain model:

- `K` domain: operational filesystem path for kernel/runtime/storage interaction.
- `Q` domain: quantum file-type API surface; currently hardware-gated.
- `Phi` domain: phi-domain file-type API surface; currently hardware-gated.

### 3.1 Domain Availability

- K-domain procedures are active and return operational status codes.
- Q/Phi procedures return `ERR_DOMAIN_NOT_AVAILABLE (100)` when domain-native hardware is unavailable.
- This allows stable API compatibility now while preserving forward compatibility for future domain hardware enablement.

## 4. Storage Hardware Model

XDVFS standard storage layer (`xdvfs_storage_device.ds`) supports these bus classes in K-domain contracts:

- ATA/PIO (`BUS_ATA_PIO = 1`)
- AHCI (`BUS_AHCI = 2`)
- NVMe (`BUS_NVME = 3`)
- USB Mass Storage (`BUS_USB_MASS_STORAGE = 4`)
- VirtIO Block (`BUS_VIRTIO_BLOCK = 5`)

Core constraints:

- Maximum enumerated block devices: `64`
- Maximum transfer sectors per operation: `4096`
- Logical sector size model: `512` default, `4096` for NVMe
- Physical sector size model: `4096` when device exists

## 5. Filesystem Architecture

XDVFS is organized as layered modules:

1. Error and status model (`xdvfs_errors.ds`)
2. Storage and device contracts (`xdvfs_storage_device.ds`)
3. Partition discovery and table management (`xdvfs_partition.ds`)
4. Superblock contracts (`xdvfs_superblock.ds`)
5. Block allocator (`xdvfs_block_alloc.ds`)
6. Inode lifecycle (`xdvfs_inode.ds`)
7. Directory lifecycle (`xdvfs_directory.ds`)
8. K-domain file operations (`xdvfs_k_file.ds`)
9. Formatter pipeline (`xdvfs_format.ds`)
10. Mount/orchestration path (`xdvfs_mount.ds`)
11. Q/Phi domain type extensions (`xdvfs_q_types.ds`, `xdvfs_phi_types.ds`)

## 6. On-Disk and Image Layout Profile

The xdv-os pipeline targets a 64MB XDVFS profile. Key constants include:

- Default image size: `64MB`
- Default partition alignment: `LBA 2048`
- Superblock relative LBA: `8`
- Kernel slot relative LBA: `32`
- Inode table LBA: `64`
- Preload payload LBA: `128`
- Data region LBA: `1024`

### 6.1 Reserved Slot Semantics

`xdvfs_format` reserves fixed windows for:

- Boot record
- Superblock
- Inode table
- Data region
- Kernel slot
- Preload payload slot

This stable slot contract is used by xdv-os image tooling and boot/runtime integration.

### 6.2 Runtime Path Expectation in xdv-os

In current xdv-os integration, boot runtime resolves the kernel from `xdvfs:/console/kernel.bin`. XDVFS metadata sloting remains available as part of the filesystem image contract.

## 7. Core Data Structures and Contracts

### 7.1 Error Model (`XdvFsErrors`)

Canonical error/status codes include:

- `ERR_OK = 0`
- `ERR_IO = 1`
- `ERR_NO_SPACE = 2`
- `ERR_NOT_FOUND = 3`
- `ERR_PERMISSION = 4`
- `ERR_EXISTS = 5`
- `ERR_INVALID_HANDLE = 7`
- `ERR_INVALID_ARG = 8`
- `ERR_INVALID_SUPERBLOCK = 11`
- `ERR_INVALID_INODE = 12`
- `ERR_INVALID_BLOCK = 13`
- `ERR_READ_ONLY = 14`
- `ERR_DOMAIN_NOT_AVAILABLE = 100`
- `ERR_INVALID_FILESYSTEM = 200`

Utility procedures:

- `is_error(code)`
- `is_domain_error(code)`

### 7.2 Superblock (`XdvFsSuperblock`)

Key constants:

- `MAGIC = 1479858246`
- `VERSION_MAJOR = 1`
- `VERSION_MINOR = 0`
- `BLOCK_SIZE = 4096`
- `ROOT_INODE = 2`
- `MIN_FILESYSTEM_BLOCKS = 2048`

Procedures:

- `create_superblock(total_blocks)`
- `validate_superblock(sb)`

Current creation rule is deterministic: `SUPERBLOCK_BASE + total_blocks + MAGIC_U64` when minimum block count is satisfied.

### 7.3 Partition Model (`XdvFsPartition`)

Supported partition styles:

- None (`0`)
- MBR (`1`)
- GPT (`2`)

Supported partition types:

- XDVFS (`227`)
- Linux (`131`)
- FAT32 LBA (`12`)

Partition APIs include detection, scan, enumerate, partition-table creation, partition creation, bootable flag assignment, and 64MB layout helpers.

### 7.4 Block Allocation (`XdvFsBlockAlloc`)

Domain base blocks:

- K-domain base: `2048`
- Q-domain base: `1048576`
- Phi-domain base: `2097152`

Metadata and reserve constants:

- Reserved metadata blocks: `1024`
- K reserve: `256`
- Q reserve: `512`
- Phi reserve: `512`

Allocator APIs:

- `init_allocator(total_blocks)`
- `domain_base(domain)`
- `get_free_block_count(alloc, domain)`
- `allocate_block(alloc, domain)`
- `free_block(alloc, block_num, domain)`

### 7.5 Inodes (`XdvFsInode`)

- Root inode: `2`
- First dynamic inode: `16`
- Max inode number: `1048576`

Supported inode types:

- Regular (`1`)
- Directory (`2`)
- Symlink (`3`)

### 7.6 Directories (`XdvFsDirectory`)

Directory operations:

- `mkdir`, `rmdir`
- `opendir`, `readdir`, `closedir`
- `lookup`
- `add_dir_entry`, `remove_dir_entry`

Root and dynamic inode boundaries are enforced through inode validity checks.

### 7.7 K-Domain File Ops (`XdvFsKFile`)

Supported open flags:

- `O_RDONLY`
- `O_WRONLY`
- `O_RDWR`
- `O_WRONLY + O_CREAT`
- `O_WRONLY + O_APPEND + O_CREAT`

File APIs:

- `k_create`
- `k_open`
- `k_read`
- `k_write`
- `k_close`
- `k_delete`

## 8. Mount, Format, and Lifecycle Flow

### 8.1 Mount Sequence

`mount()` orchestrates:

1. Mount flag validation
2. Storage probe
3. Partition table detection
4. Partition enumeration
5. Boot partition lookup
6. Superblock creation
7. Superblock validation
8. Mount success/fail return

### 8.2 Format Sequence

`format_xdvfs()` orchestrates:

1. Geometry validation (`block_size`, `inode_size`)
2. Boot record write
3. Superblock write
4. Inode table initialization
5. Data region initialization
6. Kernel slot reservation
7. Preload slot reservation
8. Format completion

`finalize_format()` flushes storage cache.

### 8.3 Sync and Fsck Contracts

- `sync_filesystem(handle)` normalizes handle and flushes cache.
- `check_filesystem(device)` performs probe + partition detect + superblock validation path.

## 9. Q/Phi Extension Semantics

Q and Phi modules provide typed API surfaces for cross-domain file classes while maintaining deterministic hardware-gated behavior in this version.

- Q-domain file type: `8`
- Phi-domain file type: `9`
- Domain not available return: `100`

This keeps ABI/API stable while deferring hardware enablement to future milestones.

## 10. Security and Reliability Posture

Current reliability controls include:

- Explicit status-code-based failure handling
- Handle normalization and validity checks
- Supported-flag whitelists for mount/open paths
- Explicit sync/finalize operations for persistence boundaries

Current security model is conservative and minimal by design, relying on explicit caller-side policy and mount flags (`readonly`, `noexec`, `nosuid`, `nodev`, `sync`).

## 11. Performance Characteristics (Current)

The current implementation emphasizes deterministic behavior and integration correctness.

- Most metadata operations are O(1)-style decision paths.
- Block I/O contracts enforce maximum transfer windows (`4096` sectors).
- Fixed slot layout for 64MB images minimizes boot/runtime lookup ambiguity.

As low-level hardware backends mature, these contracts provide stable control points for performance optimization.

## 12. Validation and Test Coverage

The library ships with dedicated test modules for all major areas, including:

- Errors
- Block allocation
- Inode
- Directory
- K-file ops
- Mount
- Superblock
- Q-domain types
- Phi-domain types

Test modules are located in `xdv-xdvfs/src/*_tests.ds` and documented under `xdv-xdvfs/docs`.

## 13. Integration with xdv-os Tooling

XDVFS integrates with:

- `xdv-os` image build and layout pipeline
- `xdv-boot` boot runtime kernel lookup/load path
- `xdv-runtime` and `xdv-kernel` runtime contracts
- `xdv-xdvfs-utils` companion utilities (mkfs/fsck/probe/partition workflows)

This creates a coherent storage lifecycle from image construction to boot-time mount and kernel handoff.

## 14. Compatibility and Versioning

Current format/version identifiers:

- Filesystem magic: `1479858246`
- Major version: `1`
- Minor version: `0`

Compatibility policy:

- Preserve core error/status contracts.
- Preserve K-domain API stability.
- Add Q/Phi hardware-native behavior without breaking existing K-domain paths.

## 15. Roadmap Direction

1. Promote deterministic storage/partition routines to hardware-backed implementations.
2. Expand inode and directory metadata persistence fidelity.
3. Add stronger fsck diagnostics and recovery workflows.
4. Introduce optional journaling or transactional metadata updates.
5. Enable Q/Phi domain-native operations where hardware support is present.

## Conclusion

XDVFS is the DPL-native filesystem foundation for xdv-os. The current implementation provides a complete, test-backed contract surface for storage probing, partition-aware mounting, formatting, core inode/directory/file operations, and boot image integration. Its domain-aware architecture allows immediate K-domain utility while preserving a clean path for Q/Phi hardware expansion.
