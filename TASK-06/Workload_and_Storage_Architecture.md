# Storage Design for a Video-Streaming Start-up

## Stage 1 – Interpret the Workload (2 Marks)

### 1. Operations

The video-streaming system performs the following operations:

- Upload: Videos are uploaded to the storage system.
- Read: Students watch stored videos.
- Random access: Students jump to any minute of a video.
- Repeated access: Popular videos are accessed thousands of times.
- Caching: Frequently watched videos are stored in faster storage.
- Backup: Copies of videos are maintained to protect against data loss.

### 2. Access Patterns

The system mainly uses read operations because videos are uploaded once and watched many times.

| Operation | Access Pattern | Description |
|---|---|---|
| Video upload | Sequential write | Video data is uploaded and stored |
| Video playback | Sequential read | Video is read during playback |
| Jump to any minute | Random access | A particular video section is accessed |
| Popular video access | Repeated read | The same video is accessed by many students |
| Backup | Sequential read/write | Video data is copied to backup storage |

### 3. Performance Targets

The following are proposed testable targets for the system. They are design goals, not measurements supplied by the assignment.

| Requirement | Proposed Target |
|---|---|
| Video playback startup | Within 3 seconds under normal network conditions |
| Video seeking | Start the selected section within 2 seconds under normal conditions |
| Video availability | 99.9% monthly service availability |
| Popular video access | Frequently watched videos should be served from cache |
| Data protection | Maintain at least two copies of important video data |
| Concurrent users | Support the expected student workload through capacity testing |

## Stage 2 – Propose the Storage Architecture (2 Marks)

### 1. Storage Architecture

The proposed system uses SSDs, HDDs and cloud storage for different purposes.

**SSD Storage:**

- Stores frequently accessed videos.
- Provides fast read access.
- Suitable for popular videos during the first week.
- Helps reduce video startup and seeking delays.

**HDD Storage:**

- Stores the main collection of uploaded videos.
- Provides large storage capacity at a lower cost per GB than SSDs.
- Suitable for videos that are not frequently accessed.

**Cloud Storage:**

- Maintains an additional copy of video files.
- Provides storage expansion when required.
- Allows videos to be accessed from different locations.
- Can be combined with a content-delivery network for wider distribution.

### 2. Selected File System

**Selected File System: XFS**

Reasons:

- Supports large files.
- Designed for high-performance storage.
- Suitable for handling large video files.
- Supports large storage volumes.
- Provides metadata journaling.

XFS is suitable for the video server's Linux-based storage system.

### 3. Selected File Allocation Method

**Selected Method: Indexed Allocation**

Reasons:

- Supports direct access to file blocks.
- Allows students to jump to different video sections.
- Does not require all file blocks to be stored continuously.
- Supports large video files.

An index structure stores references to the data blocks belonging to a video. The system can locate the required block without reading all earlier blocks in sequence.

### 4. Proposed Architecture Flow

```text
        Students
            |
            v
      Video Streaming
         Server
            |
            v
      Popular Video
          Cache
            |
       -------------
       |           |
       v           v
    SSD Storage  HDD Storage
       |           |
       -------------
            |
            v
       Cloud Backup
```

### 5. Working of the Proposed System

1. The administrator uploads lecture videos to the storage system.
2. Videos are stored in the main HDD storage.
3. Frequently accessed videos are copied or cached on SSD storage.
4. Students request videos through the streaming server.
5. The system checks the cache for the requested video section.
6. If the required section is not available in the cache, it is retrieved from HDD or cloud storage.
7. Indexed allocation helps locate the required video blocks.
8. Backup copies protect the stored videos against data loss.

## Conclusion

The proposed architecture uses HDDs for storing the main video collection, SSDs for frequently accessed videos and cloud storage for additional backup and expansion. XFS is selected as the file system, and indexed allocation supports direct access when students jump to different minutes of a video.
