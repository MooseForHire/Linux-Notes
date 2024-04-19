
# What is a Kernel Module?

Involvement in the development of Linux kernel modules requires a foundation in the C programming language and a track record of creating conventional programs intended for process execution.

A Linux kernel module is precisely defined as:

**A code segment capable of dynamic loading and unloading within the kernel as needed. These modules enhance kernel capabilities without necessitating a system reboot.** 

For example, one type of module is the device driver, which allows the kernel to access hardware connected to the system.


## How do modules get into the Kernel?


You can see what modules are already loaded into the kernel by running **lsmod**, which gets its information by reading the file /proc/modules.

When the kernel needs a feature that is not resident in the kernel, the kernel module daemon kmod[[1 General Info]](https://linux.die.net/lkmpg/x44.html#FTN.AEN62) execs modprobe to load the module in



