

First investigate if there has been any recent changes or updates to the installed software:

```
rpm -qa --last | less
tail /var/log/dnf.log
tail /var/log/yum.log
```

Then investigate the application configuration (and make sure what is currently configured in the configuration files is actually in use by the running application process).

To see all the files changed since installation (from RPMs) use:

```
rpm -Va
```

This will check all files from all packages and can take a while. The results will highlight what kind of customizations have been made to a particular system.