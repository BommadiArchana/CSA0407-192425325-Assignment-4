# Task 4.3 and 4.4 – Fairness and SSD Scheduling

## Task 4.3 – Evaluate Fairness (2 Marks)

### 1. Which Disk Scheduling Algorithms Can Cause Starvation?

Starvation occurs when a disk request waits for a very long time because other requests are continuously selected before it.

**SSTF (Shortest Seek Time First):**

SSTF can cause starvation because it always selects the nearest request. A request located far away may wait for a long time if new requests continuously arrive near the current head position.

**SCAN:**

SCAN provides better fairness because the disk head moves in both directions and services requests along its path. However, requests may wait until the head reaches their side.

**C-SCAN:**

C-SCAN provides more uniform waiting time because the head services requests in one direction only and returns to the beginning to continue servicing.

**FCFS:**

FCFS does not normally cause starvation because requests are processed in their arrival order.

### 2. Why Does C-SCAN Provide More Uniform Waiting Time Than SCAN?

SCAN moves in both directions. Requests near the middle of the disk may receive service more frequently than requests near the ends.

C-SCAN services requests in one direction only. After reaching the end, it returns to the beginning and continues in the same direction.

Therefore, C-SCAN provides more uniform waiting times for requests across the disk.

### Comparison

| Algorithm | Fairness | Starvation Possibility |
|---|---|---|
| FCFS | High | No starvation under normal operation |
| SSTF | Lower | Possible |
| SCAN | Good | Generally avoids starvation for a finite queue |
| C-SCAN | Good and more uniform | Generally avoids starvation for a finite queue |
| LOOK | Good | Generally avoids starvation for a finite queue |
| C-LOOK | Good and more uniform | Generally avoids starvation for a finite queue |

## Continuous Requests Near Cylinder 60 Under SSTF

The assignment asks us to add requests near cylinder 60 arriving every millisecond and evaluate the request at cylinder 183.

Assume the disk head is processing requests near cylinder 60 and new requests continue arriving around that position.

SSTF always selects the nearest pending request. Therefore, newly arriving requests near cylinder 60 may repeatedly be selected before the request at cylinder 183.

As a result:

- The request at cylinder 183 may wait for a long time.
- The head may continue servicing requests near cylinder 60.
- The waiting time of the request at cylinder 183 may increase.
- This demonstrates the starvation problem in SSTF.

**Conclusion:** SSTF may provide low average head movement, but it can cause starvation when requests continuously arrive near the current head position.

## Task 4.4 – Solid-State Drives (1 Mark)

### Why Does Linux Use the None or MQ-Deadline Scheduler for SSDs?

SSDs use flash memory and do not contain moving mechanical parts. Therefore, they do not require traditional disk-head movement optimisation.

**None Scheduler:**

- Sends requests to the device with minimal scheduling overhead.
- Suitable for fast SSDs that handle requests efficiently.
- Avoids unnecessary request reordering.

**MQ-Deadline Scheduler:**

- Organises requests using multiple queues.
- Uses deadlines to help prevent requests from waiting too long.
- Helps maintain predictable request processing.

### Check the Disk Scheduler in Linux

**Step 1:** Open the Linux terminal.

**Step 2:** Identify the storage device.

```bash
lsblk
```

**Step 3:** Check the scheduler for the disk. Replace `sda` with your actual disk name.

```bash
cat /sys/block/sda/queue/scheduler
```

**Example output:**

```text
[none] mq-deadline
```

The scheduler inside square brackets is the currently selected scheduler.

**Step 4:** Check the scheduler for an NVMe disk if applicable.

```bash
cat /sys/block/nvme0n1/queue/scheduler
```

### Result

The Linux disk scheduler was checked successfully using the `/sys/block/` interface. The output identifies the active scheduler for the selected storage device.

---

# Alternative Concept and Complexity Analysis – LOOK and C-LOOK

## 1. LOOK Algorithm

LOOK moves the disk head in one direction and services requests until the last request in that direction. It then reverses without travelling to the physical end of the disk.

**Given:**

- Initial head position: 53
- Request queue: 98, 183, 37, 122, 14, 124, 65, 67

**Service Order:**

53 → 37 → 14 → 65 → 67 → 98 → 122 → 124 → 183

**Total Head Movement:**

16 + 23 + 51 + 2 + 31 + 24 + 2 + 59 = 208 cylinders.

## 2. C-LOOK Algorithm

C-LOOK services requests in one direction. After reaching the last request, it jumps to the lowest pending request and continues in the same direction.

**Service Order:**

53 → 65 → 67 → 98 → 122 → 124 → 183 → 14 → 37

**Total Head Movement:**

12 + 2 + 31 + 24 + 2 + 59 + 169 + 23 = 322 cylinders.

The 169-cylinder movement from 183 to 14 is the circular jump.

## 3. Comparison of LOOK and C-LOOK with SCAN and C-SCAN

| Algorithm | Total Head Movement |
|---|---:|
| SCAN | 236 cylinders |
| C-SCAN | 382 cylinders |
| LOOK | 208 cylinders |
| C-LOOK | 322 cylinders |

LOOK requires less movement than SCAN because it reverses at the last pending request instead of reaching cylinder 0.

C-LOOK requires less movement than C-SCAN because it jumps between the last and first pending requests rather than travelling to the physical disk boundaries.

## 4. Average and Maximum Waiting Time

Waiting time depends on the order in which requests are served and the time taken for each disk movement.

For a simple comparison, assume one cylinder movement takes one time unit and requests are already waiting when scheduling begins.

| Algorithm | Average Waiting Time | Maximum Waiting Time |
|---|---|---|
| LOOK | 92.125 units | 208 units |
| C-LOOK | 152.375 units | 322 units |

These values use cumulative head movement as the service-time unit and the initial request queue as a batch. They are not real-time measurements.

## 5. Extra Work Required to Find the Last Request

The scheduler must identify the last pending request in the current direction.

**Using a Linear Search – O(n):**

- Checks each pending request.
- Finds the highest or lowest request in the selected direction.
- Requires additional scanning work.

**Using a Sorted Queue:**

- Sorts requests by cylinder number.
- Makes it easier to identify the next request and last request.
- Sorting generally takes O(n log n).
- Finding the required boundary after sorting is efficient.

## Conclusion

LOOK and C-LOOK reduce unnecessary disk-head movement by stopping at the last pending request instead of travelling to the physical disk boundary. LOOK provides 208 cylinders of movement, while C-LOOK provides 322 cylinders for the given request queue. The choice of scheduling algorithm depends on performance, fairness and waiting-time requirements.
