**RÉVISIONS COMPLÈTES**

**BTS SIO --- Option SISR**

*Cours • Avantages & Inconvénients • Questions types d\'examen*

+-----------------------------------------------------------------------+
| **13 Notions couvertes**                                              |
|                                                                       |
| PowerShell • RAID • HTTPS • SSH • IDS / IPS                           |
|                                                                       |
| Homme du Milieu • ITIL • Sauvegardes & Restaurations                  |
|                                                                       |
| Force Brute & Dictionnaire • Cyberattaques • Chiffrement              |
|                                                                       |
| Disponibilité • Multisites                                            |
|                                                                       |
| *Pour chaque notion : Cours théorique → Avantages/Inconvénients → 5   |
| questions types d\'examen*                                            |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **📌 Comment utiliser ce document ?**                                 |
+-----------------------------------------------------------------------+
| Chaque notion est structurée en 3 parties : (1) le cours complet avec |
| définitions et tableaux, (2) les avantages et inconvénients à         |
| mémoriser, (3) 5 questions types formulées comme dans les vrais       |
| sujets BTS SIO SISR.                                                  |
|                                                                       |
| Les indications en italique sous chaque question orientent vers la    |
| réponse attendue --- essayez de répondre sans les lire d\'abord !     |
+-----------------------------------------------------------------------+

> **1. PowerShell**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**▶ Définition**

PowerShell est un shell en ligne de commande et un langage de script
développé par Microsoft. Il est basé sur le framework .NET et permet
d\'automatiser l\'administration des systèmes Windows (et Linux depuis
PowerShell Core).

**▶ Caractéristiques clés**

-   **Cmdlets :** Commandes natives de PowerShell au format Verbe-Nom
    (ex : Get-Service, Set-Item)

-   **Pipeline (\|) :** Enchaîner des commandes pour passer les objets
    d\'une commande à l\'autre

-   **Scripts .ps1 :** Fichiers de scripts PowerShell exécutables

-   **Objets .NET :** Contrairement au bash, PowerShell manipule des
    objets structurés, pas juste du texte

-   **ISE / VS Code :** Environnements de développement pour écrire des
    scripts

**▶ Commandes essentielles**

  ----------------------------------- -----------------------------------
  **Commande**                        **Description**

  **Get-Help \<cmd\>**                Affiche l\'aide d\'une commande

  **Get-Service**                     Liste les services Windows

  **Start/Stop-Service**              Démarrer/arrêter un service

  **Get-Process**                     Liste les processus en cours

  **Get-EventLog**                    Consulter les journaux
                                      d\'événements

  **New-Item**                        Créer un fichier ou dossier

  **Copy-Item / Move-Item**           Copier / déplacer des fichiers

  **Get-ADUser**                      Gestion Active Directory (module
                                      RSAT)

  **Invoke-Command**                  Exécuter des commandes sur un PC
                                      distant

  **Set-ExecutionPolicy**             Définir la politique d\'exécution
                                      des scripts
  ----------------------------------- -----------------------------------

+-----------------------------------------------------------------------+
| **⚠️ ExecutionPolicy --- À retenir**                                  |
+-----------------------------------------------------------------------+
| -   **Restricted :** Aucun script n\'est autorisé (par défaut)        |
|                                                                       |
| -   **RemoteSigned :** Les scripts locaux s\'exécutent, les distants  |
|     doivent être signés                                               |
|                                                                       |
| -   **Unrestricted :** Tous les scripts s\'exécutent (risque          |
|     sécurité)                                                         |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** Automatisation puissante : remplace des tâches manuelles        |
| répétitives (création de comptes AD, déploiement\...)                 |
|                                                                       |
| **✓** Intégration native avec Windows et l\'écosystème Microsoft (AD, |
| Exchange, Azure, Office 365)                                          |
|                                                                       |
| **✓** Manipulation d\'objets .NET : résultats structurés et           |
| filtrables, pas juste du texte                                        |
|                                                                       |
| **✓** Multiplateforme depuis PowerShell Core (fonctionne aussi sur    |
| Linux et macOS)                                                       |
|                                                                       |
| **✓** Télégestion : Invoke-Command permet d\'exécuter des commandes   |
| sur des dizaines de serveurs en même temps                            |
|                                                                       |
| **✓** Traçabilité : les scripts sont auditables, documentables et     |
| reproductibles                                                        |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** Courbe d\'apprentissage initiale, surtout la syntaxe des objets |
| et pipelines                                                          |
|                                                                       |
| **✗** Politique d\'exécution restrictive par défaut : les scripts ne  |
| s\'exécutent pas sans configuration préalable                         |
|                                                                       |
| **✗** Risque de sécurité si mal sécurisé (scripts malveillants, accès |
| distants non contrôlés)                                               |
|                                                                       |
| **✗** Moins adapté que bash pour les environnements Linux purs        |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** L\'entreprise Dupont SA souhaite automatiser la création de   |
| 50 comptes utilisateurs dans Active Directory à partir d\'un fichier  |
| CSV. Quel outil et quelle commande PowerShell utiliseriez-vous ?      |
| Justifiez votre choix.                                                |
|                                                                       |
| > *→ Import-Csv + New-ADUser en boucle foreach. Mentionner le module  |
| > ActiveDirectory (RSAT).*                                            |
+-----------------------------------------------------------------------+
| **Q2.** Un technicien souhaite exécuter un script PowerShell (.ps1)   |
| sur un serveur Windows Server 2022 mais obtient l\'erreur : «         |
| L\'exécution de scripts est désactivée sur ce système ». Quelle est   |
| la cause et comment y remédier ?                                      |
|                                                                       |
| > *→ ExecutionPolicy Restricted par défaut → Set-ExecutionPolicy      |
| > RemoteSigned. Expliquer les niveaux.*                               |
+-----------------------------------------------------------------------+
| **Q3.** Vous devez vérifier à distance l\'état des services sur 10    |
| serveurs de l\'entreprise. Quelle commande PowerShell utilisez-vous ? |
| Quels prérequis réseau sont nécessaires ?                             |
|                                                                       |
| > *→ Invoke-Command -ComputerName + Get-Service. Prérequis : WinRM    |
| > activé, pare-feu, droits admin distants.*                           |
+-----------------------------------------------------------------------+
| **Q4.** Expliquez la différence entre PowerShell et l\'invite de      |
| commandes Windows (cmd.exe). Dans quel cas choisiriez-vous l\'un      |
| plutôt que l\'autre ?                                                 |
|                                                                       |
| > *→ PowerShell = objets .NET, cmdlets, scripting avancé. CMD =       |
| > commandes simples, compatibilité ancienne.*                         |
+-----------------------------------------------------------------------+
| **Q5.** Dans le cadre d\'un audit de sécurité, on vous demande de     |
| lister tous les comptes locaux administrateurs de 20 postes de        |
| travail. Proposez une solution PowerShell.                            |
|                                                                       |
| > *→ Invoke-Command + Get-LocalGroupMember \'Administrators\'. Export |
| > vers CSV avec Export-Csv.*                                          |
+-----------------------------------------------------------------------+

> **2. RAID (Redundant Array of Independent Disks)**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**▶ Définition**

Le RAID est une technologie permettant de combiner plusieurs disques
durs physiques en un seul volume logique, dans le but d\'améliorer les
performances, la redondance (tolérance aux pannes) ou les deux.

**▶ Les niveaux de RAID principaux**

  ----------------------------------- -----------------------------------
  **Niveau**                          **Description**

  **RAID 0 --- Striping**             Données réparties sur 2+ disques.
                                      Performances maximales. Aucune
                                      redondance : si 1 disque tombe,
                                      tout est perdu. Usage :
                                      performances.

  **RAID 1 --- Mirroring**            Données dupliquées sur 2 disques
                                      identiques. Tolérance : 1 disque
                                      peut tomber. Capacité utile = 1
                                      seul disque. Usage : données
                                      critiques.

  **RAID 5 --- Striping + parité**    Données + parité réparties sur 3+
                                      disques. Tolérance : 1 disque en
                                      panne. Bonne solution équilibrée.
                                      Capacité = (N-1) disques.

  **RAID 6 --- Double parité**        Comme RAID 5 mais 2 disques de
                                      parité. Tolérance : 2 disques en
                                      panne. Nécessite 4+ disques.

  **RAID 10 (1+0)**                   Miroir de stripes. Combine RAID 1
                                      et RAID 0. Hautes performances +
                                      tolérance aux pannes. Nécessite 4+
                                      disques.
  ----------------------------------- -----------------------------------

+-----------------------------------------------------------------------+
| **📊 Comparatif rapide**                                              |
+-----------------------------------------------------------------------+
|   --------------------------------- --------------------------------- |
|   **Critère**                       RAID 1 \| RAID 5 \| RAID 10       |
|                                                                       |
|   **Disques min.**                  2 \| 3 \| 4                       |
|                                                                       |
|   **Tolérance pannes**              1 disque \| 1 disque \| 1 par     |
|                                     miroir                            |
|                                                                       |
|   **Perf. lecture**                 Bonne \| Très bonne \| Excellente |
|                                                                       |
|   **Perf. écriture**                Normale \| Ralentie (parité) \|   |
|                                     Excellente                        |
|                                                                       |
|   **Coût**                          Moyen \| Bon \| Élevé             |
|   --------------------------------- --------------------------------- |
+-----------------------------------------------------------------------+

-   **RAID matériel :** Contrôleur RAID dédié --- plus performant,
    transparent pour l\'OS

-   **RAID logiciel :** Géré par l\'OS (ex : Windows Storage Spaces,
    mdadm Linux) --- moins performant

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** RAID 1 : tolérance aux pannes immédiate, restauration           |
| transparente, lecture rapide (en parallèle sur les deux disques)      |
|                                                                       |
| **✓** RAID 5 : bon compromis entre capacité, performance et           |
| redondance pour les serveurs de fichiers                              |
|                                                                       |
| **✓** RAID 10 : meilleures performances en lecture ET écriture        |
| combinées à une haute tolérance aux pannes                            |
|                                                                       |
| **✓** RAID matériel : performances optimales, transparent pour l\'OS, |
| cache intégré avec batterie de secours                                |
|                                                                       |
| **✓** Continuité de service : en cas de panne d\'un disque, le        |
| système continue de fonctionner sans interruption                     |
|                                                                       |
| **✓** Hot spare : disque de rechange à chaud qui reconstruit          |
| automatiquement le RAID en cas de panne                               |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** RAID 0 : aucune tolérance --- perte totale si 1 disque tombe    |
|                                                                       |
| **✗** RAID 5 : vulnérable lors de la reconstruction (si un 2e disque  |
| tombe pendant la reconstruction = perte totale)                       |
|                                                                       |
| **✗** Le RAID n\'est PAS une sauvegarde : une suppression             |
| accidentelle ou un ransomware affecte tous les disques                |
|                                                                       |
| **✗** RAID 5/6 : pénalité en écriture due au calcul de parité         |
|                                                                       |
| **✗** Coût : RAID 10 nécessite 2x plus de disques que la capacité     |
| utile                                                                 |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** L\'entreprise dispose d\'un serveur de fichiers avec 4        |
| disques de 2 To. Le responsable souhaite maximiser la disponibilité   |
| et les performances. Quel niveau RAID recommandez-vous ? Calculez la  |
| capacité utile.                                                       |
|                                                                       |
| > *→ RAID 10 → 4 To utiles (50% de 8 To). Justifier : 1 panne par     |
| > miroir tolérée, meilleures perfs.*                                  |
+-----------------------------------------------------------------------+
| **Q2.** Un disque tombe en panne dans un RAID 5 composé de 3 disques  |
| de 1 To. Quelles sont les conséquences immédiates ? Que risque-t-il   |
| si un deuxième disque tombe avant la reconstruction ?                 |
|                                                                       |
| > *→ Fonctionnement dégradé (lecture reconstruite à la volée), pertes |
| > de performances. Si 2e panne → perte totale.*                       |
+-----------------------------------------------------------------------+
| **Q3.** Un client vous dit : « J\'ai mis en place du RAID 1, donc mes |
| données sont sauvegardées ». Que lui répondez-vous ? Que lui          |
| recommandez-vous en complément ?                                      |
|                                                                       |
| > *→ RAID ≠ sauvegarde. Ne protège pas contre suppression,            |
| > ransomware, vol. Recommander sauvegarde 3-2-1 en complément.*       |
+-----------------------------------------------------------------------+
| **Q4.** Comparez RAID 5 et RAID 6. Dans quel contexte choisiriez-vous |
| RAID 6 plutôt que RAID 5 ?                                            |
|                                                                       |
| > *→ RAID 6 = 2 disques de parité, tolère 2 pannes. Choisir quand     |
| > disques volumineux (\>4 To) car reconstruction longue = risque.*    |
+-----------------------------------------------------------------------+
| **Q5.** Quelle est la différence entre RAID matériel et RAID logiciel |
| ? Lequel préconisez-vous pour un serveur de production ? Justifiez.   |
|                                                                       |
| > *→ RAID matériel = contrôleur dédié, cache, meilleure perf,         |
| > transparent pour l\'OS. Recommandé en production.*                  |
+-----------------------------------------------------------------------+

