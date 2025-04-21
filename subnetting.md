# Subnetting

## Internet: 100.0.0.0/24

### INTERNET-1 - FW-ST1: 100.0.0.128/26

PC da Internet 1: `100.0.0.131`

FW-ST1: `100.0.0.129`

### INTERNET-2 - FW-ST2: 100.0.192/26

PC da Internet 2: `100.0.0.202`

FW-ST2: `100.0.0.193`

### R1 - FW-ST1: 100.0.0.0/30

**4 endereços IP** - 2 routers + 2 IPs de broadcast/rede 

IPs disponíveis:
- `100.0.0.1 - 100.0.0.2`

`R1: 100.0.0.1/30`

`FW-ST1: 100.0.0.2/30`

### R1 - FW-ST2: 100.0.0.4/30

**4 endereços IP** - 2 routers + 2 IPs de broadcast/rede 

IPs disponíveis:
- `100.0.0.5 - 100.0.0.6`

`R1: 100.0.0.5/30`

`FW-ST2: 100.0.0.6/30`

### R2 - FW-ST1: 100.0.0.8/30

**4 endereços IP** - 2 routers + 2 IPs de broadcast/rede 

IPs disponíveis:
- `100.0.0.9 - 100.0.0.10`

`R2: 100.0.0.9/30`

`FW-ST1: 100.0.0.10/30`

### R2 - FW-ST2: 100.0.0.12/30

**4 endereços IP** - 2 routers + 2 IPs de broadcast/rede 

IPs disponíveis:
- `100.0.0.13 - 100.0.0.14`

`R2: 100.0.0.13/30`

`FW-ST3: 100.0.0.14/30`

### Gama de IPs para o NAT: 100.0.0.64/26

**64 endereços IP** - 62 terminais + 2 IP de broadcast/rede

`100.0.0.65 - 100.0.0.126`

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

## VLAN 1: 10.1.0.0/24

**256 endereços IP** - 253 terminais + 1 gateway + 2 IPs de broadcast/rede

Admin-PC: `10.1.0.10/24`
Gateway: `10.1.0.1/24`

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

`R1: 10.0.0.1/24`

`R2: 10.0.0.2/24`

### R1 - LB-1: 10.0.1.0/24

`R1: 10.0.1.1/24`

`LB-1: 10.0.1.11/24`

### R1 - LB-2: 10.0.18.0/24

`R1: 10.0.18.1/24`

`LB-2: 10.0.18.12/24`

### R2 - LB-1: 10.0.2.0/24

`R2: 10.0.2.2/24`

`LB-1: 10.0.2.11/24`

### R2 - LB-2: 10.0.19.0/24

`R2: 10.0.19.2/24`

`LB-2: 10.0.19.12/24`

### LB-1 - FW1: 10.0.3.0/24

`LB-1: 10.0.3.11/24`

`FW1: 10.0.3.101/24`

### LB-1 - FW2: 10.0.4.0/24

`LB-1: 10.0.4.11/24`

`FW2: 10.0.4.102/24`

### LB-2 - FW1: 10.0.20.0/24

`LB-2: 10.0.20.12/24`

`FW1: 10.0.20.101/24`

### LB-2 - FW2: 10.0.21.0/24

`LB-2: 10.0.21.12/24`

`FW2: 10.0.21.102/24`

### LB-1 - LB-2: 10.0.22.0/24

`LB-1: 10.0.22.11/24`

`LB-2: 10.0.22.12/24`

### FW1 - LB-DMZ-1: 10.0.5.0/24

`FW1: 10.0.5.101/24`

`LB-DMZ-1: 10.0.5.21/24`

### FW2 - LB-DMZ-1: 10.0.6.0/24

`FW2: 10.0.6.102/24`

`LB-DMZ-1: 10.0.6.21/24`

### FW1 - LB-C1: 10.0.7.0/24

`FW1: 10.0.7.101/24`

`LB-C1: 10.0.7.12/24`

### FW1 - LB-C2: 10.0.23.0/24

`FW1: 10.0.23.101/24`

`LB-C2: 10.0.23.22/24`

### FW2 - LB-C1: 10.0.8.0/24

`FW2: 10.0.8.102/24`

`LB-C1: 10.0.8.12/24`

### FW2 - LB-C2: 10.0.24.0/24

`FW2: 10.0.24.102/24`

`LB-C2: 10.0.24.22/24`

### LB-C1 - SWL3-C1: 10.0.9.0/24

`LB-C1: 10.0.9.12/24`

`SWL3-C1: 10.0.9.31/24`

### LB-C1 - SWL3-C2: 10.0.10.0/24

`LB-C1: 10.0.10.12/24`

`SWL3-C2: 10.0.10.32/24`

### LB-C2 - SWL3-C1: 10.0.25.0/24

`LB-C2: 10.0.25.22/24`

`SWL3-C1: 10.0.25.31/24`

### LB-C2 - SWL3-C2: 10.0.26.0/24

`LB-C2: 10.0.26.22/24`

`SWL3-C2: 10.0.26.32/24`

### LB-C1 - LB-C2: 10.0.27.0/24

`LB-C1: 10.0.27.21/24`

`LB-C2: 10.0.27.22/24`

### SWL3-C1 - SWL3-C2: 10.0.11.0/24

`SWL3-C1: 10.0.11.31/24`

`SWL3-C2: 10.0.11.32/24`

### SWL3-C1 - FW-Internal: 10.0.12.0/24

`SWL3-C1: 10.0.12.31/24`

`FW-Internal: 10.0.12.111/24`

### SWL3-C2 - FW-Internal: 10.0.13.0/24

`SWL3-C2: 10.0.13.32/24`

`FW-Internal: 10.0.13.111/24`

### SWL3-C1 - FW-Datacenter: 10.0.14.0/24

`SWL3-C1: 10.0.14.31/24`

`FW-Datacenter: 10.0.14.121/24`

### SWL3-C2 - FW-Datacenter: 10.0.15.0/24

`SWL3-C2: 10.0.15.32/24`

`FW-Datacenter: 10.0.15.121/24`

### FW-Internal - SWL3-1: 10.0.16.0/24

`FW-Internal: 10.0.16.111/24`

`SWL3-1: 10.0.16.41/24`

### FW-Datacenter - SWL3-2: 10.0.17.0/24

`FW-Datacenter: 10.0.17.121/24`

`SWL3-2: 10.0.17.42/24`