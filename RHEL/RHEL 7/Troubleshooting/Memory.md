
```
free

-m: display in megabytes
```

With no flags, free displays output in kilobytes. 

example:

```
$ free -m 
        total used free shared buffers cached 
Mem:     490   92   397    1    0        17 
-/+ buffers/cache: 74 415 
Swap: 1055 57 998
```

Total: Total amount of physical memory available to the system.
Used: Total amount of memory used by the system.
Free: Amount of memory on the system that is unused.
Shared: Shared memory available

Buffers: Typically file system metadata.
Cache: Cached memory - the contents of frequently accessed files.

# Buffers and Caches

Linux memory buffers and caches Linux will typically try to use "unused" memory for buffers and caches. This means that in order to gain efficiencies, the Linux kernel will store frequently accessed file data and filesystem metadata in the unused memory. This allows the system to utilize memory that otherwise would not have been used to enhance disk access which is often slower than system memory.

When a system is running low on unused memory, the Linux Kernel will release the buffers and cached memory, as it needs.

```
-/+ buffers/cache: 74 415 
```

First number: Used
Second: Free

Swap:

When your computer runs out of available physical memory (RAM) for running programs, the operating system can move inactive or less frequently used memory pages from RAM to the swap space on the hard drive.

The swap memory works as a temporary storage location for data that is not currently in use, freeing up space in the RAM for other active processes. When a process needs to access data that is in the swap space, the operating system will move it back to the RAM.


```
Swap: 1055 57 998
```

First: Available (1055 mb)
Second: Used (57 mb)
Third: Free (998 mb)

So, what this means is that 57mb of data was moved to swap because at some point it was low on memory.

It appears that data written to buffer is the data the kernel uses on a consistent basis.


```
grep "Out of memory" /var/log/messages
```

ps - Checking individual processes memory utilization

```
ps -eo user,pid,ppid,%mem,rss,vsize,comm | grep <pattern>
```


%mem:  The percentage of system memory that the process is using.

rss: The amount of the resident site size of the process. Amnt of memory used by the process that is not swappable.

vsize: Amount of virtual memory size: Amount of memory that the process is fully using irrespectively of whether this memory is a part of the physical or swap memory.

example output:

```
$ps -eo user,pid,ppid,%mem,rss,vsize,comm | grep lookbusy

vagrant 5383 5380 40.7 204812 212200 lookbusy
vagrant 5534 5531 34.0 170880 222440 lookbusy
```

40.7% of system memory
34.0% of system memory

These two processes combined are using:

74.7% of system memory
375mb of rss (memory used that is not swappable)
434mb of vsize (virtual memory)

You can cross reference the  memory used by these processes (375mb) with the output of `free -m` which, earlier was 490 MB. and see that these two processes are using around 76% of available memory.


`vmstat` - Monitoring memory allocation and swapping

Example:

```
$ vmstat -n 10 5 
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu----r b swpd   free  buff  cache  si   so  bi   bo   in   cs   us   sy  id  wa st 
5 0 204608 31800  0    7676   8    6   12   6    101  131  44    1  55   0 0 
1 0 192704 35816  0    2096   1887 130 4162 130  2080 2538 53    6  39   2 0 
1 0 191340 32324  0    3632   1590 57  3340 57   2097 2533 54    5  41   0 0 
4 0 191272 32260  0    5400   536  2   2150 2    1943 2366 53    4  43   0 0 
3 0 191288 34140  0    4152   392  0   679  0    1896 2366 53    3  44   0 0
```

Here, `-n 10 5` means: These options tell vmstat to only output one header line for this execution rather than a new header line for each report, run the report every 10 seconds, and limit the number of reports to 5. I

Procs:
- r: The number of processes waiting for run time.
- b: the number of process in uninterruptible sleep.


Memory:
- swpd: Amount of memory written to swap. (Virtual Memory)
- free: Amount of unused memory. (idle memory)
- buff: Amount of memory used as buffers.
- cache: Amount of memory used as cache.
- inact: Amount of inactive memory.
- active: Amount of active memory.

Swap:
- si: Amount of memory swapped in from disk
- so: Amount of memory swapped to disk.


In the output on the second report, note that 1,887 pages were swapped in and 130 pages were swapped out. 


To identify the process using the highest amount of memory, you can use:

```
ps -eo rss,vsize,user,pid,cmd | sort -nk1 | tail -n 5
```

`sort -nk1` Performs a numeric sort (-n) of the first column (-k1)


rss: amount of memory used by a process that is not swappable.
vsize: Virtual memory available





