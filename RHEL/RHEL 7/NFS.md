RHEL 7 supports NFSv3 and NFSv4


NFS relies on Remote Procedure Calls (RPC) between clients and servers. RPC services are controlled by the rpcbind service. The rpcbind service replaces portmap, which was used in previous versions of Linux to map RPC program numbers to IP address port number combinations.

```
systemctl status rpc bind
systemctl status nfs
```

```
df -hT
```

Optimizing NFS Performance:

On a client, one of the most important optimization settings are the NFS data transfer buffer sizes, specified by the **mount** command options rsize and wsize.

These specify the size of the chunks of data that the client and server pass back and forth to each other. If no rsize and wsize are specified, the default varies: The most common default is 4K (4096 Bytes).

On Linux, the max block size is defined by the value of the kernel constant NFSSVC_MAXBLKSIZE, found in ./include/linux/nfsd/const.h.

I think this value is 32K.

`nfstat` can be used to look at nfs transactions. The -o option will show you the number of dropped packets.