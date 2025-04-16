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