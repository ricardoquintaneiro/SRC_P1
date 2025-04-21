# Configurações dos Load Balancers

## LB-1

```
configure
set interfaces ethernet eth0 address 10.0.1.11/24
set interfaces ethernet eth1 address 10.0.2.11/24
set interfaces ethernet eth2 address 10.0.3.11/24
set interfaces ethernet eth3 address 10.0.4.11/24
set interfaces ethernet eth5 address 10.0.22.11/24
set protocols ospf area 0 network 10.0.1.0/24
set protocols ospf area 0 network 10.0.2.0/24
set protocols ospf area 0 network 10.0.3.0/24
set protocols ospf area 0 network 10.0.4.0/24
set protocols ospf area 0 network 10.0.22.0/24
set load-balancing wan interface-health eth2 nexthop 10.0.3.101
set load-balancing wan interface-health eth3 nexthop 10.0.4.102
set load-balancing wan rule 1 inbound-interface eth0
set load-balancing wan rule 1 inbound-interface eth1
set load-balancing wan rule 1 interface eth2 weight 1
set load-balancing wan rule 1 interface eth3 weight 1
set load-balancing wan sticky-connections inbound
set load-balancing wan disable-source-nat
set high-availability vrrp group LBCluster vrid 10
set high-availability vrrp group LBCluster interface eth5
set high-availability vrrp group LBCluster virtual-address 192.168.100.1/24
set high-availability vrrp sync-group LBCluster member LBCluster
set high-availability vrrp group LBCluster rfc3768-compatibility
set service conntrack-sync accept-protocol 'tcp,udp,icmp'
set service conntrack-sync failover-mechanism vrrp sync-group LBCluster
set service conntrack-sync interface eth5
set service conntrack-sync mcast-group 225.0.0.50
set service conntrack-sync disable-external-cache
commit
save
```

## LB-2

```
configure
set interfaces ethernet eth0 address 10.0.18.12/24
set interfaces ethernet eth1 address 10.0.19.12/24
set interfaces ethernet eth2 address 10.0.20.12/24
set interfaces ethernet eth3 address 10.0.21.12/24
set interfaces ethernet eth5 address 10.0.22.12/24
set protocols ospf area 0 network 10.0.18.0/24
set protocols ospf area 0 network 10.0.19.0/24
set protocols ospf area 0 network 10.0.20.0/24
set protocols ospf area 0 network 10.0.21.0/24
set protocols ospf area 0 network 10.0.22.0/24
set load-balancing wan interface-health eth2 nexthop 10.0.20.101
set load-balancing wan interface-health eth3 nexthop 10.0.21.102
set load-balancing wan rule 1 inbound-interface eth0
set load-balancing wan rule 1 inbound-interface eth1
set load-balancing wan rule 1 interface eth2 weight 1
set load-balancing wan rule 1 interface eth3 weight 1
set load-balancing wan sticky-connections inbound
set load-balancing wan disable-source-nat
set high-availability vrrp group LBCluster vrid 10
set high-availability vrrp group LBCluster interface eth5
set high-availability vrrp group LBCluster virtual-address 192.168.100.1/24
set high-availability vrrp sync-group LBCluster member LBCluster
set high-availability vrrp group LBCluster rfc3768-compatibility
set service conntrack-sync accept-protocol 'tcp,udp,icmp'
set service conntrack-sync failover-mechanism vrrp sync-group LBCluster
set service conntrack-sync interface eth5
set service conntrack-sync mcast-group 225.0.0.50
set service conntrack-sync disable-external-cache
commit
save
```

## LB-C1

