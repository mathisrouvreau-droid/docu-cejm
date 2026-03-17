# 🟠 Fiche – OSPF (Open Shortest Path First)

## 📌 Concepts de base

| Terme | Description |
|---|---|
| **Protocole** | Link-State, standard ouvert (RFC 2328) |
| **Algorithme** | Dijkstra (SPF) |
| **Métrique** | Coût = 100 Mbps / bande passante de l'interface |
| **AD (Distance Admin.)** | 110 |
| **Multicast** | 224.0.0.5 (tous routeurs OSPF) / 224.0.0.6 (DR/BDR) |
| **Process ID** | Local au routeur, n'a pas besoin d'être identique sur tous les routeurs |

---

## 🔧 Configuration OSPF de base (single area)

```
Router(config)# router ospf 1

! Déclarer les réseaux connectés (avec wildcard + area)
Router(config-router)# network 192.168.1.0 0.0.0.255 area 0
Router(config-router)# network 10.0.0.0 0.0.0.3 area 0

! (Optionnel) Définir le Router-ID manuellement
Router(config-router)# router-id 1.1.1.1
```

> 🔑 **Area 0** = backbone area, obligatoire dans tout réseau OSPF.

---

## 🔧 Route par défaut avec OSPF

```
! Configurer une route statique par défaut
Router(config)# ip route 0.0.0.0 0.0.0.0 203.0.113.1

! Redistribuer cette route dans OSPF
Router(config-router)# default-information originate
```

---

## 🔧 Interface passive (ne pas envoyer de Hello sur les LAN)

```
Router(config-router)# passive-interface GigabitEthernet0/0
```

> ✅ À utiliser sur les interfaces connectées à des LAN (pas de voisin OSPF dessus).

---

## 📋 États de voisinage OSPF (Adjacency States)

```
Down → Init → 2-Way → Exstart → Exchange → Loading → Full
```

| État | Signification |
|---|---|
| **Down** | Aucun Hello reçu |
| **Init** | Hello reçu, pas encore bidirectionnel |
| **2-Way** | Bidirectionnel – élection DR/BDR possible |
| **Full** | Synchronisation complète (base de données identique) |

---

## 📋 DR / BDR (sur les réseaux multi-accès comme Ethernet)

- **DR** (Designated Router) : collecte et distribue les LSA
- **BDR** (Backup DR) : prend le relais si DR tombe
- Élection basée sur : **priorité** (0–255, défaut=1) puis **Router-ID**
- Priorité 0 = ne peut pas être élu DR/BDR

```
Router(config-if)# ip ospf priority 100    ! forcer l'élection comme DR
```

---

## 🔍 Vérification

```
Router# show ip ospf neighbor
Router# show ip ospf
Router# show ip route ospf
Router# show ip ospf interface
Router# debug ip ospf events
```

---

## ⚠️ Points clés à retenir

- Le **Process ID** (ex: `router ospf 1`) est **local**, pas besoin de correspondre
- La commande `network` utilise un **wildcard mask**, pas un masque de sous-réseau
- OSPF forme des **adjacences** (Full) seulement avec DR/BDR sur Ethernet
- Le **Router-ID** est choisi : ID configuré manuellement > IP la plus haute d'une loopback > IP la plus haute des interfaces actives
- Toutes les areas doivent être **connectées à l'area 0**
