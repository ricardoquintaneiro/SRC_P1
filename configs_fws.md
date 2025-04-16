# Configurações das Firewalls

## FW-Internal

```
configure
set interfaces ethernet eth0 address 10.0.12.111/24
set interfaces ethernet eth1 address 10.0.13.111/24
set interfaces ethernet eth2 address 10.0.16.111/24
set protocols ospf area 0 network 10.0.12.0/24
set protocols ospf area 0 network 10.0.13.0/24
set protocols ospf area 0 network 10.0.16.0/24
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
commit
save
```