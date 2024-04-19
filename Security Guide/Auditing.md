
## Audit System Architecture

The Audit system consists of two main parts: the user-space applications and utilities, and the kernel-side system call processing. The kernel component receives system calls from user-space applications and filters them through one of the following filters: _user_, _task_, _fstype_, or _exit_.

# Understanding Audit Log Files

By default, the Audit system stores log entries in the `/var/log/audit/audit.log` file; if log rotation is enabled, rotated `audit.log` files are stored in the same directory.

The following Audit rule logs every attempt to read or modify the `/etc/ssh/sshd_config` file:

```
-w /etc/ssh/sshd_config -p warx -k sshd_config
```

# Searching the Audit Log Files

The **ausearch** utility allows you to search Audit log files for specific events. By default, **ausearch** searches the `/var/log/audit/audit.log` file. 

To search the `/var/log/audit/audit.log` file for failed login attempts, use the following command:

```
~]# ausearch --message USER_LOGIN --success no --interpret
```

To search for all logged actions performed by a certain user, using the user's login ID (`auid`), use the following command:

```
~]# ausearch -ua 1000 -i
```

