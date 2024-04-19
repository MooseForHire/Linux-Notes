

# Definition

The _control groups_, abbreviated as _cgroups_ in this guide, are a Linux kernel feature that allows you to allocate resources — such as CPU time, system memory, network bandwidth, or combinations of these resources — among hierarchically ordered groups of processes running on a system.


# How to Define Your own cgroup

You define the hierarchy (control groups tree) by providing structure to `cgroups` virtual file system, mounted by default on the `/sys/fs/cgroup/` directory.

Manually, you can manage the hierarchies of `cgroups` by creating and removing sub-directories in the `/sys/fs/cgroup/` directory.

The resource controllers in the kernel then modify the behavior of processes in `cgroups` by limiting, prioritizing or allocating system resources, of those processes.


```
cd /sys/fs/cgroup/<resource controller>/myapp

```


# Resource controller

Kernel resource controllers enable the functionality of control groups.

A resource controller, also called a control group subsystem, is a kernel subsystem that represents a single resource, such as CPU time, memory, network bandwidth or disk I/O.

The Linux kernel provides a range of resource controllers that are mounted automatically by the `systemd` service manager. You can find a list of the currently mounted resource controllers in the `/proc/cgroups` file.