1.  Power-on Self-Test (POST): When you turn on your computer, the firmware (BIOS or UEFI) performs a series of self-tests to ensure that the hardware is functioning correctly.
    
2.  Boot Loader: Once the hardware is initialized, the firmware loads the boot loader. The boot loader is responsible for loading the Linux kernel into memory and starting the initial RAM disk (initrd).
    
3.  Kernel Initialization: The kernel initializes various components of the system, such as the processor, memory, and hardware devices. It also loads device drivers and mounts the root file system.
    
4.  Init Process: Once the kernel has initialized, it starts the init process, which is the first user space process. The init process is responsible for initializing the rest of the system services and processes.
    
5.  Run Levels: The system can be booted into different run levels, which determine which services and processes are started. For example, run level 3 starts the system in multi-user mode with a command line interface, while run level 5 starts the system in graphical mode.
    
6.  System Services: Once the appropriate run level is selected, the init process starts various system services, such as the network, logging, and security services.
    
7.  Login Screen: Finally, the system displays a login screen, where the user can log in and start using the system.


** You can change the boot process/run level by modifying:

`/etc/inittab`

well in this case our 'bootloader' is ipxe
so normally on linux systems this would be a kernel image, an initrd ("initial ramdisk.. think drivers and things"), and the root filesystem image to mount

so on a normal booting system off disk the root filesystem would be an actual partition on disk... but in this case it will be a disk image that gets mounted into a ramdisk

and all these things are actually URLS


to images that we have in our object storage bucket... (which we download from the internet)