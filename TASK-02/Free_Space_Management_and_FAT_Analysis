# Q2 – Free-Space Management and FAT Analysis

## Task 2.4 – Free-Space Management

### Introduction

Free-space management is an important function of an operating system. It keeps track of unused disk blocks so that the operating system can allocate them to newly created files.

For a 4 TB disk, an efficient free-space management technique is required to identify available blocks and allocate storage properly.

### Bit Vector

A bit vector uses one bit for every disk block.

- A bit value of 0 represents a free block.
- A bit value of 1 represents an allocated block.
- The operating system checks the bit vector to find available blocks.

**Advantages:**
- Simple to implement.
- Easy to identify consecutive free blocks.
- Requires only one bit per disk block.

**Disadvantages:**
- The bit vector can become large for disks containing many small blocks.
- Searching for free blocks requires scanning the vector unless additional indexing is used.

### Linked Free List

A linked free list stores pointers connecting all free disk blocks.

Each free block contains a pointer to the next free block.

**Advantages:**
- Simple method for tracking free blocks.
- Does not require a large separate bit vector.
- Blocks can be allocated and released using the list.

**Disadvantages:**
- Finding consecutive free blocks is difficult.
- Traversing the list may require multiple disk accesses.
- A damaged pointer can affect the remaining free-block list.

### Grouping

Grouping is a technique in which one free block stores the addresses of several other free blocks.

The final entry points to another block containing additional free-block addresses.

**Advantages:**
- Several free blocks can be identified using one group.
- Reduces the need to traverse individual free blocks.
- Makes free-space management more efficient than a simple linked list.

**Disadvantages:**
- Additional management is required for groups.
- A damaged group block can affect access to multiple free blocks.

### Counting

Counting stores the starting address of a sequence of consecutive free blocks and the number of blocks in that sequence.

For example, if blocks 100 to 149 are free, the system stores the starting block as 100 and the count as 50.

**Advantages:**
- Requires less information when many consecutive blocks are free.
- Efficient for systems where free blocks occur in continuous runs.
- Makes allocation of consecutive blocks easier.

**Disadvantages:**
- Less efficient when free blocks are highly scattered.
- The system must update the starting address and count when blocks are allocated or released.

### Comparison of Free-Space Management Methods

| Feature | Bit Vector | Linked Free List | Grouping | Counting |
|---|---|---|---|---|
| Storage Method | One bit per block | Linked pointers | Groups of free-block addresses | Starting block and count |
| Searching | Scans the bitmap | Traverses the list | Searches groups | Searches free-block ranges |
| Consecutive Blocks | Easy to identify | Difficult | Depends on group information | Easy to identify |
| Storage Overhead | One bit per block | Pointer in each free block | Group information | Start and count entries |
| Main Advantage | Simple and compact | Easy block tracking | Finds multiple free blocks together | Efficient for continuous free space |
| Main Limitation | Bitmap scanning | Slow traversal | Group management | Less effective for scattered blocks |

### Bit Vector Size Calculation for a 4 TB Disk

Assume the disk uses 4 KB blocks.

**Given:**

- Disk capacity = 4 TB
- Block size = 4 KB
- Each disk block requires 1 bit in the bit vector.

**Step 1 – Calculate the number of disk blocks**

Number of blocks = Disk capacity / Block size

= (4 × 2⁴⁰) / (4 × 2¹⁰)

= 2³⁰ blocks

**Step 2 – Calculate the bit vector size**

Bit vector size = Number of blocks × 1 bit

= 2³⁰ bits

**Step 3 – Convert bits into bytes**

= 2³⁰ / 8

= 2²⁷ bytes

= 128 MB

**Final Answer:**

The bit vector requires **128 MB** of storage for a 4 TB disk using 4 KB blocks.

Note: The assignment does not specify the disk block size for this calculation. The 4 KB block size is an explicit assumption. The result changes if a different block size is used.

## Alternative Concept and Complexity Analysis – FAT

### Introduction

The alternative concept in the assignment is linked allocation using a File Allocation Table (FAT) held in memory instead of indexed allocation.

In FAT, each disk block has an entry that identifies the next block belonging to the file. The operating system follows these entries to access the file.

### Working of FAT

- Each file is stored in a chain of disk blocks.
- The FAT maintains the next-block information.
- The FAT is loaded into memory for faster access.
- The operating system follows the block chain to locate the required data.

### Time to Reach Block K

In linked allocation using FAT, reaching block K requires following the chain of FAT entries from the beginning of the file.

Time complexity: **O(k)** for reaching block k using a simple chain traversal.

In indexed allocation, the required block address can be obtained directly from the index structure.

Time complexity: **O(1)** for a single-level index lookup when the index block is already available in memory.

Therefore, indexed allocation is more suitable for frequent direct access, while FAT supports sequential access and file growth.

### FAT Memory Calculation for a 4 TB Disk

Assume:

- Disk capacity = 4 TB.
- Block size = 4 KB.
- Each FAT entry = 4 bytes.

Number of disk blocks:

= 4 TB / 4 KB

= 2³⁰ blocks

FAT memory required:

= Number of entries × Size of each entry

= 2³⁰ × 4 bytes

= 2³² bytes

= **4 GB**

Therefore, the FAT requires approximately 4 GB of memory under these assumptions.

### Reliability if FAT Is Damaged

The FAT contains information about the relationships between file blocks. If the FAT is damaged, the operating system may lose the information needed to locate the remaining blocks of files.

This can make files inaccessible or cause data loss.

Maintaining backup copies of the FAT and using file-system checking tools can help detect and recover from such problems.

### Indexed Allocation vs FAT

| Feature | Indexed Allocation | Linked Allocation using FAT |
|---|---|---|
| Block Location | Stored in an index block | Stored in the FAT |
| Direct Access | Fast using the index | Requires following FAT entries |
| Sequential Access | Supported | Supported |
| File Growth | Easy by adding block addresses | Easy by extending the block chain |
| Memory Requirement | Index-block storage | FAT table storage |
| Reliability | Index-block damage can affect a file | FAT damage can affect multiple files |

### Complexity Analysis

| Operation | Indexed Allocation | FAT Linked Allocation |
|---|---|---|
| Sequential Access | O(n) | O(n) |
| Direct Access to Block K | O(1) with index available | O(k) chain traversal |
| Storage Overhead | Index block addresses | FAT entry for each disk block |

### Conclusion

Bit vectors, linked free lists, grouping and counting are different methods of managing free disk space. A bit vector provides a simple way to identify free blocks, while grouping and counting can reduce search and storage overhead in suitable workloads.

FAT supports file growth and sequential access, but reaching a particular block may require following multiple entries. Indexed allocation provides faster direct access. For the video-surveillance recorder, indexed allocation is a suitable choice when both sequential playback and time-based direct access are important.
