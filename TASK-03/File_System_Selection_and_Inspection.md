# Task 3.4 – Inspect a Real File System

## Aim

To inspect a Linux file system and identify inode information, block size and available storage space using Linux commands.

## Commands Used

**1. stat**

The `stat` command displays information about a file, including its size, inode number and permissions.

Command:
```bash
stat sample.txt
```

**2. df -i**

The `df -i` command displays inode usage, including total, used and available inodes.

Command:
```bash
df -i
```

**3. ls -i**

The `ls -i` command displays the inode number of each file in a directory.

Command:
```bash
ls -i
```

**4. tune2fs -l**

The `tune2fs -l` command displays detailed information about an ext2, ext3 or ext4 file system, including block size and free blocks.

Command:
```bash
sudo tune2fs -l /dev/sda1
```

Replace `/dev/sda1` with the actual Linux partition name.

Alternative command:
```bash
sudo dumpe2fs -h /dev/sda1
```

## Procedure

1. Open the Linux terminal.
2. Create a sample file using `touch sample.txt`.
3. Execute `stat sample.txt` to view file information.
4. Execute `df -i` to check inode usage.
5. Execute `ls -i` to display inode numbers.
6. Identify the Linux partition using `df -T`.
7. Execute `sudo tune2fs -l` with the correct ext partition to view block size and free blocks.
8. Record the command outputs.

## Expected Output

**Command:**
```bash
stat sample.txt
```

Output includes:
```text
File: sample.txt
Size: 0
Inode: (inode number)
Access: (file permissions)
```

**Command:**
```bash
df -i
```

Output displays:
```text
Filesystem     Inodes   IUsed   IFree   IUse%
/dev/sda1      (value)  (value) (value) (value)
```

**Command:**
```bash
ls -i
```

Output:
```text
(inode number) sample.txt
```

**Command:**
```bash
sudo tune2fs -l /dev/sda1
```

Output includes:
```text
Block count: (total blocks)
Free blocks: (available blocks)
Block size: (block size in bytes)
```

## Result

The Linux file system was inspected successfully using `stat`, `df -i`, `ls -i` and `tune2fs -l` or `dumpe2fs -h`. The commands provide information about file details, inode usage, block size and available storage space.
