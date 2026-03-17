# 📋 Mémo Rapide – Packet Tracer Éval

## ⚡ Commandes essentielles à connaître par cœur

### NAT / PAT
```
ip nat inside / ip nat outside
ip nat inside source static <IP_priv> <IP_pub>
ip nat inside source list <ACL> interface <int> overload   ! PAT
show ip nat translations
```

### ACL
```
access-list 10 permit 192.168.1.0 0.0.0.255              ! Standard
access-list 100 deny tcp <src> <wild> <dst> <wild> eq 80  ! Étendue
ip access-list standard NOM / ip access-list extended NOM  ! Nommée
ip access-group <nom/num> in|out                          ! Appliquer
show access-lists
```

### OSPF
```
router ospf 1
 router-id 1.1.1.1
 network <réseau> <wildcard> area 0
 passive-interface <int>
 default-information originate
show ip ospf neighbor
show ip route ospf
```

### RIP
```
router rip
 version 2
 no auto-summary
 network <réseau_classe>
 passive-interface <int>
 default-information originate
show ip route rip
show ip protocols
```

### VLANs
```
vlan 10 / name NOM                                         ! Créer
switchport mode access / switchport access vlan 10         ! Access
switchport mode trunk / switchport trunk allowed vlan 10,20! Trunk
interface Gi0/0.10 / encapsulation dot1Q 10 / ip address   ! Router-on-stick
ip routing                                                  ! Switch L3
show vlan brief
show interfaces trunk
```

### Serveurs
```
! IP Helper (relay DHCP)
interface <int>
 ip helper-address <IP_serveur_DHCP>

! NTP
ntp server <IP>
```

---

## 📍 Règles de placement ACL

```
Standard  →  proche de la DESTINATION
Étendue   →  proche de la SOURCE
```

## 📍 Wildcards rapides

```
/24  →  0.0.0.255
/16  →  0.0.255.255
/8   →  0.255.255.255
host →  0.0.0.0  (ou mot-clé "host")
any  →  255.255.255.255  (ou mot-clé "any")
```

## 📍 Métriques & AD

| Protocole | AD | Métrique |
|---|---|---|
| Directement connecté | 0 | – |
| Statique | 1 | – |
| OSPF | 110 | Coût (100M/BW) |
| RIP | 120 | Hop count (max 15) |

## 📍 Check-list avant de soumettre

- [ ] Toutes les interfaces sont en `no shutdown`
- [ ] Les IPs sont correctement configurées (y compris les serveurs)
- [ ] Les passerelles par défaut sont configurées sur les PCs
- [ ] Les ACL ont bien un `permit ip any any` ou `permit any` si nécessaire
- [ ] NAT : `ip nat inside` ET `ip nat outside` sont bien positionnés
- [ ] OSPF/RIP : `network` déclaré pour **tous** les réseaux
- [ ] VLANs : trunk entre switches, access sur les postes
- [ ] Test ping entre tous les segments
- [ ] Test depuis un PC vers Internet si NAT configuré
