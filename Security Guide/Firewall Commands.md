
### Viewing the Current Status of `firewalld`

The firewall service, `firewalld`, is installed on the system by default. Use the `firewalld` CLI interface to check that the service is running.

To see the status of the service:

```
~]# firewall-cmd --state
```

To list all the relevant information for the default zone:

```
~]# firewall-cmd --list-all
```

To list for a specific zone:
```
firewall-cmd --list-all --zone=home
```


