# Core-SW01 Configuration

> Cisco Catalyst 2960 Switch  
> Cisco Enterprise Network Lab

---

## 1. Device Information

```cisco
hostname Core-SW01
vtp mode transparent
```

---

## 2. VLAN Configuration

```cisco
vlan 10
 name HR

vlan 20
 name SALES

vlan 30
 name DEVELOPMENT

vlan 90
 name SERVER
```

---

## 3. Trunk Port Configuration

```cisco
interface FastEthernet0/1
 switchport mode trunk

interface FastEthernet0/2
 switchport mode trunk

interface FastEthernet0/3
 switchport mode trunk

interface FastEthernet0/4
 switchport mode trunk

interface GigabitEthernet0/1
 switchport mode trunk

interface GigabitEthernet0/2
 switchport mode trunk
```

> **Note**
>
> Remaining FastEthernet interfaces are also configured as trunk ports for VLAN traffic forwarding.

---

## 4. Server Access Port

```cisco
interface FastEthernet0/5
 switchport mode access
 switchport access vlan 90
```

---

## 5. Spanning Tree

```cisco
spanning-tree mode pvst
spanning-tree extend system-id
```

---

## 6. VLAN Summary

| VLAN | Department |
|------|------------|
| 10 | HR |
| 20 | Sales |
| 30 | Development |
| 90 | Server |

---

## 7. Verification Commands

```cisco
show vlan brief
show interfaces trunk
show spanning-tree
show running-config
```

---

## Summary

- Configured Core Switch as the central Layer 2 switch.
- Created VLANs for HR, Sales, Development, and Server departments.
- Configured trunk links to carry multiple VLANs.
- Configured an access port for the internal server.
- Enabled PVST for loop prevention.
