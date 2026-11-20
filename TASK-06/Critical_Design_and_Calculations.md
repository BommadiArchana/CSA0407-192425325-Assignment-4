# Stage 3 – Critical Design Decisions (2 Marks)

## 1. Block Size

**Selected Block Size: 4 KB**

Reasons:

- Provides efficient storage management.
- Suitable for managing file-system metadata.
- Reduces unnecessary internal storage wastage for smaller files.
- Supports normal file-system operations.

Large video files are stored across multiple blocks. The file system manages their locations.

## 2. Disk Scheduler

**Selected Scheduler: MQ-Deadline**

Reasons:

- Organises disk requests into queues.
- Uses deadlines to prevent requests from waiting too long.
- Supports multiple I/O queues.
- Suitable for managing storage requests on systems where HDDs are used.

For SSD devices, the `none` scheduler can also be selected because SSDs do not have mechanical head movement.

## 3. Caching of Popular Videos

Frequently watched videos are stored in SSD cache.

**Working:**

1. The system identifies popular videos based on access frequency.
2. Frequently requested videos are copied into SSD cache.
3. When students request those videos, the system checks the cache first.
4. If the video is available, it is served from SSD.
5. Otherwise, it is retrieved from HDD or cloud storage.

**Advantages:**

- Reduces video loading time.
- Reduces repeated HDD access.
- Improves playback performance.
- Supports multiple users accessing popular videos.

## 4. Replication Factor

**Selected Replication Factor: 2**

Two copies of each important video are maintained on separate storage devices or servers.

Reasons:

- Protects against individual storage failures.
- Provides an additional copy for recovery.
- Requires less storage than three-copy replication.
- Suitable for a cost-conscious storage design.

The cloud backup provides an additional recovery option. The replication factor of two is a design choice, not a value specified in the assignment.

---

# Stage 4 – Design and Calculate (4 Marks)

## 1. Capacity Calculation

The assignment specifies that video sizes range from 300 MB to 2 GB.

For calculation, assume the start-up stores 1,000 videos, with an average size of 1 GB.

**Given:**

- Number of videos = 1,000
- Average video size = 1 GB
- Replication factor = 2

**Original Storage Capacity:**

\[
1000 \times 1\text{ GB} = 1000\text{ GB}
\]

\[
= 1\text{ TB}
\]

**Storage with Two Copies:**

\[
1000\text{ GB} \times 2 = 2000\text{ GB}
\]

\[
= 2\text{ TB}
\]

Therefore, the required storage capacity is 2 TB, excluding cache, metadata and additional backups.

## 2. Throughput Calculation

Assume 10,000 students watch videos simultaneously.

Assume the average streaming bitrate is 4 Mbps per student.

**Given:**

- Concurrent users = 10,000
- Bitrate per user = 4 Mbps

\[
\text{Total Throughput} =
10000 \times 4
\]

\[
= 40000\text{ Mbps}
\]

\[
= 40\text{ Gbps}
\]

Therefore, the system requires approximately 40 Gbps of aggregate streaming throughput under this assumed workload.

## 3. Number of Disk Reads to Start Playing at Any Minute

Assume:

- Video duration = 60 minutes
- Block size = 4 KB
- Average bitrate = 4 Mbps
- Video is encoded for random access using indexed allocation.

**Step 1: Calculate the data required per second.**

\[
4\text{ Mbps} \div 8 = 0.5\text{ MB/s}
\]

**Step 2: Calculate the data required per minute.**

\[
0.5 \times 60 = 30\text{ MB}
\]

**Step 3: Calculate the number of 4 KB blocks per minute.**

Using 1 MB = 1024 KB:

\[
\frac{30 \times 1024}{4} = 7680\text{ blocks}
\]

**Step 4: Calculate the number of blocks per second.**

\[
\frac{0.5 \times 1024}{4} = 128\text{ blocks}
\]

When a student jumps to a particular minute, the system uses the video index to locate the required section. It does not need to read all earlier video blocks.

For example, jumping to minute 30 requires locating the relevant indexed blocks and reading the data needed for playback.

**Important:** The exact number of physical disk reads cannot be calculated from the assignment information alone. It depends on the index structure, storage layout, caching, read-ahead and the video encoding's keyframe locations.

## 4. Design Summary

| Design Parameter | Selected Value |
|---|---|
| Number of videos (assumption) | 1,000 |
| Average video size (assumption) | 1 GB |
| Original capacity | 1 TB |
| Capacity with two copies | 2 TB |
| Concurrent users (assumption) | 10,000 |
| Bitrate per user (assumption) | 4 Mbps |
| Total throughput | 40 Gbps |
| Block size | 4 KB |
| File system | XFS |
| Allocation method | Indexed allocation |
| Disk scheduler | MQ-Deadline for HDD |

## Conclusion

The proposed design uses a 4 KB block size, MQ-Deadline for HDD scheduling, SSD caching and a replication factor of two. Under the stated assumptions, 1,000 videos require 2 TB of storage with two copies, and 10,000 simultaneous users require approximately 40 Gbps of streaming throughput. Indexed allocation helps locate video sections when students jump to different minutes.
