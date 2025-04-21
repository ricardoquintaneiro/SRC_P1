# Configurações das Firewalls

## FW-Stateless-1

```
configure
set protocols static route 0.0.0.0/0 next-hop 100.0.0.1
set protocols static route 0.0.0.0/0 next-hop 100.0.0.9
set interfaces ethernet eth0 address 100.0.0.129/26
set interfaces ethernet eth1 address 100.0.0.2/30
set interfaces ethernet eth2 address 100.0.0.10/30
set firewall name EDGE-IN default-action drop
set firewall name EDGE-IN rule 1 action drop
set firewall name EDGE-IN rule 1 state invalid enable
set firewall name EDGE-IN rule 3 action accept
set firewall name EDGE-IN rule 3 protocol tcp_udp
set firewall name EDGE-IN rule 3 destination port 443
set firewall name EDGE-IN rule 4 action accept
set firewall name EDGE-IN rule 4 protocol tcp
set firewall name EDGE-IN rule 4 destination port 1025
set firewall name EDGE-IN rule 5 action accept
set firewall name EDGE-IN rule 5 protocol tcp
set firewall name EDGE-IN rule 5 destination port 1993
set firewall name EDGE-IN rule 6 action accept
set firewall name EDGE-IN rule 6 protocol udp
set firewall name EDGE-IN rule 6 destination port 1053
set firewall name EDGE-IN rule 7 action accept
set firewall name EDGE-IN rule 7 protocol tcp_udp
set firewall name EDGE-IN rule 7 source port 80,443
set interfaces ethernet eth0 firewall in name EDGE-IN
commit
save
```

## FW-Stateless-2

```
configure
set protocols static route 0.0.0.0/0 next-hop 100.0.0.5
set protocols static route 0.0.0.0/0 next-hop 100.0.0.13
set interfaces ethernet eth0 address 100.0.0.193/26
set interfaces ethernet eth1 address 100.0.0.6/30
set interfaces ethernet eth2 address 100.0.0.14/30
set firewall name EDGE-IN default-action drop
set firewall name EDGE-IN rule 1 action drop
set firewall name EDGE-IN rule 1 state invalid enable
set firewall name EDGE-IN rule 3 action accept
set firewall name EDGE-IN rule 3 protocol tcp_udp
set firewall name EDGE-IN rule 3 destination port 443
set firewall name EDGE-IN rule 4 action accept
set firewall name EDGE-IN rule 4 protocol tcp
set firewall name EDGE-IN rule 4 destination port 1025
set firewall name EDGE-IN rule 5 action accept
set firewall name EDGE-IN rule 5 protocol tcp
set firewall name EDGE-IN rule 5 destination port 1993
set firewall name EDGE-IN rule 6 action accept
set firewall name EDGE-IN rule 6 protocol udp
set firewall name EDGE-IN rule 6 destination port 1053
set firewall name EDGE-IN rule 7 action accept
set firewall name EDGE-IN rule 7 protocol tcp_udp
set firewall name EDGE-IN rule 7 source port 80,443
set interfaces ethernet eth0 firewall in name EDGE-IN
commit
save
```

## FW-1

