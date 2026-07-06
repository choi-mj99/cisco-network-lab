# EDGE-RTR-01 Configuration

> Cisco 2911 Router  
> Cisco Enterprise Network Lab

---

## 1. Device Information

```cisco
hostname EDGE-RTR-01
```

---

## 2. DHCP Configuration

```cisco
ip dhcp excluded-address 192.168.10.1 192.168.10.99
ip dhcp excluded-address 192.168.20.1 192.168.20.99
ip dhcp excluded-address 192.168.30.1 192.168.30.99

ip dhcp pool HR
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
 dns-server 192.168.90.10
 domain-name company.local

ip dhcp pool SALES
 network 192.168.20.0 255.255.255.0
 default-router 192.168.20.1
 dns-server 192.168.90.10
 domain-name company.local

ip dhcp pool DEVELOPMENT
 network 192.168.30.0 255.255.255.0
 default-router 192.168.30.1
 dns-server 192.168.90.10
 domain-name company.local
```

---

## 3. Router-on-a-Stick Configuration

```cisco
interface GigabitEthernet0/0
 no ip address
 duplex auto
 speed auto

interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0

interface GigabitEthernet0/0.30
 encapsulation dot1Q 30
 ip address 192.168.30.1 255.255.255.0

interface GigabitEthernet0/0.90
 encapsulation dot1Q 90
 ip address 192.168.90.1 255.255.255.0
```

---

## 4. VLAN Gateway Summary

| VLAN | Department | Gateway |
|------|------------|---------|
| 10 | HR | 192.168.10.1 |
| 20 | Sales | 192.168.20.1 |
| 30 | Development | 192.168.30.1 |
| 90 | Server | 192.168.90.1 |

---

## 5. Verification Commands

```cisco
show ip interface brief
show ip dhcp binding
show ip dhcp pool
show running-config
```

---

## Summary

- Configured Router-on-a-Stick for Inter-VLAN routing.
- Configured DHCP pools for HR, Sales, and Development VLANs.
- Assigned DNS server information using DHCP.
- Used VLAN 90 as the server network.
