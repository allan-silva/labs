# NAT Router - Entrypoint for internal VMs subnets

All communications with labs VMs mus be established via this router. Except by the SSH port forwarded for ansible use.

## Host configuration

```
sudo ip route add 192.168.60.0/24 via 192.168.56.4
sudo ip route add 192.168.61.0/24 via 192.168.56.4
sudo ip route add 192.168.62.0/24 via 192.168.56.4
```

Where  `192.168.56.4` is host-only virtualbox adapter.