```
configure
set interfaces ethernet eth0 address 10.0.3.101/24
set interfaces ethernet eth1 address 10.0.5.101/24
set interfaces ethernet eth2 address 10.0.7.101/24
set protocols ospf area 0 network 10.0.3.0/24
set protocols ospf area 0 network 10.0.5.0/24
set protocols ospf area 0 network 10.0.7.0/24
set zone-policy zone OUTSIDE description "Outside/Internet"
set zone-policy zone OUTSIDE interface eth0
set zone-policy zone DMZ description "DMZ"
set zone-policy zone DMZ interface eth1
set zone-policy zone CORE description "Core"
set zone-policy zone CORE interface eth2
set firewall name FROM-DMZ-TO-OUTSIDE rule 1 description "Accept Internet from DMZ on port 80"
set firewall name FROM-DMZ-TO-OUTSIDE rule 1 action accept
set firewall name FROM-DMZ-TO-OUTSIDE rule 1 protocol tcp_udp
set firewall name FROM-DMZ-TO-OUTSIDE rule 1 destination port 80
set firewall name FROM-DMZ-TO-OUTSIDE rule 2 description "Accept Internet from DMZ on port 443"
set firewall name FROM-DMZ-TO-OUTSIDE rule 2 action accept
set firewall name FROM-DMZ-TO-OUTSIDE rule 2 protocol tcp_udp
set firewall name FROM-DMZ-TO-OUTSIDE rule 2 destination port 443
set firewall name FROM-DMZ-TO-OUTSIDE rule 3 description "Accept Established-Related Connections to Outside"
set firewall name FROM-DMZ-TO-OUTSIDE rule 3 action accept
set firewall name FROM-DMZ-TO-OUTSIDE rule 3 state established enable
set firewall name FROM-DMZ-TO-OUTSIDE rule 3 state related enable
set zone-policy zone OUTSIDE from DMZ firewall name FROM-DMZ-TO-OUTSIDE
set firewall name FROM-OUTSIDE-TO-DMZ rule 1 description "Accept TCP/UDP to DMZ on port 443"
set firewall name FROM-OUTSIDE-TO-DMZ rule 1 action accept
set firewall name FROM-OUTSIDE-TO-DMZ rule 1 protocol tcp_udp
set firewall name FROM-OUTSIDE-TO-DMZ rule 1 destination port 443
set firewall name FROM-OUTSIDE-TO-DMZ rule 2 description "Accept IMAP (TCP) from DMZ on port 1993"
set firewall name FROM-OUTSIDE-TO-DMZ rule 2 action accept
set firewall name FROM-OUTSIDE-TO-DMZ rule 2 protocol tcp
set firewall name FROM-OUTSIDE-TO-DMZ rule 2 destination port 1993
set firewall name FROM-OUTSIDE-TO-DMZ rule 3 description "Accept SMTP (TCP) from DMZ on port 1025"
set firewall name FROM-OUTSIDE-TO-DMZ rule 3 action accept
set firewall name FROM-OUTSIDE-TO-DMZ rule 3 protocol tcp
set firewall name FROM-OUTSIDE-TO-DMZ rule 3 destination port 1025
set firewall name FROM-OUTSIDE-TO-DMZ rule 4 description "Accept DNS (UDP) from DMZ on port 1053"
set firewall name FROM-OUTSIDE-TO-DMZ rule 4 action accept
set firewall name FROM-OUTSIDE-TO-DMZ rule 4 protocol udp
set firewall name FROM-OUTSIDE-TO-DMZ rule 4 destination port 1053
set firewall name FROM-OUTSIDE-TO-DMZ rule 5 description "Accept Established-Related Connections to DMZ"
set firewall name FROM-OUTSIDE-TO-DMZ rule 5 action accept
set firewall name FROM-OUTSIDE-TO-DMZ rule 5 state established enable
set firewall name FROM-OUTSIDE-TO-DMZ rule 5 state related enable
set zone-policy zone DMZ from OUTSIDE firewall name FROM-OUTSIDE-TO-DMZ
set firewall name FROM-CORE-TO-OUTSIDE rule 1 description "Accept Internet from Core on port 80"
set firewall name FROM-CORE-TO-OUTSIDE rule 1 action accept
set firewall name FROM-CORE-TO-OUTSIDE rule 1 protocol tcp_udp
set firewall name FROM-CORE-TO-OUTSIDE rule 1 destination port 80
set firewall name FROM-CORE-TO-OUTSIDE rule 2 description "Accept Internet from Core on port 443"
set firewall name FROM-CORE-TO-OUTSIDE rule 2 action accept
set firewall name FROM-CORE-TO-OUTSIDE rule 2 protocol tcp_udp
set firewall name FROM-CORE-TO-OUTSIDE rule 2 destination port 443
set firewall name FROM-CORE-TO-OUTSIDE rule 3 description "Accept ICMP to Datacenter from Admin device"
set firewall name FROM-CORE-TO-OUTSIDE rule 3 action accept
set firewall name FROM-CORE-TO-OUTSIDE rule 3 protocol icmp
set firewall name FROM-CORE-TO-OUTSIDE rule 3 source address 10.1.0.10/24
set firewall name FROM-CORE-TO-OUTSIDE rule 4 description "Allow SSH to Datacenter from Admin device"
set firewall name FROM-CORE-TO-OUTSIDE rule 4 action accept
set firewall name FROM-CORE-TO-OUTSIDE rule 4 protocol tcp
set firewall name FROM-CORE-TO-OUTSIDE rule 4 source address 10.1.0.10/24
set firewall name FROM-CORE-TO-OUTSIDE rule 4 destination port 2022
set zone-policy zone OUTSIDE from CORE firewall name FROM-CORE-TO-OUTSIDE
set firewall name FROM-CORE-TO-DMZ rule 1 description "Accept TCP/UDP to DMZ on port 443"
set firewall name FROM-CORE-TO-DMZ rule 1 action accept
set firewall name FROM-CORE-TO-DMZ rule 1 protocol tcp_udp
set firewall name FROM-CORE-TO-DMZ rule 1 destination port 443
set firewall name FROM-CORE-TO-DMZ rule 2 description "Accept IMAP (TCP) from DMZ on port 1993"
set firewall name FROM-CORE-TO-DMZ rule 2 action accept
set firewall name FROM-CORE-TO-DMZ rule 2 protocol tcp
set firewall name FROM-CORE-TO-DMZ rule 2 destination port 1993
set firewall name FROM-CORE-TO-DMZ rule 3 description "Accept SMTP (TCP) from DMZ on port 1025"
set firewall name FROM-CORE-TO-DMZ rule 3 action accept
set firewall name FROM-CORE-TO-DMZ rule 3 protocol tcp
set firewall name FROM-CORE-TO-DMZ rule 3 destination port 1025
set firewall name FROM-CORE-TO-DMZ rule 4 description "Accept DNS (UDP) from DMZ on port 1053"
set firewall name FROM-CORE-TO-DMZ rule 4 action accept
set firewall name FROM-CORE-TO-DMZ rule 4 protocol udp
set firewall name FROM-CORE-TO-DMZ rule 4 destination port 1053
set firewall name FROM-CORE-TO-DMZ rule 5 description "Accept ICMP to Datacenter from Admin device"
set firewall name FROM-CORE-TO-DMZ rule 5 action accept
set firewall name FROM-CORE-TO-DMZ rule 5 protocol icmp
set firewall name FROM-CORE-TO-DMZ rule 5 source address 10.1.0.10/24
set firewall name FROM-CORE-TO-DMZ rule 6 description "Allow SSH to Datacenter from Admin device"
set firewall name FROM-CORE-TO-DMZ rule 6 action accept
set firewall name FROM-CORE-TO-DMZ rule 6 protocol tcp
set firewall name FROM-CORE-TO-DMZ rule 6 source address 10.1.0.10/24
set firewall name FROM-CORE-TO-DMZ rule 6 destination port 2022
set zone-policy zone DMZ from CORE firewall name FROM-CORE-TO-DMZ
set firewall name TO-CORE rule 1 description "Accept Established-Related Connections to Core"
set firewall name TO-CORE rule 1 action accept
set firewall name TO-CORE rule 1 state established enable
set firewall name TO-CORE rule 1 state related enable
set zone-policy zone CORE from OUTSIDE firewall name TO-CORE
set zone-policy zone CORE from DMZ firewall name TO-CORE
commit
save
```

