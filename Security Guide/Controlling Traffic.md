
In an emergency situation, such as a system attack, it is possible to disable all network traffic and cut off the attacker.

To immediately disable networking traffic, switch panic mode on:

```
~]# firewall-cmd --panic-on
```

Switching off panic mode reverts the firewall to its permanent settings. To switch panic mode off:

```
~]# firewall-cmd --panic-off
```

To see whether panic mode is switched on or off, use:

```
~]# firewall-cmd --query-panic
```

### Controlling Ports using CLI

Ports are logical devices that enable an operating system to receive and distinguish network traffic and forward it accordingly to system services. These are usually represented by a daemon that listens on the port, that is it waits for any traffic coming to this port.

Normally, system services listen on standard ports that are reserved for them. The `httpd` daemon, for example, listens on port 80. However, system administrators by default configure daemons to listen on different ports to enhance security or for other reasons.

#### Opening a Port

Through open ports, the system is accessible from the outside, which represents a security risk. Generally, keep ports closed and only open them if they are required for certain services.

To get a list of open ports in the current zone:

1. List all allowed ports:
    
    ~]# `firewall-cmd --list-ports`
    
2. Add a port to the allowed ports to open it for incoming traffic:
    
    ~]# `firewall-cmd --add-port=port-number/port-type`
    
3. Make the new settings persistent:
    
    ~]# `firewall-cmd --runtime-to-permanent`

The port types are either `tcp`, `udp`, `sctp`, or `dccp`. The type must match the type of network communication.



