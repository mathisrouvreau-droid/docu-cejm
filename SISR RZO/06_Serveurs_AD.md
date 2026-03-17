# 🖥️ Fiche – Active Directory & Serveurs sur Packet Tracer

## 📌 Serveurs disponibles dans Packet Tracer

| Service | Port | Utilité |
|---|---|---|
| **DNS** | 53 UDP/TCP | Résolution de noms |
| **DHCP** | 67/68 UDP | Attribution automatique d'IP |
| **HTTP/HTTPS** | 80 / 443 | Serveur web |
| **FTP** | 21 | Transfert de fichiers |
| **TFTP** | 69 UDP | Transfert simplifié |
| **Active Directory** | – | Authentification centralisée (simulé) |
| **NTP** | 123 UDP | Synchronisation d'horloge |

---

## 🔧 Configurer un serveur DNS

1. Cliquer sur le **serveur** → onglet **Services** → **DNS**
2. Activer le service : **ON**
3. Ajouter des entrées :
   - **Name** : `www.monsite.com`
   - **Type** : `A Record`
   - **Address** : `192.168.1.100`
4. Cliquer **Add**

> 💡 Les postes clients doivent avoir l'IP du serveur DNS configurée dans leur passerelle ou DHCP.

---

## 🔧 Configurer un serveur DHCP

1. Cliquer sur le **serveur** → **Services** → **DHCP**
2. Activer : **ON**
3. Remplir les champs :
   - **Pool Name** : `LAN_POOL`
   - **Default Gateway** : `192.168.1.1`
   - **DNS Server** : `192.168.1.50`
   - **Start IP Address** : `192.168.1.100`
   - **Subnet Mask** : `255.255.255.0`
   - **Max Number of Users** : ex. `50`
4. Cliquer **Add**

Sur les postes clients → **Desktop** → **IP Configuration** → cocher **DHCP**

---

## 🔧 Configurer Active Directory (simulé)

Packet Tracer simule un service AD basique :

1. Cliquer sur le **serveur** → **Services** → **AAA** ou **Active Directory** (selon version)
2. Activer le service
3. Créer des utilisateurs :
   - **Username** : `jean.dupont`
   - **Password** : `Azerty123`
4. Cliquer **Add**

### Connexion d'un PC au domaine (Packet Tracer)

1. Sur le PC → **Desktop** → **Active Directory** (si disponible)
2. Entrer le **nom de domaine** et les **credentials administrateur**
3. Rejoindre le domaine

---

## 🔧 Configurer un serveur HTTP

1. **Services** → **HTTP**
2. Activer : **ON**
3. Le fichier `index.html` par défaut est déjà présent
4. Modifier le contenu HTML si besoin

Test depuis un PC : **Desktop** → **Web Browser** → entrer l'IP du serveur

---

## 🔧 Configurer un serveur NTP

1. **Services** → **NTP**
2. Activer : **ON**
3. Configurer les routeurs pour utiliser ce NTP :

```
Router(config)# ntp server 192.168.1.50
```

---

## 📋 Schéma type : Réseau avec serveurs

```
Internet
    |
  Routeur (NAT/PAT)
    |
  Switch L2/L3
  /    |    \
LAN  Serveur  Serveur
PC   DNS/DHCP  AD/HTTP
```

---

## 🔧 Adressage d'un serveur

1. Cliquer sur le **serveur** → **Desktop** → **IP Configuration**
2. Choisir **Static**
3. Remplir :
   - IP Address : `192.168.1.50`
   - Subnet Mask : `255.255.255.0`
   - Default Gateway : `192.168.1.1`
   - DNS Server : `192.168.1.50` (lui-même si c'est le DNS)

---

## 🔍 Tests de connectivité

```
! Depuis le PC (Command Prompt)
C:\> ping 192.168.1.50          ! tester la connectivité
C:\> nslookup www.monsite.com   ! tester la résolution DNS
C:\> ipconfig /all              ! vérifier l'adressage DHCP
```

---

## ⚠️ Points clés à retenir

- Dans Packet Tracer, AD est **simulé** : pas de GPO, pas de vraie intégration
- Le serveur doit avoir une **IP statique** (surtout DNS/DHCP/AD)
- Le serveur DHCP doit être **accessible** depuis les clients (même VLAN ou relay agent configuré)
- **IP Helper Address** : si le DHCP est sur un autre sous-réseau :

```
Router(config-if)# ip helper-address 192.168.1.50
```

- Un serveur DNS local permet d'utiliser des noms au lieu des IPs dans les navigateurs
