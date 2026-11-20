# CSA0407-192425325-Assignment-4

# OPTIMISING FILE STORAGE AND DISK ACCESS

## STUDENT DETAILS

- **Name:** B. Archana
- **Register Number:** 192425325
- **Course Code:** CSA04
- **Subject:** Operating Systems
- **Assignment:** Assignment 4
- **Course Outcome:** CO4
- **Total Marks:** 50

## MARK DISTRIBUTION

| Task | Topic | Bloom's Level | Marks |
|---|---|---|---:|
| Task 1 | File-System Design Review | K5 – Evaluate | 6 |
| Task 2 | File Allocation Methods | K5 – Evaluate | 8 |
| Task 3 | Modern File Systems | K5 – Evaluate | 9 |
| Task 4 | Disk Scheduling Algorithms | K5 – Evaluate | 7 |
| Task 5 | Distributed and Cloud Storage | K5 – Evaluate | 7 |
| Task 6 | Storage Design Challenge | K5 – Evaluate | 13 |
| **Total** | | | **50** |

## INTRODUCTION

This assignment focuses on file systems, file allocation methods, modern file systems, disk scheduling algorithms, distributed storage and cloud-based storage.

The main objective is to evaluate different storage techniques and identify suitable methods for improving storage performance, data availability and system efficiency.

## OBJECTIVES

- Evaluate and improve file-system organisation.
- Compare different file-allocation methods.
- Understand modern file systems and their features.
- Implement and compare disk scheduling algorithms.
- Study distributed and cloud-based storage.
- Design and evaluate a storage system for video streaming.

# TASK 1 – FILE-SYSTEM DESIGN REVIEW

**Marks: 6**

## Objective

To evaluate the existing file-system organisation of a college server and propose an improved design for storing and managing student files.

## Topics Covered

- Directory organisation.
- File naming and file attributes.
- File permissions and access control.
- File sharing.
- Cloud storage alternatives.

## Implementation

The existing flat directory structure and contiguous allocation method are evaluated. An improved directory structure is proposed using suitable naming rules, file permissions and sharing methods.

## Result

An improved file-system design is proposed to organise student files, protect privacy and support file sharing between students and staff.

# TASK 2 – FILE ALLOCATION METHODS

**Marks: 8**

## Objective

To compare different file-allocation methods and identify suitable techniques based on file-access patterns and storage requirements.

## Topics Covered

- File operations and access patterns.
- Contiguous allocation.
- Linked allocation.
- Indexed allocation.
- Free-space management.
- FAT and inode calculations.
- C programming implementation.

## Implementation

Different file-allocation methods are compared based on access time, storage efficiency, fragmentation and file growth. A C program is implemented to demonstrate file allocation.

## Compilation and Execution

```bash
gcc -std=c11 -Wall -Wextra file_allocation.c -o file_allocation
./file_allocation
```

## Result

The allocation methods are evaluated using calculations and program execution to identify suitable methods for different storage requirements.

# TASK 3 – MODERN FILE SYSTEMS

**Marks: 9**

## Objective

To evaluate modern file systems and compare their features, reliability and suitability for different applications.

## Topics Covered

- FAT32.
- NTFS.
- ext4.
- XFS.
- Btrfs.
- ZFS.
- APFS.
- Journaling and consistency.
- Copy-on-Write.
- File-system selection.
- Linux file-system inspection commands.

## Commands Used

```bash
stat filename
df -i
ls -i
tune2fs -l /dev/device
dumpe2fs -h /dev/device
```

## Implementation

Different file systems are compared based on storage capacity, journaling, snapshots, checksums and data consistency. Suitable file systems are selected for different applications.

## Result

Modern file systems are evaluated to identify suitable options for removable drives, database servers, laptops and backup servers.

# TASK 4 – DISK SCHEDULING ALGORITHMS

**Marks: 7**

## Objective

To implement and compare disk scheduling algorithms based on head movement, waiting time and fairness.

## Algorithms Covered

- FCFS.
- SSTF.
- SCAN.
- C-SCAN.
- LOOK.
- C-LOOK.

## Topics Covered

- Disk-head movement calculations.
- Disk scheduling implementation.
- Simulation of disk requests.
- Starvation and fairness.
- SSD scheduling.

## Compilation and Execution

### Disk Scheduling Program

```bash
gcc -std=c11 -Wall -Wextra disk_scheduling.c -o disk_scheduling
./disk_scheduling
```

### Simulation Program

```bash
gcc -std=c11 -Wall -Wextra simulation.c -o simulation
./simulation
```

## Implementation

The disk scheduling algorithms are implemented using C. Their total head movements are calculated and compared. A simulation is used to analyse requests under different workloads.

## Result

The algorithms are compared based on head movement, request handling, fairness and starvation. SSD scheduling is also analysed.

# TASK 5 – DISTRIBUTED AND CLOUD-BASED STORAGE

**Marks: 7**

## Objective

To compare distributed and cloud-based storage systems and understand how operating systems manage storage devices.

## Topics Covered

- Network File System (NFS).
- Distributed file systems.
- HDFS and Ceph.
- Amazon S3 and Google Cloud Storage.
- Data replication.
- Strong and eventual consistency.
- Device drivers.
- Buffering and caching.
- Spooling.
- Block-device interface.

## Implementation

NFS, distributed file systems and cloud object storage are compared based on consistency, availability, performance and cost. Replication and device management techniques are explained with examples.

## Result

Different storage options are evaluated to identify suitable methods for providing student and staff file access across multiple campuses and from home.

# TASK 6 – STORAGE DESIGN CHALLENGE

**Marks: 13**

## Objective

To design and evaluate a storage system for a video-streaming startup serving 200,000 students.

## Topics Covered

- Workload and access-pattern analysis.
- Storage architecture.
- HDD and SSD selection.
- File system and allocation method.
- Block size and disk scheduling.
- Popular video caching.
- Data replication.
- Storage capacity calculations.
- Throughput calculations.
- C workload simulation.
- Cloud object storage and CDN.

## Compilation and Execution

```bash
gcc -std=c11 -Wall -Wextra video_storage_simulation.c -o video_storage_simulation
./video_storage_simulation
```

## Implementation

A storage architecture using HDD storage and SSD caching is proposed. A C program compares HDD-only storage with an HDD and SSD cache design. Cloud object storage with CDN delivery is also evaluated.

## Result

The proposed storage designs are compared based on access latency, storage capacity, throughput, scalability and operating cost.

# SOFTWARE AND TOOLS USED

- Operating System: Windows / Linux
- Programming Language: C
- Compiler: GCC
- Code Editor: Visual Studio Code
- Version Control: Git
- Repository Hosting: GitHub

# GENERAL COMPILATION AND EXECUTION

Compile a C program:

```bash
gcc -std=c11 -Wall -Wextra filename.c -o program
```

Run on Linux:

```bash
./program
```

Run on Windows:

```bash
program.exe
```

Replace the filenames with the actual source-file and executable names.

# OVERALL RESULTS

All six tasks cover file-system organisation, file allocation, modern file systems, disk scheduling, distributed storage and storage-system design.

The practical implementations, calculations and comparisons demonstrate how different storage techniques affect performance, reliability, availability and storage efficiency.

# CONCLUSION

This assignment provides practical understanding of file storage, allocation methods, disk scheduling and distributed storage systems. The implementations and comparisons help identify suitable storage techniques based on performance, availability, capacity and cost.

