# Task 3.1 – Compare Modern File Systems

## Introduction

A file system is used by an operating system to organise, store, retrieve and manage files on a storage device. Different file systems provide different storage limits, protection methods and recovery features.

The following file systems are compared: FAT32, NTFS, ext4, XFS, Btrfs, ZFS and APFS.

## Comparison of Modern File Systems

| Feature | FAT32 | NTFS | ext4 | XFS | Btrfs | ZFS | APFS |
|---|---|---|---|---|---|---|---|
| Maximum file size | 4 GB minus 1 byte | Depends on Windows version and cluster size; up to 8 PB on supported modern Windows systems | 16 TiB | 8 EiB | Up to 16 EiB | 16 EiB | Exact maximum is not specified in Apple's published reference |
| Maximum volume size | Commonly up to 2 TB | Up to 8 PB on supported modern Windows systems | 1 EiB | Up to 16 EiB | Up to 16 EiB | Up to 256 ZiB theoretically | Exact maximum is not specified in Apple's published reference |
| Journaling | No | Yes, metadata journaling | Yes | Yes | No traditional journaling; uses copy-on-write | No traditional journaling; uses copy-on-write | Uses copy-on-write and checkpoints |
| Snapshots | No | Supported through Windows Volume Shadow Copy | Not built in; can use LVM snapshots | Not built in; can use LVM snapshots | Yes | Yes | Yes |
| Checksums | No general file-data checksums | No general file-data checksums | Metadata checksums | Metadata checksums | Data and metadata checksums | End-to-end data and metadata checksums | Metadata checksums |
| Copy-on-write | No | No | No | No | Yes | Yes | Yes |

**Note:** Storage limits are format or implementation limits, not guaranteed usable sizes on every computer. Actual limits depend on operating-system version, block size, cluster size and configuration. NTFS limits above refer to supported modern Windows versions. APFS maximum size figures are not stated here because Apple's published reference does not specify them.

## Explanation of Each File System

**FAT32**

FAT32 is an older file system commonly used in USB drives and memory cards. It supports many operating systems, including Windows and Linux. However, it has a maximum individual file size of approximately 4 GB. It does not support journaling, snapshots or copy-on-write.

**NTFS**

NTFS is the standard file system used by Windows. It supports large files, file permissions, access control, encryption and metadata journaling. Windows also provides Volume Shadow Copy for creating volume snapshots. NTFS is suitable for Windows computers and storage systems.

**ext4**

ext4 is a widely used Linux file system. It supports journaling, large files, file permissions and reliable storage management. It does not provide built-in snapshots or copy-on-write. It is commonly used for Linux operating systems and servers.

**XFS**

XFS is a high-performance Linux file system designed for handling large files and large storage volumes. It supports metadata journaling and metadata checksums. It does not provide native file-system snapshots or general copy-on-write functionality.

**Btrfs**

Btrfs is a modern Linux file system that uses copy-on-write. It supports snapshots, checksums for data and metadata, compression and error detection. It is useful for systems that require data protection and snapshot management.

**ZFS**

ZFS is an advanced file system and storage management system. It uses copy-on-write and provides snapshots, data checksums, storage pooling and data integrity checking. It is suitable for backup servers and large storage systems.

**APFS**

APFS stands for Apple File System. It is designed by Apple for macOS and other Apple devices. It supports copy-on-write metadata, snapshots, encryption and space sharing. It is optimised for modern storage devices, especially SSDs.

## Conclusion

Each file system is designed for different storage requirements. FAT32 is useful for compatibility, NTFS is suitable for Windows systems, ext4 and XFS are commonly used in Linux systems, while Btrfs and ZFS provide snapshots and copy-on-write features. APFS is designed for Apple devices. The selection depends on storage capacity, performance, compatibility and data protection requirements.