## FW-2

```
configure
set interfaces ethernet eth0 address 10.0.4.102/24
set interfaces ethernet eth1 address 10.0.6.102/24
set interfaces ethernet eth2 address 10.0.8.102/24
set protocols ospf area 0 network 10.0.4.0/24
set protocols ospf area 0 network 10.0.6.0/24
set protocols ospf area 0 network 10.0.8.0/24
set zone-policy zone OUTSIDE description "Outside/Internet"
set zone-policy zone OUTSIDE interface eth0
set zone-policy zone DMZ description "DMZ"
set zone-policy zone DMZ interface eth1
set zone-policy zone CORE description "Core"
set zone-policy zone CORE interface eth2
set firewall name FROM-DMZ-TO-OUTSIDE rule 1 description "Accept TCP/UDP from DMZ on port 80"
set firewall name FROM-DMZ-TO-OUTSIDE rule 1 action accept
set firewall name FROM-DMZ-TO-OUTSIDE rule 1 protocol tcp_udp
set firewall name FROM-DMZ-TO-OUTSIDE rule 1 destination port 80
set firewall name FROM-DMZ-TO-OUTSIDE rule 2 description "Accept TCP/UDP from DMZ on port 443"
set firewall name FROM-DMZ-TO-OUTSIDE rule 2 action accept
set firewall name FROM-DMZ-TO-OUTSIDE rule 2 protocol tcp_udp
set firewall name FROM-DMZ-TO-OUTSIDE rule 2 destination port 443
set firewall name FROM-DMZ-TO-OUTSIDE rule 3 description "Accept Established-Related Connections to Outside"
set firewall name FROM-DMZ-TO-OUTSIDE rule 3 action accept
set firewall name FROM-DMZ-TO-OUTSIDE rule 3 state established enable
set firewall name FROM-DMZ-TO-OUTSIDE rule 3 state related enable
set zone-policy zone OUTSIDE from DMZ firewall name FROM-DMZ-TO-OUTSIDE
set firewall name FROM-OUTSIDE-TO-DMZ rule 1 description "Accept TCP/UDP to DMZ on port 443"
set firewall name FROM-OUTSIDE-TO-DMZ rule 1 action accept
set firewall name FROM-OUTSIDE-TO-DMZ rule 1 protocol tcp_udp
set firewall name FROM-OUTSIDE-TO-DMZ rule 1 destination port 443
set firewall name FROM-OUTSIDE-TO-DMZ rule 2 description "Accept IMAP (TCP) to DMZ on port 1993"
set firewall name FROM-OUTSIDE-TO-DMZ rule 2 action accept
set firewall name FROM-OUTSIDE-TO-DMZ rule 2 protocol tcp
set firewall name FROM-OUTSIDE-TO-DMZ rule 2 destination port 1993
set firewall name FROM-OUTSIDE-TO-DMZ rule 3 description "Accept SMTP (TCP) to DMZ on port 1025"
set firewall name FROM-OUTSIDE-TO-DMZ rule 3 action accept
set firewall name FROM-OUTSIDE-TO-DMZ rule 3 protocol tcp
set firewall name FROM-OUTSIDE-TO-DMZ rule 3 destination port 1025
set firewall name FROM-OUTSIDE-TO-DMZ rule 4 description "Accept DNS (UDP) to DMZ on port 1053"
set firewall name FROM-OUTSIDE-TO-DMZ rule 4 action accept
set firewall name FROM-OUTSIDE-TO-DMZ rule 4 protocol udp
set firewall name FROM-OUTSIDE-TO-DMZ rule 4 destination port 1053
set firewall name FROM-OUTSIDE-TO-DMZ rule 5 description "Accept Established-Related Connections to DMZ"
set firewall name FROM-OUTSIDE-TO-DMZ rule 5 action accept
set firewall name FROM-OUTSIDE-TO-DMZ rule 5 state established enable
set firewall name FROM-OUTSIDE-TO-DMZ rule 5 state related enable
set zone-policy zone DMZ from OUTSIDE firewall name FROM-OUTSIDE-TO-DMZ
set firewall name FROM-CORE-TO-OUTSIDE rule 1 description "Accept Internet from Core on port 80"
set firewall name FROM-CORE-TO-OUTSIDE rule 1 action accept
set firewall name FROM-CORE-TO-OUTSIDE rule 1 protocol tcp_udp
set firewall name FROM-CORE-TO-OUTSIDE rule 1 destination port 80
set firewall name FROM-CORE-TO-OUTSIDE rule 2 description "Accept Internet from Core on port 443"
set firewall name FROM-CORE-TO-OUTSIDE rule 2 action accept
set firewall name FROM-CORE-TO-OUTSIDE rule 2 protocol tcp_udp
set firewall name FROM-CORE-TO-OUTSIDE rule 2 destination port 443
set firewall name FROM-CORE-TO-OUTSIDE rule 3 description "Accept ICMP to Datacenter from Admin device"
set firewall name FROM-CORE-TO-OUTSIDE rule 3 action accept
set firewall name FROM-CORE-TO-OUTSIDE rule 3 protocol icmp
set firewall name FROM-CORE-TO-OUTSIDE rule 3 source address 10.1.0.10/24
set firewall name FROM-CORE-TO-OUTSIDE rule 4 description "Allow SSH to Datacenter from Admin device"
set firewall name FROM-CORE-TO-OUTSIDE rule 4 action accept
set firewall name FROM-CORE-TO-OUTSIDE rule 4 protocol tcp
set firewall name FROM-CORE-TO-OUTSIDE rule 4 source address 10.1.0.10/24
set firewall name FROM-CORE-TO-OUTSIDE rule 4 destination port 2022
set zone-policy zone OUTSIDE from CORE firewall name FROM-CORE-TO-OUTSIDE
set firewall name FROM-CORE-TO-DMZ rule 1 description "Accept TCP/UDP to DMZ on port 443"
set firewall name FROM-CORE-TO-DMZ rule 1 action accept
set firewall name FROM-CORE-TO-DMZ rule 1 protocol tcp_udp
set firewall name FROM-CORE-TO-DMZ rule 1 destination port 443
set firewall name FROM-CORE-TO-DMZ rule 2 description "Accept IMAP (TCP) to DMZ on port 1993"
set firewall name FROM-CORE-TO-DMZ rule 2 action accept
set firewall name FROM-CORE-TO-DMZ rule 2 protocol tcp
set firewall name FROM-CORE-TO-DMZ rule 2 destination port 1993
set firewall name FROM-CORE-TO-DMZ rule 3 description "Accept SMTP (TCP) to DMZ on port 1025"
set firewall name FROM-CORE-TO-DMZ rule 3 action accept
set firewall name FROM-CORE-TO-DMZ rule 3 protocol tcp
set firewall name FROM-CORE-TO-DMZ rule 3 destination port 1025
set firewall name FROM-CORE-TO-DMZ rule 4 description "Accept DNS (UDP) to DMZ on port 1053"
set firewall name FROM-CORE-TO-DMZ rule 4 action accept
set firewall name FROM-CORE-TO-DMZ rule 4 protocol udp
set firewall name FROM-CORE-TO-DMZ rule 4 destination port 1053
set firewall name FROM-CORE-TO-DMZ rule 5 description "Accept ICMP to Datacenter from Admin device"
set firewall name FROM-CORE-TO-DMZ rule 5 action accept
set firewall name FROM-CORE-TO-DMZ rule 5 protocol icmp
set firewall name FROM-CORE-TO-DMZ rule 5 source address 10.1.0.10/24
set firewall name FROM-CORE-TO-DMZ rule 6 description "Allow SSH to Datacenter from Admin device"
set firewall name FROM-CORE-TO-DMZ rule 6 action accept
set firewall name FROM-CORE-TO-DMZ rule 6 protocol tcp
set firewall name FROM-CORE-TO-DMZ rule 6 source address 10.1.0.10/24
set firewall name FROM-CORE-TO-DMZ rule 6 destination port 2022
set zone-policy zone DMZ from CORE firewall name FROM-CORE-TO-DMZ
set firewall name TO-CORE rule 1 description "Accept Established-Related Connections to Core"
set firewall name TO-CORE rule 1 action accept
set firewall name TO-CORE rule 1 state established enable
set firewall name TO-CORE rule 1 state related enable
set zone-policy zone CORE from OUTSIDE firewall name TO-CORE
set zone-policy zone CORE from DMZ firewall name TO-CORE
commit
save
```


