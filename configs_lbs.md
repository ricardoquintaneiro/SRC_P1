# Configurações dos Load Balancers

## LB-1

```
configure
set interfaces ethernet eth0 address 10.0.1.11/24
set interfaces ethernet eth1 address 10.0.2.11/24
set interfaces ethernet eth2 address 10.0.3.11/24
set interfaces ethernet eth3 address 10.0.4.11/24
set protocols ospf area 0 network 10.0.1.0/24
set protocols ospf area 0 network 10.0.2.0/24
set protocols ospf area 0 network 10.0.3.0/24
set protocols ospf area 0 network 10.0.4.0/24
commit
save
```

## LB-2

```
configure
set interfaces ethernet eth0 address 10.0.7.12/24
set interfaces ethernet eth1 address 10.0.8.12/24
set interfaces ethernet eth2 address 10.0.9.12/24
set interfaces ethernet eth3 address 10.0.10.12/24
set protocols ospf area 0 network 10.0.7.0/24
set protocols ospf area 0 network 10.0.8.0/24
set protocols ospf area 0 network 10.0.9.0/24
set protocols ospf area 0 network 10.0.10.0/24
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
commit
save
```
