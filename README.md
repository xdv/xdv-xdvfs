# XDVFS - Cross-Domain Virtualizer File System

**Version:** 0.2.0  
**Status:** Implemented  
**Language:** Dust Programming Language (DPL)  

---

## Overview

XDVFS is the native file system for the XDV Operating System. It provides domain-aware file storage supporting:

- **K-Domain (Classical)**: Full read/write/delete operations
- **Q-Domain (Quantum)**: Type awareness (operations stubbed - returns ERR_DOMAIN_NOT_AVAILABLE)
- **Φ-Domain (Phase-Native)**: Type awareness (operations stubbed - returns ERR_DOMAIN_NOT_AVAILABLE)

## Directory Structure

```
xdv-xdvfs/
├── State.toml
├── README.md
└── src/
    ├── xdvfs_errors.ds              # Error codes
    ├── xdvfs_errors_tests.ds       # Error codes tests
    ├── xdvfs_superblock.ds         # Superblock management
    ├── xdvfs_superblock_tests.ds   # Superblock tests
    ├── xdvfs_inode.ds              # Inode operations
    ├── xdvfs_inode_tests.ds        # Inode tests
    ├── xdvfs_block_alloc.ds        # Block allocation
    ├── xdvfs_block_alloc_tests.ds  # Block allocation tests
    ├── xdvfs_k_file.ds             # K-Domain file ops
    ├── xdvfs_k_file_tests.ds       # K-Domain file tests
    ├── xdvfs_q_types.ds            # Q-Domain types (stubbed)
    ├── xdvfs_q_types_tests.ds      # Q-Domain types tests
    ├── xdvfs_phi_types.ds          # Φ-Domain types (stubbed)
    ├── xdvfs_phi_types_tests.ds    # Φ-Domain types tests
    ├── xdvfs_directory.ds          # Directory operations
    ├── xdvfs_directory_tests.ds    # Directory tests
    └── xdvfs_mount.ds             # Mount operations
    └── xdvfs_mount_tests.ds       # Mount tests
```

## Implemented Features

### K-Domain (Full)
- File creation, open, read, write, close
- Directory operations (mkdir, rmdir)
- File deletion
- Block allocation

### Q-Domain (Stubbed)
- Type definitions present
- All operations return ERR_DOMAIN_NOT_AVAILABLE (100)
- `q_available()` returns 0 (false)

### Φ-Domain (Stubbed)
- Type definitions present  
- All operations return ERR_DOMAIN_NOT_AVAILABLE (100)
- `phi_available()` returns 0 (false)

## Error Codes

| Code | Description |
|------|-------------|
| 0 | Success |
| 1 | I/O Error |
| 2 | No Space |
| 3 | Not Found |
| 4 | Permission Denied |
| 5 | File Exists |
| 6 | Not a Directory |
| 7 | Invalid Handle |
| 100 | Domain Not Available |
| 200 | Invalid Filesystem |

## Usage Example

```dust
use xdv_xdvfs;

// Mount filesystem
let result = xdv_xdvfs_mount::mount("/dev/sda1", "/mnt", "xdvfs", 0);

// K-Domain file operations (full support)
let file = xdv_xdvfs_k_file::k_open("/hello.txt", 0);

// Q-Domain (not available on K-only hardware)
if xdv_xdvfs_q_types::q_available() == 0 {
    // Q-domain not available
}
```

## Build

```bash
dust check xdv-xdvfs/src
```

## Status

- [x] Error codes
- [x] Error codes tests
- [x] Superblock management
- [x] Superblock tests
- [x] Inode operations
- [x] Inode tests
- [x] Block allocation
- [x] Block allocation tests
- [x] K-File operations (FULL)
- [x] K-File tests
- [x] Q-Types (stubbed)
- [x] Q-Types tests
- [x] Φ-Types (stubbed)
- [x] Φ-Types tests
- [x] Directory operations
- [x] Directory tests
- [x] Mount operations
- [x] Mount tests

## License

Copyright © 2026 Dust LLC