## FW-Internal

```
configure
set interfaces ethernet eth0 address 10.0.12.111/24
set interfaces ethernet eth1 address 10.0.13.111/24
set interfaces ethernet eth2 address 10.0.16.111/24
set protocols ospf area 0 network 10.0.12.0/24
set protocols ospf area 0 network 10.0.13.0/24
set protocols ospf area 0 network 10.0.16.0/24
set firewall name V10-20-SIP-ONLY default-action accept
set firewall name V10-20-SIP-ONLY rule 1 action accept
set firewall name V10-20-SIP-ONLY rule 1 state established enable
set firewall name V10-20-SIP-ONLY rule 1 state related enable
set firewall name V10-20-SIP-ONLY rule 2 action accept
set firewall name V10-20-SIP-ONLY rule 2 protocol udp
set firewall name V10-20-SIP-ONLY rule 2 source address 10.10.0.0/24
set firewall name V10-20-SIP-ONLY rule 2 destination address 10.20.0.0/24
set firewall name V10-20-SIP-ONLY rule 2 destination port 5060
set firewall name V10-20-SIP-ONLY rule 3 action accept
set firewall name V10-20-SIP-ONLY rule 3 protocol udp
set firewall name V10-20-SIP-ONLY rule 3 source address 10.20.0.0/24
set firewall name V10-20-SIP-ONLY rule 3 destination address 10.10.0.0/24
set firewall name V10-20-SIP-ONLY rule 3 destination port 5060
set firewall name V10-20-SIP-ONLY rule 4 action drop
set firewall name V10-20-SIP-ONLY rule 4 source address 10.10.0.0/24
set firewall name V10-20-SIP-ONLY rule 4 destination address 10.20.0.0/24
set firewall name V10-20-SIP-ONLY rule 5 action drop
set firewall name V10-20-SIP-ONLY rule 5 source address 10.20.0.0/24
set firewall name V10-20-SIP-ONLY rule 5 destination address 10.10.0.0/24
set interfaces ethernet eth2 firewall in name V10-20-SIP-ONLY
set zone-policy zone CORE description "Core"
set zone-policy zone CORE interface eth0
set zone-policy zone CORE interface eth1
set zone-policy zone BUILDINGS description "Buildings"
set zone-policy zone BUILDINGS interface eth2
set firewall name BUILDINGS-TO-CORE rule 1 description "Accept TCP/UDP on port 80"
set firewall name BUILDINGS-TO-CORE rule 1 action accept
set firewall name BUILDINGS-TO-CORE rule 1 protocol tcp_udp
set firewall name BUILDINGS-TO-CORE rule 1 destination port 80
set firewall name BUILDINGS-TO-CORE rule 2 description "Accept TCP/UDP on port 443"
set firewall name BUILDINGS-TO-CORE rule 2 action accept
set firewall name BUILDINGS-TO-CORE rule 2 protocol tcp_udp
set firewall name BUILDINGS-TO-CORE rule 2 destination port 443
set firewall name BUILDINGS-TO-CORE rule 4 description "Accept IMAP (TCP) on port 1993"
set firewall name BUILDINGS-TO-CORE rule 4 action accept
set firewall name BUILDINGS-TO-CORE rule 4 protocol tcp
set firewall name BUILDINGS-TO-CORE rule 4 destination port 1993
set firewall name BUILDINGS-TO-CORE rule 5 description "Accept SMTP (TCP) on port 1025"
set firewall name BUILDINGS-TO-CORE rule 5 action accept
set firewall name BUILDINGS-TO-CORE rule 5 protocol tcp
set firewall name BUILDINGS-TO-CORE rule 5 destination port 1025
set firewall name BUILDINGS-TO-CORE rule 6 description "Accept DNS (TCP/UDP) on port 1053"
set firewall name BUILDINGS-TO-CORE rule 6 action accept
set firewall name BUILDINGS-TO-CORE rule 6 protocol tcp_udp
set firewall name BUILDINGS-TO-CORE rule 6 destination port 1053
set firewall name BUILDINGS-TO-CORE rule 7 description "Accept TCP on port 3306"
set firewall name BUILDINGS-TO-CORE rule 7 action accept
set firewall name BUILDINGS-TO-CORE rule 7 protocol tcp
set firewall name BUILDINGS-TO-CORE rule 7 source address 10.20.0.0/24
set firewall name BUILDINGS-TO-CORE rule 7 destination address 10.100.2.0/24
set firewall name BUILDINGS-TO-CORE rule 7 destination port 3306
set firewall name BUILDINGS-TO-CORE rule 8 description "Accept Admin (ICMP) to Core"
set firewall name BUILDINGS-TO-CORE rule 8 action accept
set firewall name BUILDINGS-TO-CORE rule 8 protocol icmp
set firewall name BUILDINGS-TO-CORE rule 8 source address 10.1.0.10/24
set firewall name BUILDINGS-TO-CORE rule 9 description "Allow SSH to Core"
set firewall name BUILDINGS-TO-CORE rule 9 action accept
set firewall name BUILDINGS-TO-CORE rule 9 protocol tcp
set firewall name BUILDINGS-TO-CORE rule 9 source address 10.1.0.10/24
set firewall name BUILDINGS-TO-CORE rule 9 destination port 2022
set zone-policy zone CORE from BUILDINGS firewall name BUILDINGS-TO-CORE
set firewall name CORE-TO-BUILDINGS rule 1 description "Accept Established-Related Connections to Buildings"
set firewall name CORE-TO-BUILDINGS rule 1 action accept
set firewall name CORE-TO-BUILDINGS rule 1 state established enable
set firewall name CORE-TO-BUILDINGS rule 1 state related enable
set zone-policy zone BUILDINGS from CORE firewall name CORE-TO-BUILDINGS
commit
save
```

