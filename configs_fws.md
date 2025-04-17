# Configurações das Firewalls

## FW-Stateless-1

```
configure
set protocols static route 0.0.0.0/0 next-hop 100.0.0.1
set protocols static route 0.0.0.0/0 next-hop 100.0.0.9
set interfaces ethernet eth0 address 100.0.0.129/26
set interfaces ethernet eth1 address 100.0.0.2/30
set interfaces ethernet eth2 address 100.0.0.10/30
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
set protocols static table 10 route 0.0.0.0/0 next-hop 127.0.0.1
set policy route VLAN10-TO-VLAN20 rule 1 description "Force V10-V20 via loopback"
set policy route VLAN10-TO-VLAN20 rule 1 source address 10.10.0.0/24
set policy route VLAN10-TO-VLAN20 rule 1 destination address 10.20.0.0/24
set policy route VLAN10-TO-VLAN20 rule 1 set table 10
set policy route VLAN20-TO-VLAN10 rule 1 description "Force V20-V10 via loopback"
set policy route VLAN20-TO-VLAN10 rule 1 source address 10.20.0.0/24
set policy route VLAN20-TO-VLAN10 rule 1 destination address 10.10.0.0/24
set policy route VLAN20-TO-VLAN10 rule 1 set table 10
set interfaces ethernet eth2 policy route VLAN10-TO-VLAN20
set interfaces ethernet eth2 policy route VLAN20-TO-VLAN10
set zone-policy zone CORE description "Core"
set zone-policy zone CORE interface eth0
set zone-policy zone CORE interface eth1
set zone-policy zone BUILDINGS description "Buildings"
set zone-policy zone BUILDINGS interface eth2
set firewall name BUILDINGS-TO-LOOPBACK rule 1 description "Accept SIP with TCP/UDP on port 5060"
set firewall name BUILDINGS-TO-LOOPBACK rule 1 action accept
set firewall name BUILDINGS-TO-LOOPBACK rule 1 protocol tcp_udp
set firewall name BUILDINGS-TO-LOOPBACK rule 1 source address 10.10.0.0/24
set firewall name BUILDINGS-TO-LOOPBACK rule 1 destination address 10.20.0.0/24
set firewall name BUILDINGS-TO-LOOPBACK rule 1 destination port 5060
set firewall name BUILDINGS-TO-LOOPBACK rule 2 description "Accept SIP with SCTP on port 5060"
set firewall name BUILDINGS-TO-LOOPBACK rule 2 action accept
set firewall name BUILDINGS-TO-LOOPBACK rule 2 protocol sctp
set firewall name BUILDINGS-TO-LOOPBACK rule 2 source address 10.10.0.0/24
set firewall name BUILDINGS-TO-LOOPBACK rule 2 destination address 10.20.0.0/24
set firewall name BUILDINGS-TO-LOOPBACK rule 3 description "Accept SIP with TCP/UDP on port 5060"
set firewall name BUILDINGS-TO-LOOPBACK rule 3 action accept
set firewall name BUILDINGS-TO-LOOPBACK rule 3 protocol tcp_udp
set firewall name BUILDINGS-TO-LOOPBACK rule 3 source address 10.20.0.0/24
set firewall name BUILDINGS-TO-LOOPBACK rule 3 destination address 10.10.0.0/24
set firewall name BUILDINGS-TO-LOOPBACK rule 3 destination port 5060
set firewall name BUILDINGS-TO-LOOPBACK rule 4 description "Accept SIP with SCTP on port 5060"
set firewall name BUILDINGS-TO-LOOPBACK rule 4 action accept
set firewall name BUILDINGS-TO-LOOPBACK rule 4 protocol sctp
set firewall name BUILDINGS-TO-LOOPBACK rule 4 source address 10.20.0.0/24
set firewall name BUILDINGS-TO-LOOPBACK rule 4 destination address 10.10.0.0/24
set firewall name LOOPBACK-TO-BUILDINGS rule 1 description "Accept Established-Related Connections"
set firewall name LOOPBACK-TO-BUILDINGS rule 1 action accept
set firewall name LOOPBACK-TO-BUILDINGS rule 1 state established enable
set firewall name LOOPBACK-TO-BUILDINGS rule 1 state related enable
set zone-policy zone local-zone from BUILDINGS firewall name BUILDINGS-TO-LOOPBACK
set zone-policy zone BUILDINGS from local-zone firewall name LOOPBACK-TO-BUILDINGS
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
set firewall name TO-CORE rule 1 description "Accept Established-Related Connections"
set firewall name TO-CORE rule 1 action accept
set firewall name TO-CORE rule 1 state established enable
set firewall name TO-CORE rule 1 state related enable
set zone-policy zone DATACENTER from CORE firewall name FROM-CORE-TO-DC
set zone-policy zone CORE from DATACENTER firewall name TO-CORE
commit
save
```