# Network

## iptables
Log package in specific port of the host:
```bash
sudo iptables -I INPUT -p tcp --dport 15672 --syn -j LOG --log-prefix "HTTPS SYN: "
```

Delete the package logging entry:
```bash
sudo iptables -D INPUT <NUMBER>
```

List the iptables INPUT:
```bash
sudo iptables -L INPUT --line-numbers
```

Tail the logs:
```bash
dmesg | grep "HTTPS SYN: "
journalctl -k | grep "HTTPS SYN: "
```

## Firewalld

