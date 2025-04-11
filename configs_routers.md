# Configurações dos routers

## R1

```
conf t
end
write
```

## R2

```
conf t
end
write
```

## SWL3-C1

```
conf t
int f0/0
ip addr 10.0.9.31 255.255.255.0
no shut
int f0/1
ip addr 10.0.12.31 255.255.255.0
no shut
int f1/0
ip addr 10.0.14.31 255.255.255.0
no shut
int f1/1
ip addr 10.0.11.31 255.255.255.0
no shut
end
write
```

## SWL3-C2

```
conf t
int f0/0
ip addr 10.0.10.32 255.255.255.0
no shut
int f0/1
ip addr 10.0.13.32 255.255.255.0
no shut
int f1/0
ip addr 10.0.15.32 255.255.255.0
no shut
int f1/1
ip addr 10.0.11.32 255.255.255.0
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
no shut
int f1/0
switchport mode trunk
switchport trunk allowed vlan 1,10,20,1002-1005
switchport trunk encapsulation dot1q
int vlan 10
ip addr 10.10.0.1 255.255.255.0
no shut
int vlan 20
ip addr 10.20.0.1 255.255.255.0
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
no shut
int f0/1
ip addr 10.100.0.1 255.255.255.0
ip addr 10.100.1.1 255.255.255.0 secondary
ip addr 10.100.2.1 255.255.255.0 secondary
no shut
end
write
```