# 🛡️ Fiche – ACL (Access Control Lists)

## 📌 Types d'ACL

| Type | Numéros | Filtre sur |
|---|---|---|
| **Standard** | 1–99 / 1300–1999 | IP source uniquement |
| **Étendue** | 100–199 / 2000–2699 | IP src/dst, protocole, port |
| **Nommée** | Nom texte | Standard ou étendue, plus lisible |

> 📍 **Règle de placement :**
> - ACL **standard** → placer **le plus près de la destination**
> - ACL **étendue** → placer **le plus près de la source**

---

## 🔧 ACL Standard Numérotée

```
! Autoriser seulement le réseau 192.168.1.0/24
Router(config)# access-list 10 permit 192.168.1.0 0.0.0.255
Router(config)# access-list 10 deny any

! Appliquer sur une interface (filtre le trafic entrant)
Router(config)# interface GigabitEthernet0/1
Router(config-if)# ip access-group 10 out
```

---

## 🔧 ACL Standard Nommée

```
Router(config)# ip access-list standard AUTORISER_LAN
Router(config-std-nacl)# permit 192.168.1.0 0.0.0.255
Router(config-std-nacl)# deny any

! Appliquer
Router(config)# interface GigabitEthernet0/1
Router(config-if)# ip access-group AUTORISER_LAN out
```

---

## 🔧 ACL Étendue Numérotée

```
! Bloquer HTTP depuis 192.168.1.0 vers 10.0.0.0
Router(config)# access-list 100 deny tcp 192.168.1.0 0.0.0.255 10.0.0.0 0.0.0.255 eq 80
Router(config)# access-list 100 permit ip any any

! Appliquer en entrée sur l'interface source
Router(config)# interface GigabitEthernet0/0
Router(config-if)# ip access-group 100 in
```

---

## 🔧 ACL Étendue Nommée

```
Router(config)# ip access-list extended BLOQUER_HTTP
Router(config-ext-nacl)# deny tcp 192.168.1.0 0.0.0.255 host 10.0.0.1 eq 80
Router(config-ext-nacl)# permit ip any any

Router(config)# interface GigabitEthernet0/0
Router(config-if)# ip access-group BLOQUER_HTTP in
```

---

## 📋 Mots-clés protocoles / ports courants

| Mot-clé | Protocole/Port |
|---|---|
| `tcp` | TCP |
| `udp` | UDP |
| `icmp` | Ping |
| `ip` | Tout IP |
| `eq 80` | HTTP |
| `eq 443` | HTTPS |
| `eq 23` | Telnet |
| `eq 22` | SSH |
| `eq 53` | DNS |

---

## 📋 Wildcards courants

| Masque réseau | Wildcard |
|---|---|
| 255.255.255.0 (/24) | 0.0.0.255 |
| 255.255.0.0 (/16) | 0.0.255.255 |
| 255.255.255.255 (host) | 0.0.0.0 |
| 0.0.0.0 (any) | 255.255.255.255 |

> 💡 Raccourcis : `host 10.0.0.1` = `10.0.0.1 0.0.0.0` | `any` = `0.0.0.0 255.255.255.255`

---

## 🔍 Vérification

```
Router# show access-lists
Router# show ip interface GigabitEthernet0/0
```

---

## ⚠️ Points clés à retenir

- Il y a un **`deny any` implicite** à la fin de chaque ACL
- L'ordre des règles **compte** : la première correspondance gagne
- Une ACL peut être appliquée `in` (entrant) ou `out` (sortant) sur une interface
- Maximum **1 ACL par interface, par direction, par protocole**
- Les ACL nommées permettent de **supprimer des lignes individuelles** (`no permit ...`)
