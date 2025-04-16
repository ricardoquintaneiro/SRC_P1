# Configurações dos Load Balancers

## LB-DMZ-1

```
configure
set interfaces ethernet eth0 address 10.0.5.21/24
set interfaces ethernet eth1 address 10.0.6.21/24
set interfaces ethernet eth2 address 200.0.0.1/25
set interfaces ethernet eth2 address 200.0.0.129/26
set interfaces ethernet eth2 address 200.0.0.193/26
commit
save
```