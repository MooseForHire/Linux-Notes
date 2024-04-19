
The `nftables` framework provides packet classification facilities and it is the designated successor to the `iptables`, `ip6tables`, `arptables`, `ebtables`, and `ipset` tools.

Similarly to `iptables`, `nftables` use tables for storing chains. The chains contain individual rules for performing actions.



## When to use firewalld or nftables

- `firewalld`: Use the `firewalld` utility for simple `firewall` use cases. The utility is easy to use and covers the typical use cases for these scenarios.
    
- `nftables`: Use the `nftables` utility to set up complex and performance critical firewalls, such as for a whole network.

### Displaying the nftables rule set

The rule set of `nftables` contains tables, chains, and rules. This section explains how to display this rule set.

To display all the rule set, enter:

```
 # nft list ruleset
table inet example_table {
  chain example_chain {
    type filter hook input priority filter; policy accept;
    tcp dport http accept
    tcp dport ssh accept
  }
}
```

