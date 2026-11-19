# Q2 – File Allocation Methods

## Task 2.1 – Identify the File Operations

### Problem Context – Storage for a Video-Surveillance Recorder

A network video recorder stores footage from 32 cameras. Files grow continuously while recording, are read mainly from start to end, are sometimes searched by time (random access), and are deleted after 30 days.

### File Operations

The video-surveillance recorder performs the following file operations:

**File Creation**

A new video file is created when a camera starts recording or when a new recording period begins.

**Write Operation**

Video data is continuously written to storage while the cameras are recording. Since 32 cameras operate simultaneously, the system must handle continuous write operations from multiple sources.

**Sequential Read Operation**

Recorded video footage is mainly read from the beginning to the end. For example, when security staff review a complete recording, the video is accessed sequentially.

**Direct Access / Random Read**

Sometimes security staff need to search for footage from a particular date and time. The system accesses the required portion of the video without reading the entire file from the beginning.

**File Deletion**

Video files older than 30 days are deleted automatically to release storage space for new recordings.

**File Metadata Management**

The recorder maintains information such as file name, camera number, recording date, start time, end time and file size. This information helps users locate the required footage.

### File Operations, Frequency and Access Pattern

| File Operation | Frequency | Access Pattern | Purpose |
|---|---|---|---|
| File Creation | When a new recording file or recording period begins | Sequential | Creates storage files for camera footage. |
| Write | Continuous during recording | Sequential | Stores incoming video data. |
| Read | Frequently during video playback | Sequential | Plays recorded footage from beginning to end. |
| Search | Occasionally when a particular time is requested | Direct / Random | Locates footage for a specific date and time. |
| Delete | Automatically after 30 days | File-level operation | Removes expired recordings and frees storage. |
| Metadata Update | During file creation and recording | Metadata access | Maintains camera and recording information. |

### Workload Analysis

The video-surveillance recorder has a write-intensive workload because 32 cameras continuously generate video data.

Sequential access is the main pattern because most recordings are written continuously and played from start to end.

Direct access is also important because security staff sometimes need to locate a specific time within a recording.

The system must also support automatic deletion of recordings after 30 days to maintain available storage capacity.

### Conclusion

The video-surveillance recorder requires efficient file creation, continuous writing, sequential reading, direct access for time-based searches and automatic file deletion. Therefore, the selected file-allocation method should support continuous file growth, efficient sequential access and reasonable direct-access performance.
