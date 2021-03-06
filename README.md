# Recoverable-Virtual-Memory

## Introduction
The goal of this project is to realize lightweight recoverable virtual memory.

The mechanism can be briefly concluded as follows. Each segment is associated with a log file. Before users write to external data segments, they first write to log files. The next time they map from external data segments to in-memory segments, log files will be truncated and any new updates will be reflected on external data segments. The data in external data segments will be brought into memory segments. In case a crash happens, memory can be recovered to the last committed state using committed log entries in log files and data in external data segments.

## Functions

### rvm_init()
Create backing directory.

### rvm_map()
Map external data segment into memory. This mapping is a one-to-one mapping.

### rvm_unmap()
Unmap in-memory segment from external data segment.

### rvm_destroy()
Destroy external data segment.

### rvm_begin_trans()
Mark the segments that will be modified by the new transaction and return its transaction ID.

### rvm_about_to_modify()
Declare that the library is about to modify a specified region of memory in the specified segment.

### rvm_commit_trans()
Commit all changes that have been made within the specified transaction into logs.

### rvm_abort_trans()
Undo all changes that have happened within the specified transaction.

### rvm_truncate_log()
Apply changes recorded in logs onto external data segments and erase contents of logs.

### rvm_verbose()
Print information about what the library is doing when verbose output is enabled.

## Contributions of Each Team Member
Zeyu Chen: Design appropriate data structures. Implement initialization and mapping operations of RVM library. Also implement library output operation of RVM library. Design 1 additional test case.

Yaohong Wu: Design appropriate data structures. Implement transactional operations of RVM library. Design 2 additional test cases.

## Release
See release repo to see the released version.