> **3. HTTPS (HyperText Transfer Protocol Secure)**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**▶ Définition**

HTTPS est la version sécurisée du protocole HTTP. Il utilise TLS
(Transport Layer Security) pour chiffrer les communications entre le
client (navigateur) et le serveur web. Port par défaut : 443.

**▶ Fonctionnement TLS**

-   **1. Handshake TLS :** Le client et le serveur négocient les
    algorithmes de chiffrement et s\'authentifient via un certificat
    numérique.

-   **2. Échange de clés :** Une clé de session symétrique est générée
    pour chiffrer les données échangées.

-   **3. Communication chiffrée :** Toutes les données sont chiffrées
    --- données et mots de passe sont illisibles en clair sur le réseau.

**▶ Types de certificats SSL/TLS**

  ----------------------------------- -----------------------------------
  **Type**                            **Description**

  **CA (Certificate Authority)**      Autorité de certification qui signe
                                      les certificats (Let\'s Encrypt,
                                      DigiCert\...)

  **Certificat DV**                   Domain Validation --- vérifie
                                      uniquement le domaine. Rapide et
                                      gratuit (Let\'s Encrypt).

  **Certificat OV**                   Organization Validation --- vérifie
                                      l\'organisation. Plus de confiance.

  **Certificat EV**                   Extended Validation --- nom de
                                      l\'entreprise visible. Très haute
                                      confiance.

  **Certificat auto-signé**           Signé par soi-même, non reconnu
                                      publiquement. Usage interne
                                      uniquement.
  ----------------------------------- -----------------------------------

+-----------------------------------------------------------------------+
| **⚠️ HTTP vs HTTPS**                                                  |
+-----------------------------------------------------------------------+
| -   **HTTP :** Données en clair, port 80, vulnérable aux écoutes et   |
|     attaques homme du milieu                                          |
|                                                                       |
| -   **HTTPS :** Données chiffrées, port 443, authentification du      |
|     serveur via certificat, intégrité garantie                        |
|                                                                       |
| Un cadenas dans le navigateur = HTTPS actif. Attention : un site      |
| phishing peut aussi avoir un certificat HTTPS valide !                |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** Chiffrement de bout en bout : les données échangées sont        |
| illisibles pour un tiers qui intercepterait le trafic                 |
|                                                                       |
| **✓** Authentification du serveur : le certificat garantit que vous   |
| communiquez avec le bon serveur                                       |
|                                                                       |
| **✓** Intégrité des données : TLS garantit que les données n\'ont pas |
| été modifiées en transit                                              |
|                                                                       |
| **✓** SEO : Google favorise les sites HTTPS dans son classement       |
|                                                                       |
| **✓** Gratuit avec Let\'s Encrypt : les certificats DV sont désormais |
| disponibles gratuitement et auto-renouvelables                        |
|                                                                       |
| **✓** Protection contre l\'injection de contenu par des               |
| intermédiaires (FAI, proxy malveillant)                               |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** Légère surcharge de traitement (chiffrement/déchiffrement) ---  |
| négligeable avec le matériel moderne                                  |
|                                                                       |
| **✗** Certificats payants pour OV/EV, gestion du renouvellement à     |
| automatiser                                                           |
|                                                                       |
| **✗** Un certificat valide ne garantit PAS que le site est légitime   |
| (site phishing peut avoir HTTPS)                                      |
|                                                                       |
| **✗** Configuration incorrecte (TLS 1.0/1.1, cipher suites faibles)   |
| rend HTTPS moins sécurisé                                             |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** L\'entreprise met en place un portail web interne pour les    |
| employés. Le DSI vous demande de sécuriser les accès en HTTPS.        |
| Décrivez les étapes de mise en œuvre sur un serveur Apache/Nginx.     |
|                                                                       |
| > *→ Obtenir certificat (Let\'s Encrypt ou CA interne), configurer    |
| > virtual host SSL, port 443, rediriger HTTP→HTTPS, configurer HSTS.* |
+-----------------------------------------------------------------------+
| **Q2.** Un utilisateur constate que le site de sa banque affiche un   |
| cadenas vert mais remarque que l\'URL est \'www.cr-agricoIe.fr\' (I   |
| majuscule à la place du l). Quelle attaque est en cours ? Comment     |
| l\'utilisateur aurait-il pu s\'en prémunir ?                          |
|                                                                       |
| > *→ Attaque homographe / typosquatting. Le certificat HTTPS ne       |
| > garantit pas la légitimité du site. Vérifier l\'URL attentivement,  |
| > utiliser les favoris.*                                              |
+-----------------------------------------------------------------------+
| **Q3.** Expliquez le mécanisme de handshake TLS. Quels éléments sont  |
| négociés lors de cette phase ?                                        |
|                                                                       |
| > *→ Version TLS, suite cryptographique (cipher suite), échange de    |
| > clés (DH/ECDH), authentification par certificat, génération clé de  |
| > session.*                                                           |
+-----------------------------------------------------------------------+
| **Q4.** Quelle est la différence entre un certificat SSL auto-signé   |
| et un certificat signé par une CA reconnue ? Dans quel contexte       |
| utilise-t-on chacun ?                                                 |
|                                                                       |
| > *→ Auto-signé : pas de tiers de confiance, avertissement            |
| > navigateur, usage interne uniquement. CA reconnue : confiance       |
| > publique, sites externes.*                                          |
+-----------------------------------------------------------------------+
| **Q5.** L\'entreprise constate que son site web tourne encore sous    |
| TLS 1.0. Quels sont les risques ? Que recommandez-vous ?              |
|                                                                       |
| > *→ TLS 1.0/1.1 vulnérables (POODLE, BEAST). Migrer vers TLS 1.2     |
| > minimum, idéalement TLS 1.3. Désactiver les vieux cipher suites.*   |
+-----------------------------------------------------------------------+

> **4. SSH (Secure Shell)**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**▶ Définition**

SSH est un protocole réseau cryptographique permettant de se connecter à
distance à un serveur de façon sécurisée. Il remplace Telnet (non
chiffré). Port par défaut : 22.

**▶ Fonctionnalités**

-   **Connexion distante sécurisée :** Accès à un terminal distant
    (console Linux, équipements réseau Cisco\...)

-   **Transfert de fichiers :** SCP (Secure Copy) et SFTP (SSH File
    Transfer Protocol)

-   **Tunneling :** Redirection de ports pour sécuriser d\'autres
    protocoles

-   **Authentification par clé :** Paire clé publique/privée --- plus
    sécurisé que le mot de passe

**▶ Authentification par clé SSH**

1\. Générer une paire de clés sur le client : ssh-keygen

2\. Copier la clé publique sur le serveur : ssh-copy-id user@serveur

3\. La clé privée reste sur le client, ne quitte jamais la machine

  ----------------------------------- -----------------------------------
  **Commande**                        **Usage**

  **ssh user@ip**                     Connexion SSH basique

  **ssh -p 2222 user@ip**             Connexion sur un port non standard

  **ssh -i clé.pem user@ip**          Connexion avec fichier de clé
                                      privée

  **scp fichier user@ip:/chemin**     Copier un fichier vers un serveur
                                      distant

  **sftp user@ip**                    Session de transfert de fichiers
                                      interactive
  ----------------------------------- -----------------------------------

+-----------------------------------------------------------------------+
| **🔐 Bonnes pratiques SSH**                                           |
+-----------------------------------------------------------------------+
| -   **Changer le port par défaut :** Remplacer 22 par un autre port   |
|     (ex : 2222) pour réduire les scans automatiques                   |
|                                                                       |
| -   **Désactiver root login :** PermitRootLogin no dans sshd_config   |
|                                                                       |
| -   **Utiliser les clés :** Désactiver l\'auth par mot de passe       |
|     (PasswordAuthentication no)                                       |
|                                                                       |
| -   **Fail2Ban :** Bloquer automatiquement les IP après trop de       |
|     tentatives échouées                                               |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** Sécurité totale : toutes les communications sont chiffrées      |
| (contrairement à Telnet ou FTP en clair)                              |
|                                                                       |
| **✓** Authentification forte par clé : beaucoup plus sécurisée que    |
| les mots de passe seuls                                               |
|                                                                       |
| **✓** Multiusage : accès distant, transfert de fichiers (SCP/SFTP),   |
| tunneling, X11 forwarding                                             |
|                                                                       |
| **✓** Léger et disponible partout : installé nativement sur           |
| Linux/macOS, disponible sur Windows via OpenSSH                       |
|                                                                       |
| **✓** Traçabilité : les connexions SSH sont loguées (qui, quand,      |
| depuis quelle IP)                                                     |
|                                                                       |
| **✓** Automatisation sécurisée : scripts d\'administration distante   |
| sans stocker de mots de passe en clair                                |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** Port 22 très ciblé par les attaques automatisées (scanners,     |
| bots bruteforce)                                                      |
|                                                                       |
| **✗** Gestion des clés complexe à grande échelle (distribuer,         |
| révoquer les clés publiques sur de nombreux serveurs)                 |
|                                                                       |
| **✗** Si la clé privée est compromise sans passphrase, l\'accès est   |
| immédiat                                                              |
|                                                                       |
| **✗** Pas d\'interface graphique natif (usage CLI uniquement sauf     |
| tunneling X11 ou outils tiers)                                        |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** L\'administrateur d\'un serveur Linux souhaite sécuriser      |
| l\'accès SSH. Citez et expliquez 4 mesures de sécurité à mettre en    |
| place dans le fichier de configuration sshd_config.                   |
|                                                                       |
| > *→ Port non standard, PermitRootLogin no, PasswordAuthentication no |
| > (clés uniquement), AllowUsers, MaxAuthTries, LoginGraceTime.*       |
+-----------------------------------------------------------------------+
| **Q2.** Décrivez le processus d\'authentification SSH par clé         |
| publique/privée. Quelles commandes utilisez-vous pour générer et      |
| déployer la clé ?                                                     |
|                                                                       |
| > *→ ssh-keygen (génère paire), ssh-copy-id user@host (déploie clé    |
| > publique dans authorized_keys). Fonctionnement : serveur chiffre    |
| > défi avec clé pub, client déchiffre avec clé privée.*               |
+-----------------------------------------------------------------------+
| **Q3.** Un serveur SSH reçoit plusieurs centaines de tentatives de    |
| connexion par jour depuis des IP inconnues. Comment détectez-vous     |
| cette activité et quelles mesures prenez-vous ?                       |
|                                                                       |
| > *→ Analyser /var/log/auth.log. Mettre en place Fail2Ban             |
| > (bannissement auto), changer port, désactiver auth par mot de       |
| > passe, pare-feu limitant les IP source.*                            |
+-----------------------------------------------------------------------+
| **Q4.** Quelle est la différence entre SCP et SFTP ? Dans quel cas    |
| utiliseriez-vous l\'un plutôt que l\'autre ?                          |
|                                                                       |
| > *→ SCP = copie simple non interactive, rapide, scriptable. SFTP =   |
| > session interactive, navigation, reprise sur erreur. SFTP           |
| > préférable pour usage courant.*                                     |
+-----------------------------------------------------------------------+
| **Q5.** L\'entreprise souhaite permettre à ses techniciens de se      |
| connecter SSH aux équipements réseau (switches Cisco) depuis le       |
| siège. Décrivez l\'architecture et la configuration nécessaire.       |
|                                                                       |
| > *→ Bastion SSH (jump host), clés SSH, IP whitelisting,              |
| > configuration AAA sur équipements Cisco (ip ssh version 2).*        |
+-----------------------------------------------------------------------+

