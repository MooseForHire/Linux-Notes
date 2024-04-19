In modern computing, the idea of a _central_ processing unit is a misleading one, as most modern systems have multiple processors. How these processors are connected to each other and to other system resources — the _topology_ of the system — can greatly affect system and application performance, and the tuning considerations for a system.

There are two primary types of topology used in modern computing:

### Symmetric Multi-Processor (SMP) topology

SMP topology allows all processors to access memory in the same amount of time. However, because shared and equal memory access inherently forces serialized memory accesses from all the CPUs, SMP system scaling constraints are now generally viewed as unacceptable. For this reason, practically all modern server systems are NUMA machines.

### Non-Uniform Memory Access (NUMA) topology

NUMA topology was developed more recently than SMP topology. In a NUMA system, multiple processors are physically grouped on a socket. Each socket has a dedicated area of memory, and processors that have local access to that memory are referred to collectively as a node.

Processors on the same node have high speed access to that node's memory bank, and slower access to memory banks not on their node. Therefore, there is a performance penalty to accessing non-local memory.

Example:


![[Pasted image 20230905143211.png]]


Given this performance penalty, performance sensitive applications on a system with NUMA topology should access memory that is on the same node as the processor executing the application, and should avoid accessing remote memory wherever possible.

When tuning application performance on a system with NUMA topology, it is therefore important to consider where the application is being executed, and which memory bank is closest to the point of execution.


In a system with NUMA topology, the `/sys` file system contains information about how processors, memory, and peripheral devices are connected. 

The `/sys/devices/system/cpu` directory contains details about how processors in the system are connected to each other. 

The `/sys/devices/system/node` directory contains information about NUMA nodes in the system, and the relative distances between those nodes.

The `numactl --hardware` command gives an overview of your system's topology.

The `lscpu` command, provided by the util-linux package, gathers information about the CPU architecture, such as the number of CPUs, threads, cores, sockets, and NUMA nodes.

The `lstopo` command, provided by the hwloc package, creates a graphical representation of your system.











