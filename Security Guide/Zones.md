

To see which zones are available on your system:

```
~]# firewall-cmd --get-zones
```

The `firewall-cmd --get-zones` command displays all zones that are available on the system, but it does not show any details for particular zones.

To see detailed information for all zones:

```
~]# firewall-cmd --list-all-zones
```

To see detailed information for a specific zone:

```
~]# firewall-cmd --zone=_zone-name_ --list-all
```

