### Implementation checklist

- [x]  mkdir
- [x] rmdir
- [x] readdir
- [x] mknod
- [x] unlik
- [x] read
- [x] write
- [x] open
- [x] truncate
- [x] save filesystem to disc
### Requirements for Functionality

Your file system should implement the following parts of a file system using appropriate APIs from FUSE.

- [x] **Directories:** List, create, and delete files. Create and delete directories. You can omit rename and link. You are as mentioned above allowed to restrict the length of filenames.
    
- [x] **Files:** Open, close. Sequential read/write of streams of bytes.
    
- [x] **Inodes:** Size, access and modification time stamps. You can omit owner, permissions, reference count, etc.
    
- [x] **Persistance:** Once the filesystem is mounted, you should restore a previous version (if one exists), and unmounting should save to disk.
    

Remember to document your choices in the report.