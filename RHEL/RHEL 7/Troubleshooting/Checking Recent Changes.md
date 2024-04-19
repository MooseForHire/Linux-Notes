
Sometimes it is useful to see if someone has recently logged into to a system and review possible changes by them. To see users recently logged into the system and the commands they have run:

```
last -F
less ~USERNAME/.bash_history
journalctl -r _UID=UID
```

