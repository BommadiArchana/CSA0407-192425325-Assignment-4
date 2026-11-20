# Task 3.2 – Journaling and Consistency

## Introduction

File-system consistency means maintaining correct file information, directory structures and storage details. When power fails during a file operation, some data may be written while other changes remain incomplete. This can damage the file system.

## What Happens When Power Fails During a Write?

When power fails while a file is being written:

- Some data may be written successfully, while the remaining data is lost.
- File information may not be updated completely.
- Directory entries may become inconsistent.
- Some storage blocks may be marked as used even though they are not connected to a file.
- The file system may require recovery when the computer restarts.

## How Journaling Keeps the File System Consistent

Journaling records important file-system changes in a special area called a journal before applying them to the main file system.

The process is:

1. The operating system records the planned file-system changes in the journal.
2. The journal information is written to storage.
3. The actual changes are applied to the file system.
4. After successful completion, the journal transaction is marked as complete.

If power fails during the operation, the file system checks the journal during recovery. It can replay completed transactions or discard incomplete ones.

Journaling mainly protects file-system metadata. It does not automatically guarantee that every user file's contents are safe.

## How Copy-on-Write Keeps the File System Consistent

Copy-on-write (COW) does not directly overwrite existing data blocks. Instead, it writes updated information into new blocks.

The process is:

1. Existing data remains unchanged.
2. Modified data is written to new storage blocks.
3. New metadata is created to point to the updated blocks.
4. The file system updates its main reference after the new information is ready.

If power fails before the update is completed, the previous valid data and metadata can remain available. This helps prevent partially updated file-system structures.

## Comparison of ext4 Journaling Modes

| Journaling Mode | Working Method | Data Protection | Performance |
|---|---|---|---|
| Journal | Writes both file data and metadata to the journal before committing changes | Provides stronger protection for file data and metadata | Usually slower |
| Ordered | Writes file data to its final location before committing related metadata to the journal | Helps prevent metadata from pointing to unwritten data | Balanced performance and protection |
| Writeback | Journals metadata without requiring file data to be written first | Provides weaker protection for recently written file data | Usually faster |

## Conclusion

Journaling and copy-on-write help maintain file-system consistency after unexpected power failures. Journaling records changes before applying them, while copy-on-write stores updated information in new blocks. In ext4, journal mode provides stronger data protection, ordered mode provides a balance, and writeback mode gives better performance with weaker protection for recent file data.
