# Q1 – File-System Design Review

## Task 1.1 – Evaluate the Proposed File Organisation

### Problem Context

A college proposes to store every student's files on a shared server. The proposed system has the following arrangements:

- One flat directory for all 12,000 students.
- Files are named only by the student's choice.
- Contiguous allocation is used for every file.
- No access control is provided because students are expected not to access one another's files.

This design may appear simple to implement, but it creates several problems related to file organisation, performance, storage management, security and sharing.

### Weaknesses of the Proposed Design

**Name Clashes in a Single Directory**

When 12,000 students use one common directory, different students may create files with the same name. For example, many students may save their assignments as `Assignment.docx`.

This creates naming conflicts and makes it difficult to identify the correct file. A unique naming system or separate student directories are required.

**Searching for Files Among 12,000 Students**

Keeping all files in one directory makes file management difficult. Searching for a particular student's file requires identifying the correct file among a large number of entries.

As the number of students and files increases, directory management becomes more complicated. Organising files into separate student directories makes searching and administration easier.

**File Growth Under Contiguous Allocation**

Contiguous allocation stores a file in consecutive disk blocks. It provides efficient sequential and direct access, but it creates problems when a file grows.

For example, if a file occupies blocks 10 to 19 and needs additional space, the following blocks may already belong to another file. The operating system may need to move the file to a larger continuous free area.

This can cause external fragmentation and make storage allocation difficult.

**Protection and Privacy**

The proposed system does not provide access control. Therefore, one student may be able to read, modify or delete another student's files.

Student assignments, personal documents and academic records must be protected. File permissions and Access Control Lists (ACLs) are required to control who can read, write or execute files.

**Backup and Recovery**

A single shared directory containing files from all students makes backup management difficult. If files are accidentally deleted, corrupted or damaged due to a system failure, important student information may be lost.

The system should support regular backups, recovery procedures and separate backup policies for student and shared project files.

**Sharing Files for Group Projects**

Students working on group projects need to share selected files with their team members. The proposed system does not provide a proper method for controlled sharing.

Giving access to the entire shared directory is unsafe. Instead, separate project directories should be created with permissions granted only to authorised group members.

### Summary of Identified Weaknesses

| Problem | Effect on the System | Suggested Improvement |
|---|---|---|
| Name clashes | Different students may create files with identical names. | Use separate student directories and unique identifiers. |
| Large flat directory | File searching and management become difficult. | Use a hierarchical directory structure. |
| Contiguous allocation | File growth becomes difficult and causes external fragmentation. | Use indexed or extent-based allocation. |
| No access control | Students may access or modify other students' files. | Apply permissions and ACLs. |
| Backup difficulties | Recovery and management of student files become complicated. | Maintain regular and separate backups. |
| File sharing problems | Group members cannot securely access selected files. | Create shared project directories with controlled permissions. |

### Overall Evaluation

The proposed file organisation is not suitable for a college server containing files for 12,000 students. A single flat directory, unrestricted access and compulsory contiguous allocation create problems with file searching, privacy, storage growth and sharing.

A hierarchical directory structure, suitable file allocation method, access permissions, backup facilities and controlled project sharing would provide a more organised and secure file-storage system.

### Conclusion

The proposed system should be improved before implementation. Each student should have an individual directory, while group projects should use separate shared directories. Access permissions and regular backups should be introduced to protect student data. A suitable file allocation method should also be selected to support file growth and efficient storage utilisation.
