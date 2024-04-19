

**inode** is a "database" of all file information that tells about file structure. The inode of each file uses a pointer(inode number) to point to the specific file, directory or object.

![[Pasted image 20230918124411.png]]


When an application needs a file, the application exchanges the file name for the inode number from the directory listing. After that, the application uses the inode number for a reference to the file.



