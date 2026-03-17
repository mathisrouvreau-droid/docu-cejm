# 🔁 Fiche – NAT / PAT (Cisco IOS)

## 📌 Concepts de base

| Terme | Description |
|---|---|
| **NAT** | Network Address Translation – traduit une IP privée en IP publique (1-to-1) |
| **PAT** | Port Address Translation (NAT overload) – plusieurs IP privées → 1 IP publique via les ports |
| **Inside Local** | IP privée de l'hôte interne |
| **Inside Global** | IP publique vue depuis l'extérieur |
| **Outside Global** | IP du serveur distant |

---

## 🔧 Configuration NAT Statique (1 pour 1)

```
! Définir les interfaces
Router(config)# interface GigabitEthernet0/0
Router(config-if)# ip nat inside

Router(config)# interface GigabitEthernet0/1
Router(config-if)# ip nat outside

! Créer la règle statique
Router(config)# ip nat inside source static 192.168.1.10 203.0.113.5
```

> ✅ Utilisé pour exposer un serveur interne avec une IP publique fixe.

---

## 🔧 Configuration PAT (NAT Overload)

```
! Interfaces
Router(config)# interface GigabitEthernet0/0
Router(config-if)# ip nat inside

Router(config)# interface GigabitEthernet0/1
Router(config-if)# ip nat outside

! Access-list pour définir les hôtes internes
Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255

! NAT overload avec l'IP de l'interface outside
Router(config)# ip nat inside source list 1 interface GigabitEthernet0/1 overload
```

> ✅ C'est le cas le plus courant en entreprise / maison.

---

## 🔧 Configuration NAT Dynamique (pool d'adresses)

```
! Créer un pool d'IPs publiques
Router(config)# ip nat pool MON_POOL 203.0.113.1 203.0.113.10 netmask 255.255.255.0

! ACL des hôtes autorisés
Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255

! Lier l'ACL au pool
Router(config)# ip nat inside source list 1 pool MON_POOL
```

---

## 🔍 Vérification

```
Router# show ip nat translations
Router# show ip nat statistics
Router# debug ip nat
```

---

## ⚠️ Points clés à retenir

- `ip nat inside` → interface côté réseau privé
- `ip nat outside` → interface côté internet/WAN
- Le mot-clé `overload` transforme le NAT en PAT
- Sans `overload`, c'est du NAT dynamique (1-to-1 avec un pool)
- L'ACL utilisée dans NAT est une **ACL standard** (numérotée ou nommée)
