
The `Internet Control Message Protocol` (`ICMP`) is a supporting protocol that is used by various network devices to send error messages and operational information indicating a connection problem, for example, that a requested service is not available. `ICMP` differs from transport protocols such as TCP and UDP because it is not used to exchange data between systems.


Unfortunately, it is possible to use the `ICMP` messages, especially `echo-request` and `echo-reply`, to reveal information about your network and misuse such information for various kinds of fraudulent activities. Therefore, `firewalld` enables blocking the `ICMP` requests to protect your network information.


