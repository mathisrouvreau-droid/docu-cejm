# 🔵 Fiche – RIP (Routing Information Protocol)

## 📌 Concepts de base

| Terme | Description |
|---|---|
| **Protocole** | Distance-Vector |
| **Versions** | RIPv1 (classful) / RIPv2 (classless, VLSM, MD5) |
| **Métrique** | Nombre de sauts (hop count), max = **15** (16 = inaccessible) |
| **AD** | 120 |
| **Timers** | Update: 30s / Invalid: 180s / Flush: 240s |
| **Multicast RIPv2** | 224.0.0.9 |

---

## 🔧 Configuration RIPv2

```
Router(config)# router rip
Router(config-router)# version 2

! Déclarer les réseaux DIRECTEMENT connectés (adresse de classe, pas CIDR)
Router(config-router)# network 192.168.1.0
Router(config-router)# network 10.0.0.0

! Désactiver la sommation automatique (IMPORTANT avec VLSM)
Router(config-router)# no auto-summary
```

> ⚠️ **`no auto-summary`** est indispensable si vous utilisez des sous-réseaux non contigus ou du VLSM.

---

## 🔧 Interface passive

```
Router(config-router)# passive-interface GigabitEthernet0/0
```

> ✅ Empêche l'envoi de mises à jour RIP sur les interfaces sans voisin RIP (LAN).

---

## 🔧 Route par défaut avec RIP

```
! Créer la route statique par défaut
Router(config)# ip route 0.0.0.0 0.0.0.0 203.0.113.1

! Option 1 : redistribuer dans RIP
Router(config-router)# default-information originate

! Option 2 : créer une route résumée
Router(config-router)# network 0.0.0.0
```

---

## 📋 Différences RIPv1 vs RIPv2

| Caractéristique | RIPv1 | RIPv2 |
|---|---|---|
| Classful/Classless | Classful | Classless |
| Masque envoyé | ❌ Non | ✅ Oui |
| VLSM/CIDR | ❌ Non | ✅ Oui |
| Authentification | ❌ Non | ✅ MD5 |
| Multicast | ❌ (broadcast) | ✅ 224.0.0.9 |

---

## 🔧 Authentification RIPv2 (MD5)

```
! Créer la keychain
Router(config)# key chain MA_KEYCHAIN
Router(config-keychain)# key 1
Router(config-keychain-key)# key-string MON_MOT_DE_PASSE

! Appliquer sur l'interface
Router(config)# interface GigabitEthernet0/0
Router(config-if)# ip rip authentication mode md5
Router(config-if)# ip rip authentication key-chain MA_KEYCHAIN
```

---

## 🔍 Vérification

```
Router# show ip rip database
Router# show ip route rip
Router# show ip protocols
Router# debug ip rip
```

---

## ⚠️ Points clés à retenir

- RIP utilise le **nombre de sauts** comme métrique → pas optimal pour les grands réseaux
- La commande `network` prend l'**adresse de classe** du réseau (pas le sous-réseau exact)
- **`no auto-summary`** est quasi-obligatoire en RIPv2
- Maximum **15 sauts** → inutilisable dans les grandes topologies
- RIPv1 envoie en **broadcast**, RIPv2 en **multicast**
- Convergence lente comparée à OSPF