## FW-Datacenter

```
configure
set interfaces ethernet eth0 address 10.0.14.121/24
set interfaces ethernet eth1 address 10.0.15.121/24
set interfaces ethernet eth2 address 10.0.17.121/24
set protocols ospf area 0 network 10.0.14.0/24
set protocols ospf area 0 network 10.0.15.0/24
set protocols ospf area 0 network 10.0.17.0/24
set firewall name INTRA-DATACENTER default-action accept
set firewall name INTRA-DATACENTER rule 1 action accept
set firewall name INTRA-DATACENTER rule 1 state established enable
set firewall name INTRA-DATACENTER rule 1 state related enable
set firewall name INTRA-DATACENTER rule 2 action drop
set firewall name INTRA-DATACENTER rule 2 source address 10.100.0.0/24
set firewall name INTRA-DATACENTER rule 2 destination address 10.100.1.0/24
set firewall name INTRA-DATACENTER rule 3 action drop
set firewall name INTRA-DATACENTER rule 3 source address 10.100.0.0/24
set firewall name INTRA-DATACENTER rule 3 destination address 10.100.2.0/24
set firewall name INTRA-DATACENTER rule 4 action drop
set firewall name INTRA-DATACENTER rule 4 source address 10.100.1.0/24
set firewall name INTRA-DATACENTER rule 4 destination address 10.100.0.0/24
set firewall name INTRA-DATACENTER rule 5 action drop
set firewall name INTRA-DATACENTER rule 5 source address 10.100.1.0/24
set firewall name INTRA-DATACENTER rule 5 destination address 10.100.2.0/24
set firewall name INTRA-DATACENTER rule 6 action drop
set firewall name INTRA-DATACENTER rule 6 source address 10.100.2.0/24
set firewall name INTRA-DATACENTER rule 6 destination address 10.100.0.0/24
set firewall name INTRA-DATACENTER rule 7 action drop
set firewall name INTRA-DATACENTER rule 7 source address 10.100.2.0/24
set firewall name INTRA-DATACENTER rule 7 destination address 10.100.1.0/24
set interfaces ethernet eth2 firewall in name INTRA-DATACENTER
set zone-policy zone CORE description "Core"
set zone-policy zone CORE interface eth0
set zone-policy zone CORE interface eth1
set zone-policy zone DATACENTER description "Datacenter"
set zone-policy zone DATACENTER interface eth2
set firewall group network-group VLANS-10-20 network 10.10.0.0/24
set firewall group network-group VLANS-10-20 network 10.20.0.0/24
set firewall group network-group INT-IDNS network 10.100.0.0/24
set firewall group network-group INT-IDNS network 10.100.1.0/24
set firewall name FROM-CORE-TO-DC rule 1 description "Accept TCP on port 443"
set firewall name FROM-CORE-TO-DC rule 1 action accept
set firewall name FROM-CORE-TO-DC rule 1 protocol tcp
set firewall name FROM-CORE-TO-DC rule 1 source group network-group VLANS-10-20
set firewall name FROM-CORE-TO-DC rule 1 destination group network-group INT-IDNS
set firewall name FROM-CORE-TO-DC rule 1 destination port 443
set firewall name FROM-CORE-TO-DC rule 2 description "Accept DNS on port 53"
set firewall name FROM-CORE-TO-DC rule 2 action accept
set firewall name FROM-CORE-TO-DC rule 2 protocol tcp_udp
set firewall name FROM-CORE-TO-DC rule 2 source group network-group VLANS-10-20
set firewall name FROM-CORE-TO-DC rule 2 destination group network-group INT-IDNS
set firewall name FROM-CORE-TO-DC rule 2 destination port 1053
set firewall name FROM-CORE-TO-DC rule 3 description "Accept TCP on port 3306"
set firewall name FROM-CORE-TO-DC rule 3 action accept
set firewall name FROM-CORE-TO-DC rule 3 protocol tcp
set firewall name FROM-CORE-TO-DC rule 3 source address 10.20.0.0/24
set firewall name FROM-CORE-TO-DC rule 3 destination address 10.100.2.0/24
set firewall name FROM-CORE-TO-DC rule 3 destination port 3306
set firewall name FROM-CORE-TO-DC rule 4 description "Accept Established-Related Connections to Datacenter"
set firewall name FROM-CORE-TO-DC rule 4 action accept
set firewall name FROM-CORE-TO-DC rule 4 state established enable
set firewall name FROM-CORE-TO-DC rule 4 state related enable
set firewall name FROM-CORE-TO-DC rule 5 description "Accept ICMP to Datacenter from Admin device"
set firewall name FROM-CORE-TO-DC rule 5 action accept
set firewall name FROM-CORE-TO-DC rule 5 protocol icmp
set firewall name FROM-CORE-TO-DC rule 5 source address 10.1.0.10/24
set firewall name FROM-CORE-TO-DC rule 6 description "Allow SSH to Datacenter from Admin device"
set firewall name FROM-CORE-TO-DC rule 6 action accept
set firewall name FROM-CORE-TO-DC rule 6 protocol tcp
set firewall name FROM-CORE-TO-DC rule 6 source address 10.1.0.10/24
set firewall name FROM-CORE-TO-DC rule 6 destination port 2022
set firewall name TO-CORE rule 1 description "Accept Established-Related Connections"
set firewall name TO-CORE rule 1 action accept
set firewall name TO-CORE rule 1 state established enable
set firewall name TO-CORE rule 1 state related enable
set firewall name TO-CORE rule 2 description "Accept TCP/UDP on port 80"
set firewall name TO-CORE rule 2 action accept
set firewall name TO-CORE rule 2 protocol tcp_udp
set firewall name TO-CORE rule 2 destination port 80
set firewall name TO-CORE rule 3 description "Accept TCP/UDP on port 443"
set firewall name TO-CORE rule 3 action accept
set firewall name TO-CORE rule 3 protocol tcp_udp
set firewall name TO-CORE rule 3 destination port 443
set firewall name TO-CORE rule 4 description "Accept IMAP (TCP) on port 1993"
set firewall name TO-CORE rule 4 action accept
set firewall name TO-CORE rule 4 protocol tcp
set firewall name TO-CORE rule 4 destination port 1993
set firewall name TO-CORE rule 5 description "Accept SMTP (TCP) on port 1025"
set firewall name TO-CORE rule 5 action accept
set firewall name TO-CORE rule 5 protocol tcp
set firewall name TO-CORE rule 5 destination port 1025
set firewall name TO-CORE rule 6 description "Accept DNS (UDP) on port 1053"
set firewall name TO-CORE rule 6 action accept
set firewall name TO-CORE rule 6 protocol udp
set firewall name TO-CORE rule 6 destination port 1053
set zone-policy zone DATACENTER from CORE firewall name FROM-CORE-TO-DC
set zone-policy zone CORE from DATACENTER firewall name TO-CORE
commit
save
```