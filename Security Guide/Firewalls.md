
A _firewall_ is a way to protect machines from any unwanted traffic from outside. It enables users to control incoming network traffic on host machines by defining a set of _firewall rules_. These rules are used to sort the incoming traffic and either block it or allow through.


`firewalld` is a firewall service daemon that provides a dynamic customizable host-based firewall with a `D-Bus` interface. Being dynamic, it enables creating, changing, and deleting the rules without the necessity to restart the firewall daemon each time the rules are changed.

`firewalld` uses the concepts of _zones_ and _services_, that simplify the traffic management.

## Firewall Zones: 

Predefined sets of rules. Network interfaces and sources can be assigned to a zone.

The traffic allowed depends on the network your computer is connected to and the security level this network is assigned

## Firewall Services:

Predefined rules that cover all necessary settings to allow incoming traffic for a specific service and they apply within a zone.

Services use one or more _ports_ or _addresses_ for network communication. Firewalls filter communication based on ports.

To allow network traffic for a service, its ports must be _open_. `firewalld` blocks all traffic on ports that are not explicitly set as open. Some zones, such as _trusted_, allow all traffic by default.

![[Pasted image 20230906155334.png]]

Restarting `firewalld` closes all open ports and stops the networking traffic.


