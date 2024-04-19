

Separate PKI instances
run as a single Java-based Apache Tomcat instance,
contain a single PKI subsystem (CA, KRA, OCSP, TKS, or TPS), and
must utilize unique ports if co-located on the same physical machine or virtual machine (VM).


Shared PKI instances
run as a single Java-based Apache Tomcat instance,
can contain a single PKI subsystem that is identical to a separate PKI instance,
can contain any combination of up to one of each type of PKI subsystem:
CA
TKS
CA, KRA
CA, OCSP
TKS, TPS
CA, KRA, TKS, TPS
CA, KRA, OCSP, TKS, TPS
and so on.

allow all of their subsystems contained within that instance to share the same ports, and
must utilize unique ports if more than one is co-located on the same physical machine or VM.

systemctl start pki-tomcatd starts a PKI instance.

A pki instance runs as a single Java-based Apache Tomcat instance. It contains a single PKI Subsystem - CA.



======================================================================

The /var/lib/dirsrv/slapd-instance_name/ directory contains the database, as well as the backup and export directory. The /etc/dirsrv/slapd-instance_name/ directory contains the instance configuration and the network security services (NSS) database. Before you remove an instance, backup this data.


Directory Server stores the configuration from the cn=config entry in the /etc/dirsrv/slapd-instance_name/dse.ldif file. The server stores only parameters you modified in this file. Attributes that are not listed, use their default value.

DS uses port 389 for LDAP, 636 for LDAPS

dsconf -D "cn=Directory Manager" ldap://server.example.com config get nsslapd-port nsslapd-secureport

dsconf -D "cn=Directory Manager" ldap://server.example.com backend suffix list

