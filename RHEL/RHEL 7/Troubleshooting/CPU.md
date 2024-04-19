
```
top
```

us - User CPU %. This is the % of CPU being consumed by the processes in the user mode. In user mode, applications are required to use system calls (API's) to perform priveleged executions.

sy - System CPU %. The number is the percentage of CPU being consumed by kernel mode execution. Normally reserved for trust OS processes.

id - Idle: Percentage of CPU time being spent idle. (Amount of COU time spent not being utilized)

wa - Wait: The number is the percentage of CPU time spent waiting. Typically high when many processes are waiting for I/O devices.

st - Stolen: This number specifically applies to Linux systems running as a virtual machine. This number is the percentage of CPU time stolen from this machine by the host. This number is usually present when the host machine itself is running into CPU contention


Top section - Prints the scale based on the systems as a whole.
Processes section - CPU scale is for one CPU.

`cat /proc/cpuinfo`  Shows CPU info
`lscpu`

```
ps -lf

-l: Long listing
-f: full format
```


pri: The higher the priority number, the lower priority the process has with the system scheduler.

The below command will compare two processes in the format you specify with the -o flag.

```
ps -o state,user,pid,ppid,%cpu,cmd -p 3000,3001
```

In order to identify all processes associated with a running process, we can run:

```
ps --forest -eo state,user,pid,ppid,%cpu,cmd

Here, the -e flag will display all users running processes
```



Process states:


Uninterruptible sleep (D): Processes generally in a sleep state when waiting for I/O Running or Runnable (R): Processes on the run queue 
Interruptible sleep (S): Processes waiting for an event to complete but not blocking CPU or I/O 
Stopped (T): Processes that are stopped by a job control system 
Paging (P): Processes that are current paging; 
Dead (X): Processes that are dead, this should never be seen, as dead processes should not show up when running ps
Defunct (Z): Zombie processes that are terminated but left in an undead state

