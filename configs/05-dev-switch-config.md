# Dev-SW01 Configuration

> Cisco Catalyst 2960 Switch  
> Cisco Enterprise Network Lab

---

## 1. Device Information

```cisco
hostname Dev-SW01
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
```

---

## 3. Trunk Port Configuration

```cisco
interface FastEthernet0/1
 switchport mode trunk

interface GigabitEthernet0/1
 switchport mode trunk
```

---

## 4. Access Port Configuration

```cisco
interface FastEthernet0/2
 switchport mode access
 switchport access vlan 30

interface FastEthernet0/3
 switchport mode access
 switchport access vlan 30
```

---

## 5. Spanning Tree

```cisco
spanning-tree mode pvst
spanning-tree extend system-id
```

---

## 6. Verification Commands

```cisco
show vlan brief
show interfaces trunk
show running-config
```

---

## Summary

- Configured Development department access switch.
- Assigned client devices to VLAN 30.
- Connected to the Core Switch using trunk links.
- Enabled PVST for loop prevention.