> **5. IDS et IPS**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**▶ IDS --- Intrusion Detection System**

Un IDS est un système de détection d\'intrusion. Il surveille le trafic
réseau ou les activités système et génère des alertes en cas de
comportement suspect. Il ne bloque pas --- il observe et alerte
uniquement.

**▶ IPS --- Intrusion Prevention System**

Un IPS est un système de prévention d\'intrusion. En plus de détecter
les menaces comme un IDS, il peut bloquer activement le trafic
malveillant en temps réel. Il est positionné en ligne (inline) dans le
flux réseau.

  ----------------------------------- -----------------------------------
  **Critère**                         **IDS \| IPS**

  **Rôle**                            Détecte uniquement \| Détecte ET
                                      bloque

  **Position réseau**                 Mode passif (copie du trafic) \|
                                      Mode inline (flux réel)

  **Réaction**                        Génère des alertes \| Bloque,
                                      rejette, réinitialise la connexion

  **Risque faux positif**             Faible impact \| Peut bloquer du
                                      trafic légitime

  **Exemples**                        Snort (mode IDS), Suricata \| Snort
                                      (mode IPS), Suricata IPS
  ----------------------------------- -----------------------------------

**▶ Types de détection**

-   **Détection par signature :** Compare le trafic à une base de
    signatures connues (efficace pour menaces connues)

-   **Détection comportementale / anomalie :** Établit un profil normal
    et alerte en cas de déviation (efficace pour menaces zero-day)

-   **IDS/IPS réseau (NIDS/NIPS) :** Surveille le trafic réseau global

-   **IDS/IPS hôte (HIDS/HIPS) :** Surveille les activités sur un seul
    système (fichiers, processus, logs)

+-----------------------------------------------------------------------+
| **💡 Exemples d\'outils**                                             |
+-----------------------------------------------------------------------+
| -   **Snort :** IDS/IPS open source très répandu, basé sur des règles |
|                                                                       |
| -   **Suricata :** Alternatif à Snort, multi-threading, très          |
|     performant                                                        |
|                                                                       |
| -   **OSSEC / Wazuh :** HIDS open source, surveille logs, fichiers,   |
|     rootkits                                                          |
|                                                                       |
| -   **Fail2Ban :** Outil simple qui lit les logs et bannit les IP     |
|     suspectes                                                         |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** Détection en temps réel : identification des attaques au moment |
| où elles se produisent                                                |
|                                                                       |
| **✓** Visibilité réseau : les IDS/IPS donnent une vue complète du     |
| trafic suspect et permettent des analyses forensiques                 |
|                                                                       |
| **✓** IPS : blocage automatique sans intervention humaine, réduction  |
| du délai de réaction                                                  |
|                                                                       |
| **✓** Détection comportementale : capable de détecter des menaces     |
| zero-day inconnues des antivirus                                      |
|                                                                       |
| **✓** Génération de logs : traces précieuses pour les audits,         |
| investigations et conformité (RGPD, ISO 27001)                        |
|                                                                       |
| **✓** Complémentaire au pare-feu : l\'IPS analyse le contenu là où le |
| firewall bloque sur des règles statiques                              |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** Faux positifs : risque de bloquer du trafic légitime (surtout   |
| en mode IPS), impact sur la production                                |
|                                                                       |
| **✗** Faux négatifs : une attaque sophistiquée ou chiffrée peut       |
| passer inaperçue                                                      |
|                                                                       |
| **✗** Maintenance : les signatures doivent être mises à jour          |
| régulièrement pour rester efficaces                                   |
|                                                                       |
| **✗** Charge réseau : l\'analyse en profondeur des paquets (DPI) peut |
| introduire de la latence                                              |
|                                                                       |
| **✗** Trafic HTTPS chiffré difficile à inspecter sans SSL inspection  |
| (compromis sécurité/vie privée)                                       |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** L\'entreprise EcoTech souhaite mettre en place une solution   |
| de détection d\'intrusions sur son réseau. Expliquez la différence    |
| entre un IDS et un IPS. Lequel recommandez-vous en première intention |
| et pourquoi ?                                                         |
|                                                                       |
| > *→ IDS passif (alerte), IPS actif (bloque). Recommander IDS         |
| > d\'abord pour phase d\'apprentissage, puis IPS une fois les règles  |
| > affinées pour éviter les faux positifs.*                            |
+-----------------------------------------------------------------------+
| **Q2.** Vous constatez dans les logs de votre IDS une série           |
| d\'alertes \'SYN Flood détecté\' vers votre serveur web. De quelle    |
| attaque s\'agit-il ? Quelles contre-mesures mettez-vous en place ?    |
|                                                                       |
| > *→ Attaque DDoS SYN Flood (TCP handshake incomplet). Contre-mesures |
| > : SYN cookies, limitation de connexions, filtrage IPS, blackholing  |
| > de l\'IP source.*                                                   |
+-----------------------------------------------------------------------+
| **Q3.** Quelle est la différence entre un NIDS et un HIDS ? Donnez un |
| exemple d\'outil pour chacun et expliquez dans quel cas les combiner. |
|                                                                       |
| > *→ NIDS = réseau (Snort, Suricata). HIDS = hôte (OSSEC, Wazuh).     |
| > Combiner : NIDS pour le périmètre réseau, HIDS pour les serveurs    |
| > critiques.*                                                         |
+-----------------------------------------------------------------------+
| **Q4.** Expliquez le concept de détection par signature et de         |
| détection par anomalie. Quels sont les avantages et limites de chaque |
| approche ?                                                            |
|                                                                       |
| > *→ Signature : efficace sur menaces connues, nécessite MAJ.         |
| > Anomalie : détecte zero-day, mais génère plus de faux positifs.*    |
+-----------------------------------------------------------------------+
| **Q5.** Un IPS positionné entre le routeur Internet et le pare-feu    |
| commence à bloquer des connexions légitimes vers le serveur de        |
| messagerie. Quelle procédure suivez-vous pour diagnostiquer et        |
| résoudre ce problème ?                                                |
|                                                                       |
| > *→ Analyser les logs IPS, identifier la règle déclenchante,         |
| > vérifier si faux positif, créer une exception (whitelist), tester,  |
| > documenter le changement.*                                          |
+-----------------------------------------------------------------------+

> **6. Attaque Homme du Milieu (Man-in-the-Middle / MitM)**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**▶ Définition**

Une attaque Man-in-the-Middle (MitM) consiste pour un attaquant à
s\'intercaler secrètement entre deux parties qui communiquent (client et
serveur). L\'attaquant peut écouter, modifier ou injecter des données
dans la communication à l\'insu des deux parties.

**▶ Techniques d\'attaque MitM**

-   **ARP Poisoning / Spoofing :** Envoi de fausses réponses ARP sur le
    réseau local pour associer l\'adresse MAC de l\'attaquant à l\'IP
    d\'une cible. Tout le trafic passe par l\'attaquant.

-   **DNS Spoofing :** Falsification des réponses DNS pour rediriger un
    utilisateur vers un faux site web contrôlé par l\'attaquant.

-   **SSL Stripping :** L\'attaquant dégrade une connexion HTTPS en
    HTTP, permettant d\'écouter les données en clair.

-   **Evil Twin (WiFi) :** Point d\'accès WiFi malveillant qui imite un
    réseau légitime pour intercepter les connexions.

-   **BGP Hijacking :** Détournement du routage Internet en annonçant de
    faux préfixes BGP.

**▶ Comment se protéger**

-   **HTTPS / TLS :** Chiffrer les communications rend l\'écoute inutile
    et détecte la manipulation

-   **HSTS :** HTTP Strict Transport Security --- force le navigateur à
    toujours utiliser HTTPS

-   **VPN :** Chiffrer tout le trafic réseau

-   **DAI (Dynamic ARP Inspection) :** Sur les switchs managés, valide
    les paquets ARP pour contrer l\'ARP poisoning

-   **Éviter les WiFi publics :** Ou utiliser un VPN systématiquement

