# Q2 – File Allocation Methods

## Task 2.2 – Compare File Allocation Methods

### Introduction

File allocation methods determine how files are stored in disk blocks. The three major methods are contiguous allocation, linked allocation and indexed allocation.

For the video-surveillance recorder storing footage from 32 cameras, selecting a suitable allocation method is important because video files grow continuously, are mainly read sequentially and are sometimes accessed directly using a particular time.

### Contiguous Allocation

In contiguous allocation, a file is stored in consecutive disk blocks.

**Advantages:**
- Provides fast sequential access.
- Supports direct access because block locations can be calculated.
- Requires simple file-location information.
- Provides good performance when files are stored in consecutive blocks.

**Disadvantages:**
- File growth is difficult when adjacent blocks are occupied.
- External fragmentation may occur.
- Files may need to be moved to another location when additional space is required.

### Linked Allocation

In linked allocation, each file block contains a pointer to the next block. The blocks can be located anywhere on the disk.

**Advantages:**
- Files can grow easily.
- External fragmentation is avoided.
- No need to reserve a large continuous area.

**Disadvantages:**
- Direct access is slow because blocks must be followed one by one.
- Pointer storage creates additional overhead.
- If a pointer is damaged, part of the file may become inaccessible.

### File Allocation Table (FAT)

FAT is a variation of linked allocation. Instead of storing the next-block pointer inside each data block, the pointers are maintained in a File Allocation Table.

The FAT records the sequence of blocks belonging to each file. Keeping the table in memory can improve access compared with reading pointers from individual disk blocks.

**Advantages:**
- Supports file growth.
- Makes block-chain management easier.
- FAT can be kept in memory for faster lookup.

**Disadvantages:**
- Accessing a later block may require following multiple FAT entries.
- The FAT requires memory.
- Damage to the FAT can affect access to many files.

### Indexed Allocation

In indexed allocation, each file has an index block that stores the addresses of its data blocks.

The operating system uses the index block to locate the required data block.

**Advantages:**
- Supports direct and sequential access.
- Files can grow by adding new block addresses.
- Avoids external fragmentation.
- Data blocks do not need to be stored consecutively.

**Disadvantages:**
- Additional storage is required for index blocks.
- Small files may waste space in their index blocks.
- Large files may require multiple levels of indexing.

### Comparison of File Allocation Methods

| Feature | Contiguous Allocation | Linked Allocation (FAT) | Indexed Allocation |
|---|---|---|---|
| Sequential Access | Very fast | Good | Good |
| Direct Access | Fast | Slow in ordinary linked allocation; FAT requires following entries | Fast using index block |
| File Growth | Difficult | Easy | Easy |
| External Fragmentation | Occurs | Does not occur | Does not occur |
| Storage Overhead | Low | Pointer or FAT storage | Index block storage |
| Reliability | File movement or fragmentation can create management problems | Pointer or FAT damage can affect file access | Index block damage can affect file access |
| Block Location | Consecutive blocks | Blocks can be anywhere | Blocks can be anywhere |

### Suitable Method for the Video-Surveillance Recorder

The recorder stores footage continuously from 32 cameras. Most recordings are read sequentially, but security staff also need to access specific portions of recordings using date and time.

Indexed allocation is a suitable choice because it supports both sequential and direct access. It also allows video files to grow by adding data-block addresses to the index structure without requiring one large continuous storage area.

Linked allocation with FAT is another possible choice because it supports file growth, but reaching a particular block may require following multiple FAT entries.

Contiguous allocation provides good access performance, but continuous file growth can be difficult and may cause external fragmentation.

### Conclusion

Contiguous allocation provides fast access but has limitations when files grow. Linked allocation supports file growth but makes direct access slower. Indexed allocation provides a good balance between sequential access, direct access and file growth. Therefore, indexed allocation is a suitable option for the video-surveillance recorder workload.
