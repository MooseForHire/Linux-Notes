
Check requirements for the application.

For example, if an application requires Apache or Nginx, we can first validate that the web server is running and installed:

```
rpm -qa | grep -i apache
```

Recall that the default port for HTTP requests is port 80.

```
netstat -nap | grep 80
```

This will show us processes are using port 80.

We can also verify services listed in the netstat output by checking the pid:

```
ps -elf | grep <PID>
```



