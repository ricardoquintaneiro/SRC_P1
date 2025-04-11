# Configurações dos VPCS

## Internet

### INTERNET-1

```
ip 100.0.0.201/24 100.0.0.121
save
```

### INTERNET-2

```
ip 100.0.0.202/24 100.0.0.122
save
```

## DMZ

### DMZ-WEB

```
ip 200.0.0.10/25 200.0.0.1
save
```

### DMZ-EMAIL

```
ip 200.0.0.130/26 200.0.0.129
save
```

### DMZ-DNS

```
ip 200.0.0.200/26 200.0.0.193
save
```

## VLANs internas

### PC-VLAN10

```
ip 10.10.0.10/24 10.10.0.1
save
```

### PC-VLAN20

```
ip 10.20.0.10/24 10.20.0.1
save
```

## Datacenters

### Datacenter-Intranet/Storage

```
ip 10.100.0.10/24 10.100.0.1
save
```

### Datacenter-Internal/DNS

```
ip 10.100.1.10/24 10.100.1.1
save
```

### Datacenter-Database

```
ip 10.100.2.10/24 10.100.2.1
save
```