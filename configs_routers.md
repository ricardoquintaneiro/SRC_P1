# Configurações dos routers

## R1

```
conf t
ip routing
ip route 100.0.0.128 255.255.255.192 100.0.0.2
ip route 100.0.0.192 255.255.255.192 100.0.0.6
router ospf 1 
default-information originate always
int f0/0
ip addr 100.0.0.1 255.255.255.252
no shut
int f0/1
ip addr 100.0.0.5 255.255.255.252
no shut
int f1/0
ip addr 10.0.0.1 255.255.255.0
ip ospf 1 area 0
no shut
int f1/1
ip addr 10.0.1.1 255.255.255.0
ip ospf 1 area 0
no shut
exit
access-list 1 permit 10.0.0.0 0.0.255.255
access-list 1 permit 10.10.0.0 0.0.0.255
access-list 1 permit 10.20.0.0 0.0.0.255
access-list 1 permit 10.100.0.0 0.0.255.255
ip nat pool POOL 100.0.0.65 100.0.0.126 netmask 255.255.255.192
ip nat Stateful id 1
primary 10.0.0.1
peer 10.0.0.2
mapping-id 10
ip nat inside source list 1 pool POOL mapping-id 10 overload
int f0/0
ip nat outside
int f0/1
ip nat outside
int f1/0
ip nat inside
int f1/1
ip nat inside
end
write
```

## R2

```
conf t
ip routing
ip route 100.0.0.128 255.255.255.192 100.0.0.10
ip route 100.0.0.192 255.255.255.192 100.0.0.14
router ospf 1 
default-information originate always
int f0/0
ip addr 100.0.0.9 255.255.255.252
no shut
int f0/1
ip addr 100.0.0.13 255.255.255.252
no shut
int f1/0
ip addr 10.0.0.2 255.255.255.0
ip ospf 1 area 0
no shut
int f1/1
ip addr 10.0.2.2 255.255.255.0
ip ospf 1 area 0
no shut
exit
access-list 1 permit 10.0.0.0 0.0.255.255
access-list 1 permit 10.10.0.0 0.0.0.255
access-list 1 permit 10.20.0.0 0.0.0.255
access-list 1 permit 10.100.0.0 0.0.255.255
ip nat pool POOL 100.0.0.65 100.0.0.126 netmask 255.255.255.192
ip nat Stateful id 1
backup 10.0.0.2
peer 10.0.0.1
mapping-id 10
ip nat inside source list 1 pool POOL mapping-id 10 overload
int f0/0
ip nat outside
int f0/1
ip nat outside
int f1/0
ip nat inside
int f1/1
ip nat inside
end
write
```

## SWL3-C1

```
conf t
ip routing
int f0/0
ip addr 10.0.9.31 255.255.255.0
ip ospf 1 area 0
no shut
int f0/1
ip addr 10.0.12.31 255.255.255.0
ip ospf 1 area 0
no shut
int f1/0
no switchport
ip addr 10.0.14.31 255.255.255.0
ip ospf 1 area 0
no shut
int f1/1
no switchport
ip addr 10.0.11.31 255.255.255.0
ip ospf 1 area 0
no shut
end
write
```

## SWL3-C2

```
conf t
ip routing
int f0/0
ip addr 10.0.10.32 255.255.255.0
ip ospf 1 area 0
no shut
int f0/1
ip addr 10.0.13.32 255.255.255.0
ip ospf 1 area 0
no shut
int f1/0
no switchport
ip addr 10.0.15.32 255.255.255.0
ip ospf 1 area 0
no shut
int f1/1
no switchport
ip addr 10.0.11.32 255.255.255.0
ip ospf 1 area 0
no shut
end
write
```

## SWL3-1

```
vlan database
vlan 10
vlan 20
exit
conf t
ip routing
int f0/0
ip addr 10.0.16.41 255.255.255.0
ip ospf 1 area 0
no shut
int f1/0
switchport mode trunk
switchport trunk allowed vlan 1,10,20,1002-1005
switchport trunk encapsulation dot1q
int vlan 10
ip addr 10.10.0.1 255.255.255.0
ip ospf 1 area 0
no shut
int vlan 20
ip addr 10.20.0.1 255.255.255.0
ip ospf 1 area 0
no shut
end
write
```

## SWL3-2

```
conf t
ip routing
int f0/0
ip addr 10.0.17.42 255.255.255.0
ip ospf 1 area 0
no shut
int f0/1
ip addr 10.100.0.1 255.255.255.0
ip addr 10.100.1.1 255.255.255.0 secondary
ip addr 10.100.2.1 255.255.255.0 secondary
ip ospf 1 area 0
no shut
end
write
```

