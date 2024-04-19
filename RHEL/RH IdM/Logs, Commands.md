
Logs:

```

CLIENT SIDE:

# SSSD
/var/log/sssd/sssd.conf   #  sssd Configuration
/var/log/sssd/sssd_example.com.log    # debug messages


# SSH

/etc/ssh/ssh_config

# Kerberos (KDC)

/var/log/krb5kdc.log

----------------------------------------------------------------------------
IdM SIDE

Web UI:

/var/log/httpd/access_log        
/var/log/httpd/error_log         


Certificates:

/var/log/pki-ca/debug
/var/log/pki-ca/system
/var/log/pki-ca/transactions
/var/log/pki-ca/signedAudit

Directory Server:

/var/log/dirsrv/slapd-REALM/access
/var/log/dirsrv/slapd-REALM/audit
/var/log/dirsrv/slapd-REALM/errors

Kerberos:

/var/log/krb5libs.log     --- Kerberos Connections
/var/log/krb5kdc.log      --- Primary Log File
```


Commands:

```
service sssd restart
```