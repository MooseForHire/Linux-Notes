
Ping the NFS server.

Example:

```
mount | grep "data"

192.168.33.13:/nfs on /data type nfs4 (rw,relatime,vers=4.0,rsize=65536,wsize=65536,namlen=255,hard,proto=tcp,port=0,timeo=600,retrans=2,sec=sys,clientaddr=192.168.33.12,local_lock=none,addr=192.168 .33.13)

```

rw = mounted with read/write privileges'.

IP address is the NFS server.


`/etc/services` file is a static file that is used to map network ports to a simple name.

can also `netstat -na | grep <host name>`



```
showmount -e <host name or ip address>
```

Can be used to display the directories being exported via the -e flag.