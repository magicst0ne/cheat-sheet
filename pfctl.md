Table:
```

pfctl -t list -T show
pfctl -t list -T delete 1.2.3.4
pfctl -t list -T add 1.2.3.4
```

NAT:
```

NAT Rules:            pfctl -vvsn
Firewall Rules:       pfctl -vvsr
Tables:               pfctl -vs Tables
State Table Contents: pfctl -vvss
Info:                 pfctl -si
Show All:             pfctl -sa
Queues:               pfctl -s queue -v
OSFP:                 pfctl -s osfp
```
