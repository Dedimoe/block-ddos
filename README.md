# block-ddos

#### 1. Block: DDoS

```
iptables -A INPUT -p tcp --dport 80 -m limit --limit 20/minute --limit-burst 100 -j ACCEPT
```
20 minutes is just a standard to maintain.


#### 2. Block: Port Scanning
```
sudo iptables -N block-scan
sudo iptables -A block-scan -p tcp —tcp-flags SYN,ACK,FIN,RST RST -m limit —limit 1/s -j RETURN
sudo iptables -A block-scan -j DROP
```


#### 3. Block: Bad Ports
```
badport="135,136,137,138,139,445"
sudo iptables -A INPUT -p tcp -m multiport --dport $badport -j DROP
sudo iptables -A INPUT -p udp -m multiport --dport $badport -j DROP
```
You can add more ports according to your needs.

To view the list of iptables:
```
sudo iptables-save
```

