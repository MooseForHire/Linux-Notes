Mounting a filesystem is the process of making the files and directories on a storage device (such as a hard drive or USB drive) accessible to the operating system and its users.

When a storage device is mounted, the operating system creates a link between the device and a directory in the file system, called a mount point. The files and directories on the storage device then become accessible through this mount point in the file system hierarchy.

Linux systems look at a file called `/etc/fstab`  (filesystem table) to determine which filesystems to mount during the boot process. Filesystems that do not have an entry in this file will not be automatically mounted