+-----------------------------------------------------------------------+
| **🎯 Scénario type à retenir**                                        |
+-----------------------------------------------------------------------+
| Un employé se connecte au WiFi public d\'un hôtel. Un attaquant a     |
| créé un faux point d\'accès au même nom (Evil Twin). Toutes les       |
| communications de l\'employé sont interceptées (identifiants, emails, |
| données).                                                             |
|                                                                       |
| Solution : VPN obligatoire sur tout réseau non maîtrisé par           |
| l\'entreprise.                                                        |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** (Côté défenseur) HTTPS/TLS : rend l\'écoute inutile et détecte  |
| toute tentative d\'interception                                       |
|                                                                       |
| **✓** HSTS : empêche le downgrade HTTP, force HTTPS même si           |
| l\'attaquant tente de dégrader la connexion                           |
|                                                                       |
| **✓** Authentification mutuelle (mTLS) : le client ET le serveur      |
| s\'authentifient mutuellement                                         |
|                                                                       |
| **✓** VPN : chiffre tout le trafic réseau, protège même sur des       |
| réseaux non fiables (WiFi public)                                     |
|                                                                       |
| **✓** DAI (Dynamic ARP Inspection) : protège contre l\'ARP poisoning  |
| au niveau des switchs managés                                         |
|                                                                       |
| **✓** DNSSEC : protège contre le DNS spoofing en signant              |
| cryptographiquement les enregistrements DNS                           |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** Difficile à détecter sans outils spécialisés : l\'attaque est   |
| transparente pour les victimes                                        |
|                                                                       |
| **✗** ARP poisoning possible sur tout réseau LAN non protégé (DAI non |
| activé)                                                               |
|                                                                       |
| **✗** Les certificats auto-signés ou mal vérifiés facilitent les      |
| attaques SSL stripping                                                |
|                                                                       |
| **✗** Les utilisateurs ignorent souvent les avertissements de         |
| sécurité des navigateurs                                              |
|                                                                       |
| **✗** WiFi public : vecteur d\'attaque très courant et sous-estimé    |
| par les utilisateurs                                                  |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** Lors d\'un audit de sécurité du réseau local de la société    |
| FinanceExpress, vous suspectez une attaque ARP spoofing. Comment la   |
| détectez-vous ? Quelles mesures correctives proposez-vous au niveau   |
| des équipements réseau ?                                              |
|                                                                       |
| > *→ Analyser la table ARP (arp -a), utiliser arpwatch/XArp.          |
| > Corrective : activer DAI sur les switchs Cisco (ip arp inspection), |
| > DHCP snooping.*                                                     |
+-----------------------------------------------------------------------+
| **Q2.** Un commercial utilise le WiFi d\'un hôtel pour accéder au CRM |
| de l\'entreprise. Expliquez en quoi cette pratique est risquée et     |
| proposez une politique de sécurité adaptée.                           |
|                                                                       |
| > *→ Risques : Evil Twin, écoute réseau, MitM. Politique : VPN        |
| > obligatoire sur tout réseau non maîtrisé, HTTPS pour toutes les     |
| > apps, sensibilisation.*                                             |
+-----------------------------------------------------------------------+
| **Q3.** Expliquez l\'attaque SSL Stripping. Comment HSTS permet-il de |
| s\'en protéger ?                                                      |
|                                                                       |
| > *→ SSL Stripping : attaquant intercepte et dégrade HTTPS→HTTP. HSTS |
| > : le serveur indique au navigateur de toujours utiliser HTTPS       |
| > (Strict-Transport-Security header), même si l\'utilisateur tape     |
| > http://\...*                                                        |
+-----------------------------------------------------------------------+
| **Q4.** Un employé reçoit un email qui semble provenir du PDG lui     |
| demandant de virer 50 000€. L\'email est authentique en apparence.    |
| Analysez le risque et proposez des mesures organisationnelles et      |
| techniques.                                                           |
|                                                                       |
| > *→ Attaque Business Email Compromise (BEC) / Whaling. Mesures :     |
| > DMARC/DKIM/SPF sur les emails, procédure de validation des          |
| > virements, sensibilisation, MFA sur la messagerie.*                 |
+-----------------------------------------------------------------------+
| **Q5.** Qu\'est-ce que le certificate pinning ? Dans quel contexte    |
| est-il utilisé et quelles sont ses limites ?                          |
|                                                                       |
| > *→ Associer une application à un certificat ou une clé publique     |
| > spécifique → résiste aux faux certificats. Utilisé dans les apps    |
| > mobiles. Limite : mise à jour difficile si certificat change.*      |
+-----------------------------------------------------------------------+

> **7. ITIL (Information Technology Infrastructure Library)**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**▶ Définition**

ITIL est un référentiel de bonnes pratiques pour la gestion des services
informatiques (IT Service Management --- ITSM). Il fournit un ensemble
de processus, procédures et recommandations pour aligner les services IT
sur les besoins métier.

ITIL n\'est pas une norme imposée, c\'est un cadre de référence
(framework). La version actuelle est ITIL 4.

**▶ Les 5 étapes du cycle de vie ITIL**

  ----------------------------------- -----------------------------------
  **Étape**                           **Description**

  **1. Stratégie des services**       Définir la stratégie, comprendre
                                      les besoins métier, aligner l\'IT
                                      sur les objectifs de l\'entreprise

  **2. Conception des services**      Concevoir les nouveaux services ou
                                      les améliorations (SLA, capacité,
                                      disponibilité, sécurité)

  **3. Transition des services**      Mettre en production les nouveaux
                                      services en maîtrisant les risques
                                      (gestion des changements, tests)

  **4. Exploitation des services**    Gérer quotidiennement les services
                                      (incidents, problèmes, demandes,
                                      accès)

  **5. Amélioration continue**        Mesurer, analyser et améliorer en
                                      permanence les services (PDCA)
  ----------------------------------- -----------------------------------

**▶ Processus clés**

-   **Gestion des incidents :** Rétablir le service le plus rapidement
    possible après une interruption. Objectif : minimiser l\'impact
    métier.

-   **Gestion des problèmes :** Identifier et éliminer les causes
    profondes des incidents répétitifs (analyse RCA --- Root Cause
    Analysis).

-   **Gestion des changements :** Évaluer, approuver et implémenter les
    changements en minimisant les risques (CAB --- Change Advisory
    Board).

-   **Gestion des niveaux de service (SLA) :** Définir et surveiller les
    engagements de qualité de service entre l\'IT et les clients.

-   **Service Desk :** Point de contact unique (SPOC) pour les
    utilisateurs --- gère incidents et demandes.

+-----------------------------------------------------------------------+
| **📋 Incident vs Problème vs Changement**                             |
+-----------------------------------------------------------------------+
| -   **Incident :** Interruption ou dégradation non planifiée. Action  |
|     immédiate. Ex : le serveur de messagerie est inaccessible.        |
|                                                                       |
| -   **Problème :** Cause sous-jacente d\'un ou plusieurs incidents.   |
|     Investigation de fond. Ex : pourquoi le serveur tombe en panne    |
|     chaque lundi ?                                                    |
|                                                                       |
| -   **Changement :** Modification planifiée d\'un service ou d\'une   |
|     infrastructure. Ex : mise à jour de l\'OS du serveur.             |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** Alignement IT / métier : ITIL s\'assure que les services        |
| informatiques répondent réellement aux besoins de l\'entreprise       |
|                                                                       |
| **✓** Standardisation des processus : tout le monde parle le même     |
| langage (incident, problème, changement\...)                          |
|                                                                       |
| **✓** Amélioration de la qualité de service : les processus ITIL      |
| réduisent le temps de résolution des incidents                        |
|                                                                       |
| **✓** Gestion des risques : la gestion des changements prévient les   |
| interruptions causées par les mises à jour                            |
|                                                                       |
| **✓** SLA mesurables : objectifs de service contractualisés et suivis |
| (disponibilité, temps de réponse\...)                                 |
|                                                                       |
| **✓** Amélioration continue : le cycle de vie ITIL intègre un         |
| processus permanent d\'optimisation                                   |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** Lourdeur administrative : trop de processus formels peuvent     |
| ralentir les équipes, surtout dans les petites structures             |
|                                                                       |
| **✗** Coût de mise en œuvre : formation des équipes, outils ITSM      |
| (ServiceNow, GLPI\...), temps d\'adaptation                           |
|                                                                       |
| **✗** Risque de bureaucratie : si mal appliqué, ITIL peut devenir une |
| fin en soi plutôt qu\'un moyen                                        |
|                                                                       |
| **✗** ITIL n\'est pas prescriptif : cadre de référence à adapter, pas |
| de recette unique                                                     |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** Le lundi matin, 30 utilisateurs signalent que leur messagerie |
| Outlook ne fonctionne pas. Appliquez le processus de gestion des      |
| incidents ITIL : quelles sont les étapes successives à suivre ?       |
|                                                                       |
| > *→ Détection, enregistrement, catégorisation, priorisation,         |
| > diagnostic, escalade si besoin, résolution, clôture, communication  |
| > aux utilisateurs.*                                                  |
+-----------------------------------------------------------------------+
| **Q2.** Un problème récurrent de lenteur réseau affecte le service    |
| comptabilité tous les fins de mois. Expliquez comment la gestion des  |
| problèmes ITIL diffère de la gestion des incidents. Quelle démarche   |
| adoptez-vous ?                                                        |
|                                                                       |
| > *→ Incident = réaction rapide (rétablir). Problème = investigation  |
| > profonde (comprendre). Démarche : RCA (Root Cause Analysis),        |
| > workaround, erreur connue (KEDB), solution définitive.*             |
+-----------------------------------------------------------------------+
| **Q3.** L\'entreprise prévoit de migrer son serveur de fichiers vers  |
| un nouveau NAS. Décrivez la procédure de gestion des changements ITIL |
| à respecter. Quels documents produisez-vous ?                         |
|                                                                       |
| > *→ Demande de changement (RFC), évaluation des risques et impacts,  |
| > validation par le CAB, plan de rollback, test en pré-prod,          |
| > déploiement, revue post-implémentation.*                            |
+-----------------------------------------------------------------------+
| **Q4.** Qu\'est-ce qu\'un SLA ? Donnez un exemple concret adapté à    |
| une entreprise de 100 personnes avec un service informatique interne. |
|                                                                       |
| > *→ SLA = accord de niveau de service. Exemple : incidents critiques |
| > résolus en 4h, standards en 8h ouvrables, disponibilité serveurs    |
| > 99,9%, hotline 8h-18h semaine.*                                     |
+-----------------------------------------------------------------------+
| **Q5.** L\'entreprise utilise GLPI pour gérer son parc informatique   |
| et ses tickets. En quoi cet outil s\'inscrit-il dans une démarche     |
| ITIL ? Citez les processus ITIL qu\'il supporte.                      |
|                                                                       |
| > *→ GLPI = outil ITSM. Supporte : gestion des incidents (tickets),   |
| > gestion des actifs/CMDB, gestion des contrats, base de              |
| > connaissances. Outil concret pour appliquer ITIL.*                  |
+-----------------------------------------------------------------------+

> **8. Sauvegardes et Restaurations**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**▶ Définition et enjeux**

Une sauvegarde (backup) est une copie des données permettant de les
restaurer en cas de perte, corruption, cyberattaque (ransomware) ou
sinistre. La politique de sauvegarde est un élément central de la
continuité d\'activité.

**▶ Types de sauvegardes**

  ----------------------------------- -----------------------------------
  **Type**                            **Description**

  **Sauvegarde complète (Full)**      Copie intégrale de toutes les
                                      données. Sûre et simple à
                                      restaurer, mais longue et
                                      volumineuse. Se fait en général le
                                      week-end.

  **Sauvegarde incrémentale**         Sauvegarde uniquement les données
                                      modifiées depuis la DERNIÈRE
                                      sauvegarde (complète ou
                                      incrémentale). Rapide. Restauration
                                      complexe (full + toutes les
                                      incrémentales).

  **Sauvegarde différentielle**       Sauvegarde les données modifiées
                                      depuis la DERNIÈRE SAUVEGARDE
                                      COMPLÈTE. Restauration plus simple
                                      (full + dernière différentielle
                                      uniquement).

  **Sauvegarde miroir (Clone)**       Copie exacte synchronisée. Pas
                                      d\'historique --- si un fichier est
                                      supprimé, il l\'est partout.
  ----------------------------------- -----------------------------------

+-----------------------------------------------------------------------+
| **📐 Règle 3-2-1 des sauvegardes**                                    |
+-----------------------------------------------------------------------+
| -   **3 :** Garder 3 copies des données (1 originale + 2 sauvegardes) |
|                                                                       |
| -   **2 :** Sur 2 supports différents (ex : NAS + bande magnétique)   |
|                                                                       |
| -   **1 :** Dont 1 copie hors site (cloud, datacenter distant) pour   |
|     se protéger des sinistres physiques                               |
+-----------------------------------------------------------------------+

