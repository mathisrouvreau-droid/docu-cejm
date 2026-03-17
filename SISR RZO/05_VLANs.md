# 🟣 Fiche – VLANs (Virtual LAN)

## 📌 Concepts de base

| Terme | Description |
|---|---|
| **VLAN** | Segmentation logique d'un réseau sur un switch |
| **Access port** | Port appartenant à **1 seul VLAN** (poste de travail) |
| **Trunk port** | Port transportant **plusieurs VLANs** (entre switches ou vers un routeur) |
| **VLAN natif** | VLAN par défaut sur un trunk (VLAN 1 par défaut) |
| **802.1Q** | Standard d'encapsulation pour les trunks |
| **VTP** | VLAN Trunking Protocol – propagation des VLANs entre switches |

---

## 🔧 Créer des VLANs sur un switch

```
Switch(config)# vlan 10
Switch(config-vlan)# name COMPTA

Switch(config)# vlan 20
Switch(config-vlan)# name INFORMATIQUE

Switch(config)# vlan 30
Switch(config-vlan)# name DIRECTION
```

---

## 🔧 Configurer un port en mode Access

```
Switch(config)# interface FastEthernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
```

---

## 🔧 Configurer un port en mode Trunk

```
Switch(config)# interface GigabitEthernet0/1
Switch(config-if)# switchport mode trunk

! (Optionnel) Autoriser seulement certains VLANs sur le trunk
Switch(config-if)# switchport trunk allowed vlan 10,20,30

! (Optionnel) Modifier le VLAN natif
Switch(config-if)# switchport trunk native vlan 99
```

---

## 🔧 Inter-VLAN Routing – Router-on-a-Stick (1 lien physique)

```
! Sur le switch : trunk vers le routeur
Switch(config)# interface GigabitEthernet0/1
Switch(config-if)# switchport mode trunk

! Sur le routeur : sous-interfaces
Router(config)# interface GigabitEthernet0/0
Router(config-if)# no shutdown

Router(config)# interface GigabitEthernet0/0.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.10.1 255.255.255.0

Router(config)# interface GigabitEthernet0/0.20
Router(config-subif)# encapsulation dot1Q 20
Router(config-subif)# ip address 192.168.20.1 255.255.255.0

Router(config)# interface GigabitEthernet0/0.30
Router(config-subif)# encapsulation dot1Q 30
Router(config-subif)# ip address 192.168.30.1 255.255.255.0
```

> 💡 Le **gateway** de chaque VLAN est l'IP de la sous-interface correspondante.

---

## 🔧 Inter-VLAN Routing – Switch Layer 3 (SVIs)

```
! Activer le routage IP sur le switch L3
Switch(config)# ip routing

! Créer une SVI (Switch Virtual Interface) par VLAN
Switch(config)# interface vlan 10
Switch(config-if)# ip address 192.168.10.1 255.255.255.0
Switch(config-if)# no shutdown

Switch(config)# interface vlan 20
Switch(config-if)# ip address 192.168.20.1 255.255.255.0
Switch(config-if)# no shutdown
```

---

## 🔍 Vérification

```
Switch# show vlan brief
Switch# show interfaces trunk
Switch# show interfaces FastEthernet0/1 switchport
Switch# show mac address-table
```

---

## ⚠️ Points clés à retenir

- Le **VLAN 1** est le VLAN par défaut – éviter de l'utiliser en production
- Un port **access** ne transporte qu'un VLAN, un port **trunk** en transporte plusieurs
- Pour router entre VLANs il faut : soit un **routeur (router-on-a-stick)**, soit un **switch L3**
- Sur Packet Tracer, les switches **2960** sont L2 uniquement → utiliser router-on-a-stick
- Les switches **3560/3750** sont L3 → peuvent faire du routage avec `ip routing`
- La commande `encapsulation dot1Q <vlan-id>` est **obligatoire** sur les sous-interfaces
