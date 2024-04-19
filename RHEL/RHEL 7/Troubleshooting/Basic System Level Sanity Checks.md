
```
lscpu
lsmem
lsblk
ip a
```

Check for virtual or physical hardware, driver, or kernel internal issues (like filesystem or storage errors)

```
dmesg -T
```

Check top to make sure no unexpected processes are running or eating all CPU and there is no notable IO wait. High IO wait may indicate storage issues.

```
top
```

Check the recent messages in system logs to see if anything unusual has been reported recently. There might also be information about crashed processes which would indicate application level issues.

```
journalctl -l -b | less
less /var/log/messages
less /var/log/secure
```

When using SELinux in Enforcing mode (as it [should](https://stopdisablingselinux.com/) be) it is worth checking for possible SELinux denials with interpretations:

```
ausearch -m AVC -i 
```

Additional SELinux related information can be found with the commands below:

```
grep denied /var/log/audit/audit.log
ausearch -i --input /var/log/audit/audit.log
```

Query all packages installed:

```
rpm -qa
```

Print a process by process ID:

```
ps -p <pid>
```

Check existing established network connections

```
netstat -na

-a: all
-n: numeric instead of DNS host names
```


iotop - top-like I/O monitor

```
iotop
```

iostat - Report I/O and CPU statistics

```
iostat
```


```
ps --forest -eo user,pid,ppid,%cpu,cmd

This command prints parent and child processes in a tree format.

-e: everything
-o: specifies you want the output in a specific format.
```
