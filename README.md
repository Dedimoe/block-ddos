# block-ddos
Block DDoS

```
iptables -A INPUT -p tcp --dport 80 -m limit --limit 20/minute --limit-burst 100 -j ACCEPT
```
20 minutes is just a standard to maintain.

