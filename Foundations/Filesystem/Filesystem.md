In computing, file system or filesystem (often abbreviated to fs) is a method and data structure that the operating system uses to control how data is stored and retrieved.

Without a file system, data placed in a storage medium would be one large body of data with no way to tell where one piece of data stopped and the next began, or where any piece of data was located when it was time to retrieve it.

By separating the data into pieces and giving each piece a name, the data is easily isolated and identified

A filesystem typically has layers:

1.  Application layer: This is the layer where user applications interface with the filesystem. The application layer sends requests to the kernel for file operations such as reading, writing, creating, or deleting files.
    
2.  Filesystem layer: This is the layer that implements the filesystem-specific operations such as block allocation, directory management, file system journaling, and permissions. It also provides an abstraction layer between the kernel and the hardware.
    
3.  Block layer: This layer handles low-level disk I/O operations and deals with disk sectors and disk blocks. It provides a buffer cache to optimize disk I/O operations and manages the allocation of blocks to files.
    
4.  Device layer: This layer handles the interaction between the filesystem and the underlying storage device, which can be a hard disk, solid-state drive, or other storage media. It provides a device driver to communicate with the storage device and handles block-level I/O requests.
    
5.  Physical layer: This is the layer that deals with the actual physical storage medium, such as the hard disk platters, read/write heads, and the electronic circuits that control them.



-   /bin: Contains essential system binaries (executable files) that are required for booting the system and for normal system operation.
    
-   /sbin: Contains system binaries that are used for system administration tasks, such as disk partitioning and system startup.
    
-   /etc: Contains system configuration files that are used by various applications and services.
    
-   /usr: Contains user applications and libraries, such as web browsers, text editors, and development tools.
    
-   /var: Contains variable files, such as log files and temporary files.
    
-   /home: Contains the home directories for user accounts.
    
-   /root: The home directory for the root user.
    
-   /tmp: Contains temporary files that are created by applications and services.

Linux supports a wide range of filesystems, including popular ones such as ext4, XFS, and Btrfs, as well as network filesystems like NFS and SMB.

Popular Filesystems:

Ext4: Journaled, backwards compatible, stabled.

XFS: Specializes in performance and large data files formats quickly, has snapshotting features.

BTRFS: Modern filesystem. Allows volume management functionality.

ZFS (Zettabyte File System): is a combined file system and logical volume manager developed by Sun Microsystems (now owned by Oracle).

FAT, vFAT: Supported by almost all operating systems. Good for universal exchange between computers and devices of any type and age. vFAT is an optional extension for long filenames. Volumes using VFAT can also be read by operating systems not supporting VFAT extensions.