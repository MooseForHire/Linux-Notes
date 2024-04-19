
```
iostat - CPU and device I/O statistics

-x: Extended statistics flag
```

Used for troubleshooting disk performance issues.

- %iowait - Shows percentage of the the time that the CPU or CPUs were idle during which the system had an outstanding disk I/O request.

- %util - Tells us how much time did the storage device have outstanding work (how long was it busy)

- await: Tells us how fast requests go through. (Average)


If a device starts with `dm` , this is an indication that the device is a logical device created by the device mapper.

The Device Mapper is a Linux kernel framework that allows the system to create virtual disk devices that "map" back to physical devices.

```
iotop - used to identify which processes are utilizing I/O the most. Bandwidth.
```

