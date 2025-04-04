# Subnetting

## Internet: 100.0.0.0/24

PC da Internet: 100.0.0.100


## DMZ: 200.0.0.0/24

### Web services: 200.0.0.0/25

**128 endereços IP** - 125 terminais + 1 gateway + 2 IPs de broadcast/rede 

IPs disponíveis:
- `200.0.0.1 - 200.0.0.126`

### E-mail services: 200.0.0.128/26

64 endereços IP - 61 terminais + 1 gateway + 2 IPs de broadcast/rede

IPs disponíveis:
- `200.0.0.129 - 200.0.0.190`

### DNS services: 200.0.0.192/26

64 endereços IP - 61 terminais + 1 gateway + 2 IPs de broadcast/rede

IPs disponíveis:
- `200.0.0.193 - 200.0.0.254`

## VLAN 10: 10.10.0.0/24

256 endereços IP - 253 terminais + 1 gateway + 2 IPs de broadcast/rede

IPs disponíveis:
- `10.10.0.1 - 10.10.0.254`


## VLAN 20: 10.20.0.0/24

256 endereços IP - 253 terminais + 1 gateway + 2 IPs de broadcast/rede

IPs disponíveis:
- `10.20.0.1 - 10.20.0.254`

## Datacenter: 10.100.0.0/16

### Intranet/Storage: 10.100.0.0/24

256 endereços IP - 253 terminais + 1 gateway + 2 IPs de broadcast/rede
IPs disponíveis:
- `10.100.0.1 - 10.100.0.254`

### DNS interno: 10.100.1.0/24

256 endereços IP - 253 terminais + 1 gateway + 2 IPs de broadcast/rede
IPs disponíveis:
- `10.100.1.1 - 10.100.1.254`

### Databases: 10.100.2.0/24

256 endereços IP - 253 terminais + 1 gateway + 2 IPs de broadcast/rede
IPs disponíveis:
- `10.100.2.1 - 10.100.2.254`

## Internal Connections: 10.0.0.0/16

### R1 - R2: 10.0.0.0/24

R1: 10.0.0.1/24
R2: 10.0.0.2/24

### 