**▶ Concepts importants**

-   **RPO (Recovery Point Objective) :** Perte de données maximale
    acceptable. RPO = 4h → on peut perdre au maximum 4h de données.

-   **RTO (Recovery Time Objective) :** Temps maximal acceptable pour
    restaurer le service. RTO = 2h → service rétabli en moins de 2h.

-   **PCA (Plan de Continuité d\'Activité) :** Ensemble de mesures pour
    maintenir l\'activité pendant un sinistre.

-   **PRA (Plan de Reprise d\'Activité) :** Ensemble de procédures pour
    reprendre l\'activité après un sinistre.

**▶ Supports et solutions**

-   **NAS (Network Attached Storage) :** Serveur de fichiers connecté au
    réseau

-   **Bandes magnétiques (LTO) :** Très grande capacité, archivage
    longue durée, faible coût au Go

-   **Cloud Backup :** Sauvegarde vers AWS S3, Azure Backup,
    Backblaze\... Hors site par définition

-   **Logiciels :** Veeam Backup, Acronis, Windows Server Backup, Bacula

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** Protection contre tous les types de pertes : pannes             |
| matérielles, erreurs humaines, ransomwares, sinistres                 |
|                                                                       |
| **✓** Règle 3-2-1 : garantit qu\'aucun événement unique ne peut       |
| détruire toutes les copies                                            |
|                                                                       |
| **✓** Sauvegarde incrémentale : très rapide quotidiennement, espace   |
| disque économisé                                                      |
|                                                                       |
| **✓** Test de restauration possible : le seul moyen de valider        |
| qu\'une sauvegarde fonctionne réellement                              |
|                                                                       |
| **✓** Conformité légale : certaines données doivent être conservées X |
| années (comptabilité, RH\...)                                         |
|                                                                       |
| **✓** RPO/RTO définis : objectifs mesurables qui permettent de        |
| dimensionner la politique de sauvegarde                               |
|                                                                       |
| **✓** Versioning : possibilité de restaurer une version antérieure    |
| d\'un fichier (ex : avant infection virale)                           |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** Coût : stockage, licences logicielles, maintenance des          |
| supports, bande passante cloud                                        |
|                                                                       |
| **✗** Délai de restauration : une restauration complète peut prendre  |
| des heures voire des jours selon le volume                            |
|                                                                       |
| **✗** Sauvegarde incrémentale : restauration complexe (full + toutes  |
| les incrémentales dans l\'ordre)                                      |
|                                                                       |
| **✗** Les sauvegardes non testées régulièrement ne sont PAS fiables   |
| --- trop d\'entreprises le découvrent lors d\'un sinistre             |
|                                                                       |
| **✗** Sauvegardes connectées au réseau : vulnérables aux ransomwares  |
| qui se propagent et les chiffrent aussi                               |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** La société MedTech conserve ses données patients sur un       |
| serveur NAS. Proposez une politique de sauvegarde complète en         |
| respectant la règle 3-2-1. Précisez les types de sauvegardes, les     |
| supports et la fréquence.                                             |
|                                                                       |
| > *→ Full le dimanche, incrémentales du lundi au samedi. Copie locale |
| > NAS + copie sur bandes (coffre), + copie cloud chiffrée. Rétention  |
| > 30 jours minimum.*                                                  |
+-----------------------------------------------------------------------+
| **Q2.** Expliquez la différence entre RPO et RTO. Une entreprise a un |
| RPO de 4h et un RTO de 2h. Qu\'est-ce que cela signifie concrètement  |
| ? Quels impacts sur la politique de sauvegarde ?                      |
|                                                                       |
| > *→ RPO 4h = max 4h de perte de données → sauvegardes toutes les 4h. |
| > RTO 2h = service rétabli en max 2h → infrastructure redondante,     |
| > procédures testées, serveur de secours.*                            |
+-----------------------------------------------------------------------+
| **Q3.** Le serveur de fichiers a été chiffré par un ransomware un     |
| mardi à 14h. La dernière sauvegarde complète date de dimanche, et des |
| incrémentales ont été effectuées lundi et mardi matin. Décrivez la    |
| procédure de restauration.                                            |
|                                                                       |
| > *→ Isoler le serveur, restaurer sur machine propre, appliquer full  |
| > (dimanche) + incrémentale lundi + incrémentale mardi matin. Perte = |
| > données de mardi matin à 14h.*                                      |
+-----------------------------------------------------------------------+
| **Q4.** Pourquoi est-il impératif de tester régulièrement les         |
| restaurations ? À quelle fréquence recommandez-vous ces tests ?       |
| Comment les documentez-vous ?                                         |
|                                                                       |
| > *→ Une sauvegarde non testée = sauvegarde infiable (corruption,     |
| > erreur de config). Tests trimestriels minimum. PV de test de        |
| > restauration avec : date, durée, volume, résultat, signature.*      |
+-----------------------------------------------------------------------+
| **Q5.** L\'entreprise envisage de migrer ses sauvegardes vers le      |
| cloud. Quels sont les avantages, les risques et les points de         |
| vigilance à aborder avec la direction ?                               |
|                                                                       |
| > *→ Avantages : hors site automatiquement, scalabilité, coût opex.   |
| > Risques : confidentialité (chiffrer avant envoi), bande passante,   |
| > dépendance fournisseur. RGPD : localisation des données.*           |
+-----------------------------------------------------------------------+

> **9. Force Brute et Attaque par Dictionnaire**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**▶ Force brute --- Définition**

L\'attaque par force brute consiste à tester systématiquement toutes les
combinaisons possibles de caractères jusqu\'à trouver le mot de passe
correct. Aucune intelligence --- pure exhaustivité.

-   **Exemple :** Pour un mot de passe de 4 chiffres : on teste 0000,
    0001\... jusqu\'à 9999 (10 000 combinaisons max)

-   **Limites :** Très lent pour des mots de passe longs. Un mdp de 12
    caractères alphanumériques = des milliards de combinaisons.

**▶ Attaque par dictionnaire --- Définition**

L\'attaque par dictionnaire utilise une liste prédéfinie de mots de
passe courants. Elle est bien plus rapide car elle exploite les
mauvaises habitudes des utilisateurs.

-   **Exemples de dictionnaires :** rockyou.txt (14 millions de mots de
    passe), liste des 1000 mots de passe les plus utilisés

-   **Outils courants :** Hydra, Medusa, John the Ripper, Hashcat

-   **Variante hybride :** Attaque par règles --- applique des
    transformations (password → P@ssw0rd)

  ----------------------------------- -----------------------------------
  **Type**                            **Méthode \| Vitesse \| Limite**

  **Force brute**                     Teste toutes les combinaisons \|
                                      Lent mais exhaustif \| Fonctionne
                                      toujours

  **Dictionnaire**                    Liste de mots prédéfinis \| Très
                                      rapide \| Dépend de la qualité du
                                      dictionnaire

  **Hybride**                         Dictionnaire + règles de
                                      transformation \| Efficace sur mots
                                      communs modifiés

  **Rainbow Table**                   Tables précalculées de hashes \|
                                      Très rapide \| Contrée par le
                                      salage (salt)
  ----------------------------------- -----------------------------------

**▶ Contre-mesures**

-   **Mots de passe forts :** Longueur minimale 12 caractères,
    majuscules, minuscules, chiffres, caractères spéciaux

-   **Verrouillage de compte :** Bloquer le compte après N tentatives
    échouées (Account Lockout Policy)

-   **MFA (Multi-Factor Authentication) :** Même si le mot de passe est
    découvert, un second facteur est nécessaire

-   **Fail2Ban / IPS :** Détecter et bloquer automatiquement les IP
    effectuant trop de tentatives

-   **Salage des mots de passe :** Ajouter une valeur aléatoire (salt)
    avant le hachage pour contrer les rainbow tables

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** (Défenseur) Verrouillage de compte : neutralise efficacement    |
| les attaques automatisées                                             |
|                                                                       |
| **✓** MFA : même si le mot de passe est découvert, l\'accès reste     |
| bloqué sans le second facteur                                         |
|                                                                       |
| **✓** Politique de mots de passe forts : augmente exponentiellement   |
| le temps de craquage                                                  |
|                                                                       |
| **✓** Salage des hashes : rend les rainbow tables inefficaces, chaque |
| hash est unique même pour le même mdp                                 |
|                                                                       |
| **✓** Fail2Ban : automatise le bannissement des IP attackantes sans   |
| intervention humaine                                                  |
|                                                                       |
| **✓** Monitoring : permet de détecter les attaques en cours et d\'y   |
| répondre rapidement                                                   |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** Verrouillage de compte : peut être détourné pour du déni de     |
| service (verrouiller les comptes des autres utilisateurs)             |
|                                                                       |
| **✗** Les hashes MD5/SHA-1 non salés se craquent en quelques secondes |
| avec des GPU modernes                                                 |
|                                                                       |
| **✗** Attaque offline (hash volé) : aucune limite de tentatives, le   |
| verrouillage ne protège pas                                           |
|                                                                       |
| **✗** Mots de passe \'complexes\' prévisibles : P@ssw0rd1 est dans    |
| tous les dictionnaires modernes                                       |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** Suite à une intrusion, vous découvrez qu\'un attaquant a      |
| extrait la base de données des mots de passe hashés en MD5. Quels     |
| sont les risques ? Quelles actions immédiates prenez-vous ? Que       |
| recommandez-vous pour l\'avenir ?                                     |
|                                                                       |
| > *→ MD5 = cassable rapidement (rainbow tables, GPU). Actions :       |
| > forcer réinitialisation de tous les mots de passe, avertir les      |
| > utilisateurs. Futur : bcrypt/argon2 + salt, MFA.*                   |
+-----------------------------------------------------------------------+
| **Q2.** La politique de verrouillage bloque le compte après 3         |
| tentatives échouées. Un utilisateur signale que son compte se         |
| verrouille régulièrement sans qu\'il ait fait de fausses manœuvres.   |
| Comment analysez-vous la situation ?                                  |
|                                                                       |
| > *→ Analyser logs d\'authentification (Event ID 4625 Windows). Peut  |
| > être une attaque en cours ou un problème de sync credentials (app   |
| > mobile, partage réseau avec ancien mdp).*                           |
+-----------------------------------------------------------------------+
| **Q3.** Expliquez la différence entre une attaque par force brute et  |
| une attaque par dictionnaire. Pour tester la robustesse des mots de   |
| passe des comptes AD, quelle démarche légale adoptez-vous ?           |
|                                                                       |
| > *→ Différencier les deux méthodes. Pour test légal : autorisation   |
| > écrite de la direction, audit en environnement de test ou hors      |
| > production, rapport confidentiel. Outils : John the Ripper,         |
| > Hashcat.*                                                           |
+-----------------------------------------------------------------------+
| **Q4.** Quelles règles de politique de mots de passe recommandez-vous |
| dans une GPO Active Directory pour une PME de 80 personnes ?          |
| Justifiez chaque paramètre.                                           |
|                                                                       |
| > *→ Longueur min 12 car, complexité activée, historique 10 derniers  |
| > mdp, expiration 90 jours (ou sans expiration si MFA), verrouillage  |
| > après 5 tentatives, durée verrouillage 15 min.*                     |
+-----------------------------------------------------------------------+
| **Q5.** Qu\'est-ce qu\'une attaque par credential stuffing ? En quoi  |
| diffère-t-elle de la force brute classique ? Comment s\'en protéger ? |
|                                                                       |
| > *→ Credential stuffing = utilisation de couples login/mdp issus de  |
| > fuites de données sur d\'autres sites. Différence : utilise des     |
| > identifiants valides connus. Protection : MFA, détection d\'IP      |
| > anormales, Have I Been Pwned.*                                      |
+-----------------------------------------------------------------------+

> **10. Types de Cyberattaques et Comment les Reconnaître**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**🦠 Malwares (logiciels malveillants)**

  ----------------------------------- -----------------------------------
  **Type**                            **Description et signes**

  **Virus**                           S\'attache à un programme légitime
                                      et se propage. Reconnaître :
                                      ralentissement, fichiers corrompus,
                                      comportement anormal.

  **Ver (Worm)**                      Se propage automatiquement sur le
                                      réseau sans fichier hôte.
                                      Reconnaître : saturation réseau,
                                      propagation rapide.

  **Trojan (Cheval de Troie)**        Se déguise en logiciel légitime
                                      mais contient du code malveillant.
                                      Reconnaître : installations non
                                      sollicitées, connexions réseau
                                      inattendues.

  **Ransomware**                      Chiffre les fichiers et demande une
                                      rançon. Reconnaître : fichiers avec
                                      extension bizarre (.locked),
                                      message de rançon.

  **Spyware**                         Collecte discrètement des
                                      informations (frappes clavier, mots
                                      de passe). Reconnaître : lenteur
                                      système, activité réseau anormale.

  **Rootkit**                         Masque sa présence dans le système,
                                      donne un accès persistant à
                                      l\'attaquant. Très difficile à
                                      détecter.
  ----------------------------------- -----------------------------------

**🎣 Attaques sociales (ingénierie sociale)**

-   **Phishing :** Email frauduleux imitant une entité de confiance pour
    voler des identifiants. Reconnaître : URL suspecte, fautes, urgence
    artificielle, expéditeur douteux.

-   **Spear Phishing :** Phishing ciblé sur une personne précise avec
    des informations personnalisées. Plus difficile à détecter.

-   **Vishing / Smishing :** Phishing par téléphone (voice) ou par SMS.

-   **Whaling :** Phishing ciblant des dirigeants (PDG, DAF) --- enjeux
    financiers élevés.

**💥 Attaques réseau**

-   **DoS / DDoS :** Saturation d\'un service. DoS = 1 source, DDoS =
    réseau de machines compromises (botnet). Reconnaître : serveur
    inaccessible, forte hausse du trafic.

-   **ARP / DNS Spoofing :** Falsification d\'identités réseau --- base
    des attaques MitM.

-   **Injection SQL :** Insertion de code SQL dans un formulaire pour
    manipuler une base de données. Reconnaître : réponses d\'erreur SQL
    dans l\'application.

-   **XSS (Cross-Site Scripting) :** Injection de scripts malveillants
    dans une page web pour cibler les utilisateurs.

+-----------------------------------------------------------------------+
| **📊 Signes généraux d\'une cyberattaque**                            |
+-----------------------------------------------------------------------+
| -   **Signes système :** CPU/RAM élevés sans raison, processus        |
|     inconnus, fichiers modifiés/chiffrés, nouveaux comptes créés      |
|                                                                       |
| -   **Signes réseau :** Trafic inhabituel, connexions vers des IP     |
|     inconnues, lenteur réseau, scans de ports                         |
|                                                                       |
| -   **Signes utilisateur :** Mots de passe ne fonctionnant plus,      |
|     emails envoyés à l\'insu                                          |
|                                                                       |
| -   **Logs :** Tentatives d\'authentification répétées, accès à des   |
|     heures inhabituelles, erreurs en masse                            |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** Connaissance des attaques = meilleure défense : comprendre les  |
| techniques adversaires permet de mieux se protéger                    |
|                                                                       |
| **✓** Sensibilisation efficace : expliquer concrètement les attaques  |
| (phishing, ransomware) aux utilisateurs réduit drastiquement les      |
| risques                                                               |
|                                                                       |
| **✓** Plans de réponse aux incidents : avoir identifié les types      |
| d\'attaques permet de préparer des procédures adaptées                |
|                                                                       |
| **✓** Threat intelligence : surveiller les nouvelles campagnes        |
| d\'attaques permet d\'anticiper les menaces                           |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** Les attaquants innovent constamment : les défenses d\'hier ne   |
| protègent pas contre les attaques de demain                           |
|                                                                       |
| **✗** Attaques sociales (phishing, ingénierie sociale) : la           |
| technologie seule ne suffit pas --- l\'humain reste le maillon faible |
|                                                                       |
| **✗** Attaques zero-day : aucune signature disponible, difficile à    |
| détecter avant publication du patch                                   |
|                                                                       |
| **✗** Ransomware-as-a-Service : les attaques sont accessibles à des   |
| acteurs sans compétences techniques                                   |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** Un employé de la comptabilité reçoit un email de son          |
| \'directeur financier\' lui demandant de réaliser un virement urgent  |
| de 25 000€. L\'email est bien orthographié et l\'adresse semble       |
| correcte. Identifiez l\'attaque, analysez les signaux d\'alerte et    |
| proposez des mesures préventives.                                     |
|                                                                       |
| > *→ Business Email Compromise (BEC) / Whaling / Social Engineering.  |
| > Signaux : urgence, demande inhabituelle. Mesures : procédure de     |
| > double validation des virements, DMARC, formation.*                 |
+-----------------------------------------------------------------------+
| **Q2.** Le système de supervision réseau indique une saturation à     |
| 100% de la liaison Internet depuis 30 minutes. Les serveurs web sont  |
| inaccessibles. Identifiez le type d\'attaque probable et décrivez     |
| votre procédure de réponse à incident.                                |
|                                                                       |
| > *→ DDoS probable. Procédure : contacter le FAI (blackholing,        |
| > scrubbing center), activer CDN/Cloudflare si disponible, analyser   |
| > les logs, activer le PCA, communication interne et externe.*        |
+-----------------------------------------------------------------------+
| **Q3.** Plusieurs utilisateurs signalent que leurs fichiers ont été   |
| renommés avec l\'extension \'.locked\' et un fichier                  |
| \'README_DECRYPT.txt\' est apparu sur leurs bureaux. Que s\'est-il    |
| passé ? Quelles sont vos actions immédiates ?                         |
|                                                                       |
| > *→ Ransomware. Actions immédiates : isoler les machines             |
| > (déconnecter réseau), identifier le patient zéro, ne pas payer la   |
| > rançon, restaurer depuis sauvegardes saines, identifier le vecteur  |
| > d\'entrée.*                                                         |
+-----------------------------------------------------------------------+
| **Q4.** Expliquez le fonctionnement d\'une attaque par injection SQL. |
| Donnez un exemple concret et expliquez comment sécuriser une          |
| application web contre cette vulnérabilité.                           |
|                                                                       |
| > *→ Saisie de code SQL dans un champ (ex : \' OR \'1\'=\'1).         |
| > Sécurisation : requêtes préparées (parameterized queries),          |
| > validation des entrées, WAF, principe du moindre privilège DB.*     |
+-----------------------------------------------------------------------+
| **Q5.** Qu\'est-ce qu\'une attaque de phishing ? Comment              |
| sensibilisez-vous les collaborateurs d\'une entreprise ? Proposez un  |
| plan de sensibilisation concret pour une PME.                         |
|                                                                       |
| > *→ Formation initiale + rappels réguliers, simulation de phishing   |
| > (faux emails tests), procédure de signalement, affichage,           |
| > e-learning. Indicateurs : taux de clics sur simulations.*           |
+-----------------------------------------------------------------------+

> **11. Chiffrement (Cryptographie)**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**▶ Définition**

Le chiffrement est le processus de transformation de données lisibles
(texte clair) en données illisibles (texte chiffré) à l\'aide d\'un
algorithme et d\'une clé. Seule une personne possédant la clé de
déchiffrement peut lire les données.

**▶ Chiffrement symétrique**

Une seule et même clé est utilisée pour chiffrer ET déchiffrer. Rapide,
adapté aux grands volumes de données. Problème : comment partager la clé
de façon sécurisée ?

  ----------------------------------- -----------------------------------
  **Algorithme**                      **Description**

  **AES (Advanced Encryption          Standard actuel, très sécurisé.
  Standard)**                         AES-128, AES-192, AES-256. Utilisé
                                      dans HTTPS, WPA2, chiffrement de
                                      disques.

  **DES / 3DES**                      Ancien standard, DES est cassé (56
                                      bits). 3DES plus solide mais
                                      obsolète.

  **ChaCha20**                        Algorithme moderne, très rapide,
                                      utilisé dans TLS 1.3.
  ----------------------------------- -----------------------------------

**▶ Chiffrement asymétrique**

Paire de clés : une clé publique (partageable) et une clé privée
(secrète). Ce qui est chiffré avec la clé publique ne peut être
déchiffré qu\'avec la clé privée, et vice-versa.

-   **Usage 1 --- Confidentialité :** Je chiffre avec la clé publique du
    destinataire, seul lui peut déchiffrer avec sa clé privée

-   **Usage 2 --- Signature numérique :** Je signe avec ma clé privée,
    tout le monde peut vérifier avec ma clé publique

  ----------------------------------- -----------------------------------
  **Algorithme**                      **Description**

  **RSA**                             Standard historique. Clés de 2048
                                      ou 4096 bits. Utilisé dans TLS,
                                      SSH, certificats.

  **ECDSA / ECDH**                    Basé sur courbes elliptiques. Plus
                                      efficace que RSA à sécurité
                                      équivalente.

  **Diffie-Hellman**                  Protocole d\'échange de clé
                                      sécurisé sur un canal non sécurisé.
                                      Base de TLS.
  ----------------------------------- -----------------------------------

**▶ Fonctions de hachage**

Transforme des données de taille quelconque en une empreinte (hash) de
taille fixe. Opération à sens unique (on ne peut pas retrouver les
données depuis le hash).

-   **SHA-256 / SHA-3 :** Standards actuels sécurisés. Utilisés pour les
    certificats, signatures, intégrité des fichiers.

-   **MD5 / SHA-1 :** Obsolètes et vulnérables aux collisions. Ne plus
    utiliser pour la sécurité.

-   **Bcrypt / Argon2 :** Fonctions spécialement conçues pour hacher les
    mots de passe (lentes par conception).

+-----------------------------------------------------------------------+
| **🔑 Tableau récapitulatif**                                          |
+-----------------------------------------------------------------------+
|   --------------------------------- --------------------------------- |
|   **Type**                          **Clés \| Vitesse \| Usage \|     |
|                                     Exemples**                        |
|                                                                       |
|   **Symétrique**                    1 clé \| Rapide \| Grands volumes |
|                                     \| AES, ChaCha20                  |
|                                                                       |
|   **Asymétrique**                   Clé pub + privée \| Lent \|       |
|                                     Échanges de clés, signatures \|   |
|                                     RSA, ECDSA                        |
|                                                                       |
|   **Hachage**                       Aucune clé \| Très rapide \|      |
|                                     Intégrité, mots de passe \|       |
|                                     SHA-256, Bcrypt                   |
|   --------------------------------- --------------------------------- |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** Confidentialité absolue : même si les données sont interceptées |
| ou volées, elles sont illisibles sans la clé                          |
|                                                                       |
| **✓** AES-256 considéré incassable en pratique : force brute          |
| impossible avec les ordinateurs actuels                               |
|                                                                       |
| **✓** Chiffrement asymétrique : résout le problème de l\'échange de   |
| clé sur un canal non sécurisé                                         |
|                                                                       |
| **✓** Signatures numériques : garantissent l\'authenticité et la      |
| non-répudiation (l\'émetteur ne peut nier avoir signé)                |
|                                                                       |
| **✓** Hachage : vérification rapide de l\'intégrité sans stocker les  |
| données d\'origine                                                    |
|                                                                       |
| **✓** Chiffrement de bout en bout (E2EE) : même le fournisseur de     |
| service ne peut pas lire les données                                  |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** Gestion des clés : problème complexe --- si la clé est perdue,  |
| les données sont définitivement inaccessibles                         |
|                                                                       |
| **✗** Performance : le chiffrement a un coût CPU, significatif pour   |
| de très grands volumes ou systèmes embarqués                          |
|                                                                       |
| **✗** Chiffrement asymétrique lent : utilisé uniquement pour les      |
| échanges de clés, pas pour les données en masse                       |
|                                                                       |
| **✗** Algorithmes obsolètes (MD5, DES, RC4) toujours utilisés dans de |
| vieux systèmes --- risque de sécurité                                 |
|                                                                       |
| **✗** Chiffrement ne protège pas contre la mauvaise implémentation :  |
| un algorithme fort mal utilisé reste vulnérable                       |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** L\'entreprise stocke les mots de passe de ses utilisateurs en |
| MD5 dans sa base de données. Expliquez pourquoi c\'est problématique  |
| et proposez une solution moderne avec justification.                  |
|                                                                       |
| > *→ MD5 = compromis rapidement (rainbow tables, GPU). Solution :     |
| > bcrypt ou argon2id + salt unique par utilisateur. Ces algos sont    |
| > conçus pour être lents volontairement.*                             |
+-----------------------------------------------------------------------+
| **Q2.** Expliquez comment fonctionne l\'échange de clés               |
| Diffie-Hellman. Pourquoi est-il utilisé dans TLS malgré le fait       |
| qu\'il ne chiffre pas les données lui-même ?                          |
|                                                                       |
| > *→ DH permet à deux parties d\'établir un secret partagé sur un     |
| > canal public sans jamais l\'échanger directement. Utilisé dans TLS  |
| > pour générer la clé de session symétrique (Perfect Forward          |
| > Secrecy).*                                                          |
+-----------------------------------------------------------------------+
| **Q3.** Un utilisateur reçoit un fichier important par email. Comment |
| peut-il vérifier que le fichier n\'a pas été altéré pendant le        |
| transfert ? Décrivez la procédure technique.                          |
|                                                                       |
| > *→ L\'expéditeur calcule le hash SHA-256 du fichier et le           |
| > communique séparément. Le destinataire recalcule le hash et         |
| > compare. Si identiques = intégrité vérifiée.*                       |
+-----------------------------------------------------------------------+
| **Q4.** Dans le contexte du chiffrement d\'un disque dur              |
| d\'ordinateur portable d\'entreprise, expliquez pourquoi c\'est       |
| indispensable. Quelle solution Microsoft recommandez-vous et quel     |
| algorithme utilise-t-elle ?                                           |
|                                                                       |
| > *→ Protection en cas de vol/perte physique. BitLocker (Windows)     |
| > avec AES-256 XTS. Clé de récupération stockée dans AD ou Azure AD.  |
| > TPM pour déverrouillage automatique.*                               |
+-----------------------------------------------------------------------+
| **Q5.** Expliquez la différence entre chiffrement et encodage. Donnez |
| un exemple de chacun et précisez lequel apporte de la sécurité.       |
|                                                                       |
| > *→ Chiffrement : transformation avec clé, nécessite la clé pour     |
| > déchiffrer → sécurité. Encodage (ex: Base64) : transformation       |
| > réversible sans clé → pas de sécurité, juste une représentation     |
| > différente.*                                                        |
+-----------------------------------------------------------------------+

> **12. Disponibilité**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**▶ Définition**

La disponibilité est l\'un des trois piliers de la sécurité informatique
avec la Confidentialité et l\'Intégrité (trilogie CIA). Elle garantit
que les systèmes et les données sont accessibles quand les utilisateurs
en ont besoin.

**▶ Mesure de la disponibilité**

Elle s\'exprime en pourcentage de temps de fonctionnement annuel :

  ----------------------------------- -----------------------------------
  **Disponibilité**                   **Temps d\'arrêt annuel max**

  **99% (2 neuf)**                    Temps d\'arrêt max : \~3,65
                                      jours/an

  **99,9% (3 neuf)**                  Temps d\'arrêt max : \~8,7
                                      heures/an

  **99,99% (4 neuf)**                 Temps d\'arrêt max : \~52
                                      minutes/an

  **99,999% (5 neuf)**                Temps d\'arrêt max : \~5 minutes/an
                                      (objectif datacenter tier 4)
  ----------------------------------- -----------------------------------

**▶ Mécanismes pour assurer la disponibilité**

-   **Haute disponibilité (HA) :** Architecture avec redondance des
    composants critiques pour éliminer les SPOF. Si un composant tombe,
    un autre prend le relais automatiquement.

-   **Clustering :** Plusieurs serveurs fonctionnent en groupe et se
    partagent la charge. Si un nœud tombe, les autres continuent.

-   **Load Balancing :** Répartition du trafic entre plusieurs serveurs
    pour éviter la surcharge d\'un seul.

-   **Failover automatique :** Basculement automatique vers un système
    de secours en cas de panne.

-   **Onduleur (UPS) :** Alimentation de secours en cas de coupure
    électrique.

-   **Redondance réseau :** Liaisons réseau multiples (double FAI, liens
    redondants entre switchs).

**▶ SPOF --- Single Point of Failure**

Un SPOF est un élément unique dont la panne entraîne l\'arrêt complet du
système. L\'objectif d\'une architecture haute disponibilité est
d\'éliminer tous les SPOF.

+-----------------------------------------------------------------------+
| **💡 Disponibilité vs Continuité d\'activité**                        |
+-----------------------------------------------------------------------+
| -   **Disponibilité :** Maintenir le service opérationnel en temps    |
|     normal grâce à la redondance                                      |
|                                                                       |
| -   **PCA (Plan de Continuité) :** Maintenir une activité minimale    |
|     lors d\'un sinistre majeur                                        |
|                                                                       |
| -   **PRA (Plan de Reprise) :** Procédures pour restaurer l\'activité |
|     normale après un sinistre                                         |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** Continuité de service : les utilisateurs peuvent travailler     |
| sans interruption, même en cas de panne matérielle                    |
|                                                                       |
| **✓** Haute disponibilité (HA) : basculement automatique transparent  |
| --- l\'utilisateur ne voit pas la panne                               |
|                                                                       |
| **✓** Load balancing : améliore à la fois la disponibilité ET les     |
| performances en distribuant la charge                                 |
|                                                                       |
| **✓** Mise à jour sans interruption : avec un cluster, on peut        |
| maintenir un nœud pendant que les autres assurent le service          |
|                                                                       |
| **✓** Satisfaction utilisateur et ROI : les interruptions coûtent     |
| cher (perte de productivité, ventes perdues, pénalités SLA)           |
|                                                                       |
| **✓** Architectures cloud : le cloud facilite la mise en œuvre de la  |
| haute disponibilité (multi-AZ, auto-scaling)                          |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** Coût élevé : doubler ou tripler les infrastructures pour la     |
| redondance représente un investissement important                     |
|                                                                       |
| **✗** Complexité accrue : plus de composants = plus de points         |
| potentiels de défaillance et plus de maintenance                      |
|                                                                       |
| **✗** La synchronisation des données entre nœuds peut introduire de   |
| la latence                                                            |
|                                                                       |
| **✗** 99,999% de disponibilité est très difficile à atteindre et      |
| requiert des investissements massifs                                  |
|                                                                       |
| **✗** Un mauvais déploiement en production peut affecter TOUS les     |
| nœuds simultanément (importance des tests)                            |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** L\'entreprise LogiTrans exige que son ERP soit disponible     |
| 99,9% du temps. Calculez le temps d\'arrêt annuel maximum autorisé.   |
| Proposez une architecture technique pour atteindre cet objectif.      |
|                                                                       |
| > *→ 99,9% = 8,76h/an max. Architecture : 2 serveurs en cluster       |
| > actif/passif, VIP (IP virtuelle), stockage partagé ou réplication,  |
| > load balancer, double alimentation, UPS.*                           |
+-----------------------------------------------------------------------+
| **Q2.** Qu\'est-ce qu\'un SPOF ? Identifiez les SPOF potentiels dans  |
| l\'architecture suivante : 1 routeur, 1 firewall, 1 switch, 2         |
| serveurs. Comment les éliminer ?                                      |
|                                                                       |
| > *→ SPOF : routeur, firewall, switch (chacun unique). Éliminer :     |
| > routeur redondant (HSRP/VRRP), firewall en HA actif/passif, switch  |
| > en stack ou LAG. Les 2 serveurs sont déjà redondants.*              |
+-----------------------------------------------------------------------+
| **Q3.** Expliquez la différence entre un cluster actif/actif et       |
| actif/passif. Donnez un exemple d\'utilisation pour chacun dans un    |
| contexte professionnel.                                               |
|                                                                       |
| > *→ Actif/actif : tous les nœuds traitent des requêtes → meilleures  |
| > perfs (serveurs web, BDD). Actif/passif : nœud de secours en        |
| > attente → plus simple, pour services critiques (firewall, serveur   |
| > de fichiers).*                                                      |
+-----------------------------------------------------------------------+
| **Q4.** L\'onduleur (UPS) d\'une salle serveurs vient de sonner       |
| l\'alarme. Le courant électrique est coupé. Décrivez les actions à    |
| mener dans l\'immédiat et à moyen terme.                              |
|                                                                       |
| > *→ Immédiat : vérifier autonomie restante, contacter le             |
| > gestionnaire bâtiment/électricien, prévenir les utilisateurs. Si    |
| > autonomie insuffisante : procédure d\'arrêt contrôlé dans l\'ordre  |
| > de priorité. Moyen terme : groupe électrogène, vérification UPS.*   |
+-----------------------------------------------------------------------+
| **Q5.** Dans le cadre d\'un projet de refonte de l\'infrastructure,   |
| on vous demande de justifier l\'investissement dans une solution de   |
| haute disponibilité auprès de la direction. Quels arguments           |
| financiers et opérationnels mettez-vous en avant ?                    |
|                                                                       |
| > *→ Coût d\'une heure d\'arrêt (calculer selon CA de l\'entreprise), |
| > pénalités SLA clients, perte de données, atteinte à la réputation.  |
| > Comparer au coût annuel de la solution HA.*                         |
+-----------------------------------------------------------------------+

> **13. Architecture Multisites**

  -----------------------------------------------------------------------
  ***📖 Cours***

  -----------------------------------------------------------------------

**▶ Définition**

Une architecture multisite désigne une organisation dont
l\'infrastructure informatique est répartie sur plusieurs sites
géographiques distincts. Cela répond à des besoins de disponibilité, de
performance et de continuité d\'activité.

**▶ Objectifs d\'une architecture multisite**

-   **Continuité d\'activité :** Si un site est sinistré (incendie,
    inondation), les autres sites prennent le relais

-   **Performance / proximité :** Rapprocher les services informatiques
    des utilisateurs locaux

-   **Répartition de charge :** Distribuer les traitements entre
    plusieurs datacenters

-   **Conformité légale :** Certaines données doivent rester dans
    certains pays (RGPD, données de santé)

**▶ Types de sites**

  ----------------------------------- -----------------------------------
  **Type**                            **Description**

  **Site actif/actif**                Les deux (ou plus) sites traitent
                                      des requêtes simultanément.
                                      Performances maximales. Complexité
                                      de synchronisation élevée.

  **Site actif/passif (cold           Le site secondaire est en attente
  standby)**                          et ne prend le relais qu\'en cas de
                                      panne. Moins coûteux mais temps de
                                      bascule long.

  **Site actif/passif (warm           Le site secondaire est
  standby)**                          partiellement en fonction, prêt à
                                      basculer rapidement.

  **Hot standby**                     Le site de secours est en
                                      production permanente, synchronisé
                                      en temps réel. Bascule
                                      quasi-instantanée.
  ----------------------------------- -----------------------------------

**▶ Technologies d\'interconnexion**

-   **VPN site-à-site (IPsec) :** Tunnel chiffré entre deux sites via
    Internet. Économique, adapté aux petites structures.

-   **MPLS (Multiprotocol Label Switching) :** Réseau privé de
    l\'opérateur, garanties de QoS (Quality of Service). Coûteux mais
    fiable.

-   **SD-WAN (Software-Defined WAN) :** Gestion intelligente des liens
    WAN multiples (Internet + MPLS), optimisation automatique du
    routage.

-   **Liaisons louées (LS) :** Liens dédiés point à point entre sites.
    Haute disponibilité, faible latence, très coûteux.

**▶ Synchronisation des données**

-   **Réplication Active Directory :** Entre contrôleurs de domaine sur
    différents sites --- gérée par les sites et services AD

-   **DFS (Distributed File System) :** Réplication de partages de
    fichiers entre sites

-   **Réplication de bases de données :** SQL Server Always On, Oracle
    Data Guard, MySQL Replication

-   **Réplication de virtualisation :** VMware vSphere Replication,
    Hyper-V Replica

+-----------------------------------------------------------------------+
| **🏗️ Exemple d\'architecture multisite type BTS**                     |
+-----------------------------------------------------------------------+
| -   **Siège (Paris) :** Datacenter principal, Active Directory        |
|     maître, ERP, serveurs applicatifs                                 |
|                                                                       |
| -   **Site secondaire (Lyon) :** Contrôleur AD secondaire, NAS de     |
|     sauvegarde, serveurs de secours                                   |
|                                                                       |
| -   **Interconnexion :** VPN IPsec redondant (2 FAI différents) ou    |
|     MPLS                                                              |
|                                                                       |
| -   **Objectifs atteints :** RTO \< 4h, RPO \< 1h, disponibilité      |
|     99,9%                                                             |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***✅ Avantages & Inconvénients***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **✅ Avantages**                                                      |
+-----------------------------------------------------------------------+
| **✓** Continuité d\'activité géographique : un sinistre sur un site   |
| n\'arrête pas toute l\'entreprise                                     |
|                                                                       |
| **✓** Proximité des utilisateurs : les services sont hébergés au plus |
| près des équipes locales → réduction de la latence                    |
|                                                                       |
| **✓** Répartition de charge : les traitements sont distribués entre   |
| les sites → meilleure montée en charge                                |
|                                                                       |
| **✓** Active Directory multisite : gestion centralisée des identités  |
| tout en optimisant le trafic d\'authentification local                |
|                                                                       |
| **✓** Flexibilité : capacité à ouvrir ou fermer des sites sans tout   |
| reconstruire                                                          |
|                                                                       |
| **✓** Conformité : données hébergées dans la région adéquate pour     |
| respecter les réglementations locales (RGPD)                          |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **⚠️ Inconvénients / Limites**                                        |
+-----------------------------------------------------------------------+
| **✗** Complexité de gestion : plus de sites = plus d\'équipements, de |
| liens, de procédures à maintenir                                      |
|                                                                       |
| **✗** Coût des liaisons : MPLS et liaisons dédiées sont coûteux,      |
| SD-WAN plus abordable mais à configurer                               |
|                                                                       |
| **✗** Synchronisation des données : la réplication entre sites doit   |
| être surveillée et peut être source de conflits                       |
|                                                                       |
| **✗** Latence inter-sites : pour des applications sensibles au temps  |
| de réponse, la distance géographique impacte les performances         |
|                                                                       |
| **✗** Sécurité périmétrique multipliée : chaque site est un vecteur   |
| d\'attaque potentiel à sécuriser                                      |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  ***🎯 Questions types d\'examen***

  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **🎯 Questions types BTS SIO SISR --- basées sur anciens sujets**     |
+-----------------------------------------------------------------------+
| **Q1.** L\'entreprise RetailPro dispose d\'un siège à Paris et de 5   |
| agences régionales. Proposez une architecture réseau pour             |
| interconnecter tous les sites de manière sécurisée et redondante.     |
| Justifiez le choix de technologie WAN.                                |
|                                                                       |
| > *→ Option 1 : VPN IPsec site-à-site avec 2 FAI différents           |
| > (redondance). Option 2 : MPLS opérateur pour QoS garantie. Option 3 |
| > : SD-WAN pour gérer intelligemment les deux. Critères : coût,       |
| > débit, SLA, QoS applicatif.*                                        |
+-----------------------------------------------------------------------+
| **Q2.** L\'entreprise dispose de deux sites (Paris et Lyon) avec      |
| Active Directory. Expliquez comment configurer AD pour optimiser      |
| l\'authentification des utilisateurs sur chaque site. Quels objets AD |
| configurez-vous ?                                                     |
|                                                                       |
| > *→ Sites et services Active Directory : créer des objets Site pour  |
| > Paris et Lyon, définir les sous-réseaux IP de chaque site, créer    |
| > des liens de site (site links) avec coût et réplication schedule.   |
| > Contrôleurs de domaine locaux sur chaque site.*                     |
+-----------------------------------------------------------------------+
| **Q3.** Le site secondaire de Lyon doit servir de plan de reprise     |
| pour le site de Paris en cas de sinistre. Quel type d\'architecture   |
| retenir (cold/warm/hot standby) ? Quel RTO peut-on atteindre avec     |
| chaque option ?                                                       |
|                                                                       |
| > *→ Cold standby : RTO \> 24h. Warm standby : RTO 2-8h (infra prête, |
| > données à restaurer). Hot standby : RTO \< 1h (synchronisation      |
| > temps réel, bascule automatique). Choisir selon criticité et        |
| > budget.*                                                            |
+-----------------------------------------------------------------------+
| **Q4.** Vous devez mettre en place la réplication des partages de     |
| fichiers entre le siège et les agences. Quelle solution Microsoft     |
| utilisez-vous ? Quels paramètres configurez-vous ? Quelles limites    |
| faut-il anticiper ?                                                   |
|                                                                       |
| > *→ DFS-R (Distributed File System Replication). Configurer :        |
| > namespace DFS, groupe de réplication, planification et bande        |
| > passante. Limites : conflits de réplication si fichier modifié      |
| > simultanément sur 2 sites, bande passante WAN.*                     |
+-----------------------------------------------------------------------+
| **Q5.** Le DSI vous demande de comparer VPN IPsec, MPLS et SD-WAN     |
| pour l\'interconnexion des 8 sites de l\'entreprise. Présentez une    |
| analyse comparative et une recommandation argumentée.                 |
|                                                                       |
| > *→ VPN IPsec : économique, sur Internet, moins de QoS garantie.     |
| > MPLS : QoS garantie, SLA opérateur, coûteux. SD-WAN : combine les   |
| > deux, routage intelligent, gestion centralisée, économique.         |
| > Recommandation SD-WAN si budget moyen et besoin de priorisation     |
| > applicative.*                                                       |
+-----------------------------------------------------------------------+

**TABLEAU RÉCAPITULATIF --- MÉMO FINAL**

*Les mots-clés essentiels à retenir pour chaque notion*

  ----------------------------------- -----------------------------------------
  **Notion**                          **Mots-clés essentiels**

  **PowerShell**                      Shell Microsoft .NET. Cmdlets
                                      (Verbe-Nom), scripts .ps1,
                                      ExecutionPolicy
                                      (Restricted/RemoteSigned/Unrestricted).

  **RAID 0**                          Performance, pas de redondance, perte
                                      totale si 1 disque tombe.

  **RAID 1**                          Miroir, 1 disque peut tomber, capacité =
                                      1 disque. Pas une sauvegarde !

  **RAID 5**                          Striping + parité, 3 disques min, 1 panne
                                      tolérée, capacité = (N-1) disques.

  **RAID 10**                         Miroir + stripe, 4 disques min,
                                      meilleures perfs + redondance. Coûteux.

  **HTTPS**                           HTTP + TLS, port 443, certificats,
                                      chiffrement client-serveur. Let\'s
                                      Encrypt = gratuit.

  **SSH**                             Accès distant sécurisé, port 22, remplace
                                      Telnet. Auth par clé = plus sécurisé.
                                      Fail2Ban.

  **IDS**                             Détecte les intrusions, génère des
                                      alertes. Mode passif. Snort, Suricata,
                                      OSSEC.

  **IPS**                             Détecte ET bloque. Mode inline. Risque
                                      faux positifs. Activer après phase IDS.

  **MitM**                            Interception des communications. ARP
                                      Poisoning, SSL Stripping, Evil Twin.
                                      Contre : HTTPS, VPN, DAI.

  **ITIL**                            Référentiel ITSM. Incident ≠ Problème ≠
                                      Changement. SLA, CAB, RCA, Service Desk.

  **Sauvegardes**                     Règle 3-2-1. RPO = perte max. RTO = délai
                                      de reprise. Full + incrémentale +
                                      différentielle.

  **Force brute**                     Teste tout. Lent. Contre : verrouillage
                                      de compte, MFA, politique de mdp forts.

  **Dictionnaire**                    Liste de mdp connus. Rapide. Contre : mdp
                                      complexes, salage, Fail2Ban.

  **Ransomware**                      Chiffre les fichiers, demande rançon.
                                      Prévention : sauvegardes hors ligne,
                                      sensibilisation.

  **Phishing**                        Email frauduleux. Reconnaître : URL
                                      douteuse, urgence, fautes, expéditeur
                                      suspect.

  **DDoS**                            Saturation depuis de nombreuses sources
                                      (botnet). Mitigation : FAI, CDN, IPS.

  **Chiffrement symétrique**          1 clé. AES-256. Rapide. Pour grands
                                      volumes de données. Problème : échange de
                                      clé.

  **Chiffrement asymétrique**         Clé pub + privée. RSA, ECDSA. Échanges de
                                      clés, signatures. Lent.

  **Hachage**                         Sens unique. SHA-256, Bcrypt. Intégrité,
                                      mots de passe. MD5/SHA-1 = obsolètes.

  **Disponibilité**                   3 neuf = 99,9% = 8,7h d\'arrêt/an max.
                                      HA, clustering, load balancing. Éliminer
                                      les SPOF.

  **Multisite**                       Sites actif/actif ou actif/passif. VPN
                                      IPsec, MPLS ou SD-WAN. AD multisite,
                                      DFS-R.
  ----------------------------------- -----------------------------------------