```
configure
set interfaces ethernet eth0 address 10.0.7.12/24
set interfaces ethernet eth1 address 10.0.8.12/24
set interfaces ethernet eth2 address 10.0.9.12/24
set interfaces ethernet eth3 address 10.0.10.12/24
set interfaces ethernet eth5 address 10.0.27.21/24
set protocols ospf area 0 network 10.0.7.0/24
set protocols ospf area 0 network 10.0.8.0/24
set protocols ospf area 0 network 10.0.9.0/24
set protocols ospf area 0 network 10.0.10.0/24
set protocols ospf area 0 network 10.0.27.0/24
set load-balancing wan interface-health eth0 nexthop 10.0.7.101
set load-balancing wan interface-health eth1 nexthop 10.0.8.102
set load-balancing wan rule 1 inbound-interface eth2
set load-balancing wan rule 1 inbound-interface eth3
set load-balancing wan rule 1 interface eth0 weight 1
set load-balancing wan rule 1 interface eth1 weight 1
set load-balancing wan sticky-connections inbound
set load-balancing wan disable-source-nat
set high-availability vrrp group LBCluster vrid 10
set high-availability vrrp group LBCluster interface eth5
set high-availability vrrp group LBCluster virtual-address 192.168.100.2/24
set high-availability vrrp sync-group LBCluster member LBCluster
set high-availability vrrp group LBCluster rfc3768-compatibility
set service conntrack-sync accept-protocol 'tcp,udp,icmp'
set service conntrack-sync failover-mechanism vrrp sync-group LBCluster
set service conntrack-sync interface eth5
set service conntrack-sync mcast-group 225.0.0.50
set service conntrack-sync disable-external-cache
commit
save
```

## LB-C2

```
configure
set interfaces ethernet eth0 address 10.0.23.22/24
set interfaces ethernet eth1 address 10.0.24.22/24
set interfaces ethernet eth2 address 10.0.25.22/24
set interfaces ethernet eth3 address 10.0.26.22/24
set interfaces ethernet eth5 address 10.0.27.22/24
set protocols ospf area 0 network 10.0.23.0/24
set protocols ospf area 0 network 10.0.24.0/24
set protocols ospf area 0 network 10.0.25.0/24
set protocols ospf area 0 network 10.0.26.0/24
set protocols ospf area 0 network 10.0.27.0/24
set load-balancing wan interface-health eth0 nexthop 10.0.23.101
set load-balancing wan interface-health eth1 nexthop 10.0.24.101
set load-balancing wan rule 1 inbound-interface eth2
set load-balancing wan rule 1 inbound-interface eth3
set load-balancing wan rule 1 interface eth0 weight 1
set load-balancing wan rule 1 interface eth1 weight 1
set load-balancing wan sticky-connections inbound
set load-balancing wan disable-source-nat
set high-availability vrrp group LBCluster vrid 10
set high-availability vrrp group LBCluster interface eth5
set high-availability vrrp group LBCluster virtual-address 192.168.100.2/24
set high-availability vrrp sync-group LBCluster member LBCluster
set high-availability vrrp group LBCluster rfc3768-compatibility
set service conntrack-sync accept-protocol 'tcp,udp,icmp'
set service conntrack-sync failover-mechanism vrrp sync-group LBCluster
set service conntrack-sync interface eth5
set service conntrack-sync mcast-group 225.0.0.50
set service conntrack-sync disable-external-cache
commit
save
```

## LB-DMZ-1

```
configure
set interfaces ethernet eth0 address 10.0.5.21/24
set interfaces ethernet eth1 address 10.0.6.21/24
set interfaces ethernet eth2 address 200.0.0.1/25
set interfaces ethernet eth2 address 200.0.0.129/26
set interfaces ethernet eth2 address 200.0.0.193/26
set protocols ospf area 0 network 10.0.5.0/24
set protocols ospf area 0 network 10.0.6.0/24
set protocols ospf area 0 network 200.0.0.0/24
set load-balancing wan interface-health eth0 nexthop 10.0.5.101
set load-balancing wan interface-health eth1 nexthop 10.0.6.102
set load-balancing wan rule 1 inbound-interface eth2
set load-balancing wan rule 1 interface eth0 weight 1
set load-balancing wan rule 1 interface eth1 weight 1
set load-balancing wan sticky-connections inbound
set load-balancing wan disable-source-nat
commit
save
```
