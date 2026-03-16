+-----------------------------------------------------------------------+
| **FICHE DE RÉVISION COMPLÈTE**                                        |
|                                                                       |
| **U6 -- CYBERSÉCURITÉ DES SERVICES INFORMATIQUES**                    |
|                                                                       |
| BTS SIO SISR -- Sessions 2023 \| Cas Ville du Parc & Saint-Jacques    |
+-----------------------------------------------------------------------+

+-----------------------------------------------------------------------+
| **Thèmes couverts dans cette fiche**                                  |
|                                                                       |
| ① RGPD & données personnelles ② EBIOS RM & analyse de risques ③       |
| Ransomwares ④ Résilience & PCA                                        |
|                                                                       |
| ⑤ VLAN & sécurité réseau ⑥ PowerShell Active Directory ⑦ HAProxy &    |
| certificats TLS ⑧ Sécurité des ports Cisco                            |
|                                                                       |
| ⑨ Réponse à incident (SANS) ⑩ VPN IPSec & PKI ⑪ DDoS & haute          |
| disponibilité ⑫ Filtrage pare-feu                                     |
+-----------------------------------------------------------------------+

  -----------------------------------------------------------------------
  **① RGPD & DONNÉES PERSONNELLES**

  -----------------------------------------------------------------------

**Les obligations clés à citer (toujours minimum 4 !)**

-   Minimisation des données : ne collecter QUE ce qui est strictement
    nécessaire à la finalité

-   Information et transparence : informer l\'usager de la collecte,
    finalité, durée, droits (accès, rectif, suppression)

-   Sécurité des données : mesures techniques ET organisationnelles
    (chiffrement, contrôle d\'accès\...)

-   Désignation d\'un DPO (Délégué à la Protection des Données) :
    OBLIGATOIRE pour tout organisme public

-   Limitation de la durée de conservation : pas au-delà de la finalité

-   Tenue d\'un registre des traitements : documenter tous les
    traitements de données personnelles

-   Droit d\'accès des personnes : communication de toutes les données
    les concernant, archivées ou non

**Notification de violation (Articles 33 & 34 RGPD) -- Processus
obligatoire**

+----------+-----------------------------------------------------------+
| **⚠      | Délai de notification à la CNIL : 72h maximum après avoir |
| PIÈGE**  | pris connaissance de la violation                         |
|          |                                                           |
|          | Si risque élevé pour les personnes → notifier AUSSI les   |
|          | personnes concernées, sans délai maximal fixé mais le     |
|          | plus tôt possible                                         |
+----------+-----------------------------------------------------------+

+----------+-----------------------------------------------------------+
| **       | Étape 1 → Détection de la violation et évaluation de la   |
| 117A65** | gravité                                                   |
|          |                                                           |
|          | Étape 2 → Notification à la CNIL dans les 72h (portail    |
|          | notifications.cnil.fr) : nature de la violation, données  |
|          | concernées, nombre de personnes, conséquences, mesures    |
|          | prises                                                    |
|          |                                                           |
|          | Étape 3 → Si risque élevé : notification aux personnes    |
|          | concernées                                                |
|          |                                                           |
|          | Étape 4 → Documentation interne (accountability)          |
+----------+-----------------------------------------------------------+

**Contenu de la notification CNIL :**

-   Nature de la violation (exfiltration, chiffrement, perte\...)

-   Catégories et volume de données concernées

-   Nombre approximatif de personnes touchées

-   Conséquences probables

-   Mesures prises ou envisagées pour y remédier

+----------+-----------------------------------------------------------+
| **A      | Collectivités territoriales : soumises aussi au Code du   |
| RCHIVAGE | Patrimoine pour l\'archivage public                       |
| PUBLIC** |                                                           |
|          | Actes d\'état civil → conservés 100 ans minimum \|        |
|          | Délibérations du conseil municipal → conservées           |
|          | définitivement                                            |
|          |                                                           |
|          | Toute consultation de données archivées doit être TRACÉE  |
|          | (journalisée)                                             |
+----------+-----------------------------------------------------------+

**Conséquences d\'une faille -- Structure de réponse type**

  -----------------------------------------------------------------------
  **Pour qui ?**     **Conséquences**
  ------------------ ----------------------------------------------------
  La mairie          Amende CNIL jusqu\'à 20M€ \| Atteinte à la
                     réputation \| Perte de confiance des habitants \|
                     Poursuites judiciaires

  Les usagers        Usurpation d\'identité \| Spear phishing ciblé \|
                     Exposition de données sensibles (revenus, état
                     civil\...)
  -----------------------------------------------------------------------

  -----------------------------------------------------------------------
  **② MÉTHODE EBIOS RM -- ANALYSE DE RISQUES**

  -----------------------------------------------------------------------

  ---------------- ------------------------------------------------------------
  **DÉFINITION**   EBIOS RM (Expression des Besoins et Identification des
                   Objectifs de Sécurité -- Risk Manager) est la méthode de
                   l\'ANSSI pour identifier, évaluer et traiter les risques
                   numériques. Elle se concentre sur les MENACES
                   INTENTIONNELLES.

  ---------------- ------------------------------------------------------------

**Les 5 ateliers EBIOS RM**

  ---------------------------------------------------------------------------
  **N°**   **Atelier**      **Ce qu\'on y fait**
  -------- ---------------- -------------------------------------------------
  1        Cadrage & socle  Recenser les valeurs métier (infos et processus
           de sécurité      importants), les besoins de sécurité (D/I/C), les
                            biens supports, identifier les événements
                            redoutés

  2        Sources de       Identifier les acteurs malveillants et leurs
           risques          objectifs

  3        Scénarios        Identifier les parties prenantes vulnérables,
           stratégiques     construire des chemins d\'attaque stratégiques

  4        Scénarios        Détailler les modes opératoires techniques
           opérationnels    (comment l\'attaque se passe concrètement)

  5        Traitement du    Définir les mesures de sécurité à mettre en
           risque           œuvre, construire la stratégie de traitement
  ---------------------------------------------------------------------------

**Matrice des risques -- Comment la remplir**

+----------+-----------------------------------------------------------+
| **À      | Axe X = Vraisemblance (probabilité que l\'attaque se      |
| R        | produise) : de 1 (Minimal) à 4 (Maximal)                  |
| ETENIR** |                                                           |
|          | Axe Y = Gravité (impact sur le SI et l\'organisation) :   |
|          | de 1 (Négligeable) à 4 (Critique)                         |
|          |                                                           |
|          | Zone rouge (haut droite) = risque inacceptable → mesures  |
|          | obligatoires                                              |
|          |                                                           |
|          | Zone orange = risque important → mesures à planifier      |
|          |                                                           |
|          | Zone verte (bas gauche) = risque acceptable               |
+----------+-----------------------------------------------------------+

+----------+-----------------------------------------------------------+
| **⚠      | Ne pas confondre Gravité et Vraisemblance !               |
| PIÈGE    |                                                           |
| CLA      | GRAVITÉ = l\'impact SI le scénario se produit (D/I/C      |
| SSIQUE** | affectés, services arrêtés, données perdues\...)          |
|          |                                                           |
|          | VRAISEMBLANCE = la probabilité que le scénario se         |
|          | produise (historique, contexte, cibles similaires\...)    |
+----------+-----------------------------------------------------------+

**Évaluer Gravité et Vraisemblance -- Méthode argumentée**

+----------+-----------------------------------------------------------+
| **       | Gravité CRITIQUE (4) → attaque sur les serveurs centraux  |
| 1E8449** | = tout le SI affecté (1200 postes, 60 serveurs, tous les  |
|          | services)                                                 |
|          |                                                           |
|          | Vraisemblance ÉLEVÉE (3-4) → citer des statistiques ! Ex  |
|          | : \'20% des ransomwares 2021 = Ryuk\' \| Les              |
|          | collectivités sont des cibles reconnues                   |
|          |                                                           |
|          | Argument D/I/C à toujours développer :                    |
|          |                                                           |
|          | • Disponibilité : serveurs chiffrés → services            |
|          | inaccessibles, interruption totale                        |
|          |                                                           |
|          | • Intégrité : fichiers modifiés/chiffrés → données        |
|          | inexploitables                                            |
|          |                                                           |
|          | • Confidentialité : données potentiellement exfiltrées →  |
|          | risque RGPD                                               |
+----------+-----------------------------------------------------------+

**Mesures de résilience (liste à connaître par cœur)**

-   Infrastructure réseau redondée : 2 sites géographiques distincts
    avec 2 cœurs de réseau

-   Cluster de serveurs (ESX) avec failover automatique

-   Baies SAN en RAID 50 avec réplication inter-sites en temps réel

-   Protocole RSTP sur tous les commutateurs (topologie sans boucle et
    redondante)

-   Sauvegardes VeeamBackup : complètes + incrémentielles, chiffrées,
    hors ligne, sur 2 sites

-   Exercices de restauration réguliers pour vérifier les sauvegardes

-   Locaux sécurisés : badge + biométrie, vidéosurveillance, alarme
    incendie, UPS, double climatisation

-   Pare-feux et proxies pour filtrer les flux, centralisation des logs

  -----------------------------------------------------------------------
  **③ RANSOMWARES -- TOUT CE QU\'IL FAUT SAVOIR**

  -----------------------------------------------------------------------

**Chaîne d\'infection Bazar-Ryuk (à connaître)**

+----------+-----------------------------------------------------------+
| **       | ① Courriel de phishing contenant un lien malveillant      |
| 922B21** |                                                           |
|          | ② Clic → téléchargement du malware BazarLoader            |
|          |                                                           |
|          | ③ BazarLoader contacte son serveur C2 (Command & Control) |
|          | → télécharge une backdoor                                 |
|          |                                                           |
|          | ④ Élévation de privilèges (tools : CobaltStrike,          |
|          | Mimikatz, Metasploit, SDBBot)                             |
|          |                                                           |
|          | ⑤ Déploiement du ransomware Ryuk → chiffrement de tous    |
|          | les fichiers (AES-256)                                    |
|          |                                                           |
|          | ⑥ Clé AES chiffrée avec clé RSA publique Ryuk →           |
|          | impossibilité de déchiffrer sans payer                    |
|          |                                                           |
|          | Délai entre infection et chiffrement : entre 3h et 5      |
|          | jours (Ryuk)                                              |
+----------+-----------------------------------------------------------+

**Caractéristiques clés de Ryuk**

-   Extension ajoutée aux fichiers chiffrés : .RYK

-   Note de rançon : RyukReadMe.txt déposé dans chaque dossier chiffré

-   Persistance via clé de registre :
    HKCU\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Run\\svchost

-   Propagation réseau : scanne 10.0.0.0/8 \| 172.16.0.0/16 →
    172.31.0.0/16 \| 192.168.0.0/16

-   Tente d\'arrêter 180 services et 40 processus (antivirus,
    sauvegardes en priorité !)

-   N\'exfiltre PAS les données (contrairement à d\'autres ransomwares)

-   Groupe : Wizard Spider / UNC1878 (83% des infections Ryuk)

**Équipements pouvant être infectés (liste complète)**

-   Postes de travail des agents (PC bureau, laptops) -- vecteur
    d\'entrée initial

-   Serveurs de fichiers et de virtualisation -- cibles principales
    (données critiques)

-   Serveurs applicatifs (Active Directory, DHCP, messagerie) --
    propagation

-   NAS et systèmes de stockage réseau -- si accessibles depuis le
    réseau infecté

-   Postes publics -- si mal cloisonnés du réseau interne

+----------+-----------------------------------------------------------+
| **✗ NE   | Les équipements réseau purs (commutateurs, routeurs) sont |
| PAS      | généralement épargnés car ils n\'ont pas de système de    |
| O        | fichiers standard.                                        |
| UBLIER** |                                                           |
|          | Les serveurs de sauvegarde sont des cibles PRIORITAIRES   |
|          | pour Ryuk (il les arrête en premier !)                    |
+----------+-----------------------------------------------------------+

**Solutions de protection -- classifiées par vecteur**

  -----------------------------------------------------------------------
  **Vecteur             **Solutions de protection**
  d\'infection**        
  --------------------- -------------------------------------------------
  Clé USB               Désactivation ports USB via GPO/BIOS \| Device
                        Control (DLP/EDR) \| Clés USB sur liste blanche
                        uniquement \| Procédure de décontamination
                        obligatoire

  Courriel / lien piégé Secure Email Gateway (sandbox des liens) \| Proxy
                        web avec filtrage URL et réputation \| Anti-spam
                        avec analyse des pièces jointes \|
                        Formation/sensibilisation phishing

  Propagation réseau    Segmentation VLAN \| Principe du moindre
                        privilège \| Désactivation des comptes admin
                        partagés \| MFA sur les comptes à privilèges

  Application Guard &   Application Guard : isolation automatique des
  Sandbox               sites/fichiers non approuvés (transparent pour
                        l\'utilisateur) \| Sandbox : isolation manuelle,
                        nécessite action de l\'utilisateur
  -----------------------------------------------------------------------

+----------+-----------------------------------------------------------+
| **À      | Application Guard \> Sandbox en termes d\'efficacité car  |
| R        | il agit automatiquement sans intervention de              |
| ETENIR** | l\'utilisateur.                                           |
|          |                                                           |
|          | Application Guard réduit À LA FOIS la gravité ET la       |
|          | vraisemblance. La Sandbox réduit surtout la gravité.      |
+----------+-----------------------------------------------------------+

  -----------------------------------------------------------------------
  **④ RÉPONSE À INCIDENT -- MODÈLE SANS (6 PHASES)**

  -----------------------------------------------------------------------

  ----------------------------------------------------------------------------
  **\#**   **Phase**        **Description et actions clés**
  -------- ---------------- --------------------------------------------------
  1        Préparation      Exercices simulés d\'attaques, procédures
                            documentées et testées. Mettre en place les outils
                            de détection AVANT l\'incident.

  2        Identification   Comprendre la CAUSE PREMIÈRE, évaluer la portée
                            (quelles machines ?), collecter les IoC
                            (Indicateurs de Compromission). Ne pas
                            réinitialiser immédiatement la machine infectée !

  3        Confinement      Isoler les machines compromises du réseau pour
                            stopper la propagation. Court terme (isoler) puis
                            long terme (analyse approfondie, image disque).

  4        Éradication      Supprimer le malware, désactiver les comptes
                            compromis, appliquer les correctifs, supprimer les
                            clés de registre et tâches planifiées
                            malveillantes.

  5        Retour à la      Restaurer depuis une sauvegarde saine. Remettre
           normale          les services en production. Surveiller les
                            machines affectées.

  6        Enseignements    Réunion post-incident (Post Incident Review).
                            Analyser ce qui a fonctionné, modifier le plan de
                            réponse et les procédures.
  ----------------------------------------------------------------------------

+----------+-----------------------------------------------------------+
| **⚠      | Phase 2 (Identification) : NE PAS réinitialiser le        |
| ERREUR   | premier poste infecté immédiatement !                     |
| F        |                                                           |
| RÉQUENTE | Il faut d\'abord collecter les IoC pour rechercher        |
| PHASE    | d\'autres machines infectées dans tout le SI.             |
| 2**      |                                                           |
|          | Chercher : quelles connexions réseau le malware           |
|          | génère-t-il ? Quels fichiers créés ? Quels processus ?    |
|          | Quelles clés de registre ?                                |
+----------+-----------------------------------------------------------+

**Indicateurs de compromission (IoC) -- Comment les utiliser**

+----------+-----------------------------------------------------------+
| **✓      | 1\. Relever les adresses IP suspectes dans les journaux   |
| MÉTHODE  | du proxy/pare-feu                                         |
| IOC**    |                                                           |
|          | 2\. Comparer avec les IoC connus du malware (documents    |
|          | fournis dans l\'annexe !)                                 |
|          |                                                           |
|          | 3\. Si correspondance → INCIDENT CONFIRMÉ (pas un faux    |
|          | positif)                                                  |
|          |                                                           |
|          | 4\. Rechercher ces mêmes IoC dans les journaux de TOUTES  |
|          | les autres machines du SI                                 |
|          |                                                           |
|          | 5\. Identifier toutes les machines ayant communiqué avec  |
|          | les mêmes IP malveillantes                                |
|          |                                                           |
|          | Exemple Ryuk : IoC = connexion vers 34.217.209.239:443    |
|          | GET /www/html/var/generic/doc                             |
+----------+-----------------------------------------------------------+

**Mesures d\'éradication -- Liste exhaustive**

-   Scanner le poste avec un antivirus à jour + outils forensiques

-   Supprimer les fichiers malveillants (BazarLoader, backdoor, etc.)

-   Supprimer les clés de registre créées par le malware (Run,
    RunOnce\...)

-   Supprimer les tâches planifiées malveillantes

-   Changer les mots de passe de tous les comptes potentiellement
    compromis

-   Appliquer tous les correctifs de sécurité (OS + logiciels)

-   Si doute → réinstallation complète du poste depuis une image propre

-   Restaurer les données depuis une sauvegarde saine ANTÉRIEURE à
    l\'infection

**Mesures anti-phishing complémentaires (3 à citer)**

-   Secure Email Gateway : analyse sandbox des liens et PJ avant
    livraison en boîte mail

-   Filtrage DNS / Proxy avec blacklists : bloque l\'accès aux domaines
    malveillants connus

-   Authentification multifacteur (MFA) : même si le mot de passe est
    volé, l\'attaquant ne peut pas se connecter seul

-   DMARC/DKIM/SPF : empêche l\'usurpation du domaine expéditeur de la
    mairie

-   Campagnes de phishing simulées : tester et former les utilisateurs
    régulièrement

  -----------------------------------------------------------------------
  **⑤ RÉSILIENCE, PCA & SAUVEGARDES**

  -----------------------------------------------------------------------

**Règle 3-2-1 des sauvegardes (à citer absolument)**

+----------+-----------------------------------------------------------+
| **RÈGLE  | 3 copies des données (la production + 2 sauvegardes)      |
| 3-2-1**  |                                                           |
|          | 2 types de supports différents (ex : disque local + bande |
|          | ou cloud)                                                 |
|          |                                                           |
|          | 1 copie hors site géographiquement distincte (protection  |
|          | contre sinistre physique)                                 |
+----------+-----------------------------------------------------------+

**Réplication ≠ Sauvegarde -- Ne pas confondre !**

+----------+-----------------------------------------------------------+
| **✗      | La RÉPLICATION garantit la DISPONIBILITÉ sur un second    |
| PIÈGE    | site (copie en temps réel ou différée).                   |
| CLA      |                                                           |
| SSIQUE** | Elle ne protège PAS contre la corruption des données : si |
|          | des données sont corrompues ou chiffrées par un           |
|          | ransomware, la corruption est aussi répliquée !           |
|          |                                                           |
|          | Seule une SAUVEGARDE avec HISTORISATION permet de revenir |
|          | à un état sain antérieur.                                 |
|          |                                                           |
|          | Cas concret : données compromises un mercredi → si seule  |
|          | la dernière sauvegarde complète (dimanche) est conservée, |
|          | et qu\'elle a été écrasée par la sauvegarde du dimanche   |
|          | suivant → PERTE DE DONNÉES.                               |
+----------+-----------------------------------------------------------+

**Fréquence d\'historisation -- Comment l\'évaluer**

+----------+-----------------------------------------------------------+
| **✓      | Se demander : combien de temps APRÈS une compromission    |
| M        | peut-on la découvrir ?                                    |
| ÉTHODE** |                                                           |
|          | Si découverte possible 3 jours après → conserver AU       |
|          | MINIMUM 1 semaine de sauvegardes                          |
|          |                                                           |
|          | Bonne pratique : 4 sauvegardes complètes (4 derniers      |
|          | dimanches) + incrémentielles de la semaine                |
|          |                                                           |
|          | Archivage mensuel (pas uniquement annuel) stocké hors     |
|          | site                                                      |
+----------+-----------------------------------------------------------+

**Défauts classiques d\'un plan de réplication**

-   Réplication hebdomadaire des VMs trop espacée → jusqu\'à 7 jours de
    données perdues en cas de sinistre

-   Réplication semestrielle des données d\'école → 6 mois de données
    perdues potentielles

-   Absence de réplication des fichiers vidéo de police → perte de
    preuves judiciaires

-   Lieu de sauvegarde unique → si attaque simultanée des deux sites →
    perte totale

-   Une seule sauvegarde complète conservée → impossible de revenir à un
    état antérieur

**Solution si lien inter-site unique (point de défaillance)**

-   Déployer un accès internet autonome sur le site de secours (FAI
    différent du site principal)

-   En cas de coupure du lien principal → VPN IPSec site à site via
    internet comme lien de repli

-   Diversification des opérateurs : FAI différent pour chaque site

**Comparaison postes de crise : publics reconfigurés vs dédiés**

  ------------------------------------------------------------------------
  **Critère**      **Postes publics            **Postes dédiés (salle
                   reconfigurés**              technique)**
  ---------------- --------------------------- ---------------------------
  Disponibilité    Déjà présents mais          Prêts à l\'emploi,
                   reconfiguration nécessaire  déploiement immédiat
                   → lent en période de crise  

  Sécurité         ⚠ RISQUE ÉLEVÉ :            ✓ Contrôlés par l\'équipe
                   potentiellement compromis   IT, jamais exposés au
                   (usage public), historique  public
                   non maîtrisé                

  Coût             Faible (existants)          Plus élevé (achat dédié,
                                               non utilisés en temps
                                               normal)
  ------------------------------------------------------------------------

  ----------- ------------------------------------------------------------
  **À         Recommandation : postes dédiés car la sécurité des données
  RETENIR**   critiques est prioritaire en période de crise.

  ----------- ------------------------------------------------------------

  -----------------------------------------------------------------------
  **⑥ SÉCURITÉ RÉSEAU -- VLAN & CLOISONNEMENT**

  -----------------------------------------------------------------------

**VLAN par adresse MAC vs VLAN par port -- Différence cruciale**

  ------------------------------------------------------------------------
  **Critère**        **VLAN par adresse MAC**   **VLAN par port
                                                (Port-Based VLAN)**
  ------------------ -------------------------- --------------------------
  Principe           Le VLAN est déterminé par  Le VLAN est déterminé par
                     l\'adresse MAC de la carte le port physique du
                     réseau                     commutateur

  Sécurité           ⚠ FAIBLE : les adresses    ✓ ÉLEVÉE : impossible de
                     MAC sont facilement        changer de VLAN en
                     usurpables (MAC spoofing)  modifiant l\'adresse MAC
                     via des outils logiciels   
                     gratuits                   

  Configuration      Liée à l\'identité de la   Liée au câble physique
                     machine                    

  Usage recommandé   À ÉVITER en production     Standard recommandé
  ------------------------------------------------------------------------

+----------+-----------------------------------------------------------+
| **À      | VLAN par port = la sécurité vient du câble physique, pas  |
| R        | de la machine. Même en branchant une autre machine sur la |
| ETENIR** | prise publique, elle reste dans le VLAN public.           |
|          |                                                           |
|          | Sans ajout de matériel supplémentaire : utiliser les      |
|          | commutateurs de niveau 3 déjà en place.                   |
+----------+-----------------------------------------------------------+

**Port-Security Cisco -- Commandes à connaître par cœur**

  -----------------------------------------------------------------------
  Switch# configure terminal

  ! Sécurisation des ports actifs (ex : fa0/1 à fa0/38)

  Switch(config)# interface range fa0/1 - 38

  Switch(config-if-range)# switchport mode access

  Switch(config-if-range)# switchport port-security

  Switch(config-if-range)# switchport port-security maximum 1

  Switch(config-if-range)# switchport port-security mac-address sticky

  Switch(config-if-range)# switchport port-security violation shutdown

  Switch(config-if-range)# exit

  ! Désactivation des ports inutilisés (ex : fa0/39 à fa0/42)

  Switch(config)# interface range fa0/39 - 42

  Switch(config-if-range)# switchport mode access

  Switch(config-if-range)# shutdown

  Switch(config-if-range)# exit

  Switch(config)# exit

  Switch# write memory
  -----------------------------------------------------------------------

+----------+-----------------------------------------------------------+
| **MODES  | sticky : apprend automatiquement la 1ère adresse MAC      |
| DE       | connectée et la mémorise → pas besoin de collecter        |
| VIO      | manuellement les adresses MAC                             |
| LATION** |                                                           |
|          | violation shutdown : désactive le port si une adresse MAC |
|          | non autorisée est détectée                                |
|          |                                                           |
|          | violation protect : bloque le trafic des adresses         |
|          | inconnues sans désactiver le port                         |
|          |                                                           |
|          | violation restrict : comme protect + envoie une alerte    |
|          | SNMP + incrémente un compteur de violations               |
+----------+-----------------------------------------------------------+

**Analyse d\'une capture Wireshark -- Identifier une attaque SYN Flood**

+----------+-----------------------------------------------------------+
| **✓      | Symptôme observable : des milliers de paquets SYN vers la |
| MÉTHODE  | même adresse IP SANS ACK de retour                        |
| WIR      |                                                           |
| ESHARK** | Cause : attaque DoS de type SYN Flood -- le serveur       |
|          | réserve des ressources pour chaque SYN sans jamais        |
|          | recevoir le ACK final                                     |
|          |                                                           |
|          | Conséquence : saturation de la table des connexions → le  |
|          | serveur ne peut plus traiter de connexions légitimes      |
|          |                                                           |
|          | Source probable : machine connectée physiquement au       |
|          | réseau local (intérieur du réseau)                        |
+----------+-----------------------------------------------------------+

+----------+-----------------------------------------------------------+
| **       | Rappel du 3-Way Handshake TCP :                           |
| 117A65** |                                                           |
|          | 1\. Client → Serveur : SYN (demande de connexion)         |
|          |                                                           |
|          | 2\. Serveur → Client : SYN-ACK (acceptation)              |
|          |                                                           |
|          | 3\. Client → Serveur : ACK (confirmation)                 |
|          |                                                           |
|          | Sans le dernier ACK → le serveur réserve la connexion     |
|          | indéfiniment → SYN Flood exploite cela                    |
+----------+-----------------------------------------------------------+

**DDoS -- Points essentiels**

-   DDoS = Distributed Denial of Service : saturation des ressources
    d\'une cible depuis un réseau de machines zombies (botnet)

-   Objectif : rendre le service indisponible pour les utilisateurs
    légitimes

-   Types : SYN Flood, UDP Flood, HTTP Flood, amplification DNS/NTP

-   Pare-feux seuls : INSUFFISANTS contre le DDoS (peuvent être saturés
    eux-mêmes en amont)

-   Protection efficace : solutions anti-DDoS chez l\'opérateur/FAI ou
    scrubbing center, en amont du pare-feu

  -----------------------------------------------------------------------
  **⑦ HAPROXY, HAUTE DISPONIBILITÉ & CERTIFICATS TLS**

  -----------------------------------------------------------------------

**HAProxy -- Rôle et justification**

-   Load balancer (répartiteur de charge) open source pour TCP/HTTP

-   Répartit les requêtes entre plusieurs serveurs web (algorithme
    Round-Robin par défaut)

-   Élimine les SPOF (Single Point of Failure) : si un serveur tombe,
    les requêtes sont redirigées

-   Peut détecter et bloquer les attaques DDoS et les tentatives de
    force brute

-   Journalisation avancée pour détecter les intrusions

-   Architecture : Frontend (écoute) → Backend (serveurs web)

+----------+-----------------------------------------------------------+
| **⚠      | Il faut TOUJOURS doubler les serveurs HAProxy !           |
| PIÈGE**  |                                                           |
|          | Sans redondance, HAProxy lui-même est un SPOF : s\'il     |
|          | tombe, TOUS les services web tombent.                     |
|          |                                                           |
|          | Solution : 2 HAProxy en actif/passif avec VRRP/keepalived |
|          | (IP virtuelle flottante)                                  |
+----------+-----------------------------------------------------------+

**Stratégies de certificats TLS avec HAProxy**

  -------------------------------------------------------------------------
  **Stratégie**   **Certificat sur\...**       **Chiffrement jusqu\'où ?**
  --------------- ---------------------------- ----------------------------
  A --            Serveur(s) HAProxy           HTTPS du client jusqu\'à
  Terminaison TLS uniquement                   HAProxy. Entre HAProxy et
                                               les serveurs web : HTTP non
                                               chiffré (risque si réseau
                                               interne compromis)

  B --            Chaque serveur web backend   HTTPS de bout en bout
  Pass-Through                                 (client → serveurs web).
  TLS                                          HAProxy transmet sans
                                               déchiffrer → ne peut pas
                                               inspecter le contenu
  -------------------------------------------------------------------------

+----------+-----------------------------------------------------------+
| **À      | Pourquoi une mairie DOIT utiliser un certificat d\'une AC |
| R        | publique de confiance ?                                   |
| ETENIR** |                                                           |
|          | → Un certificat auto-signé n\'est pas reconnu par les     |
|          | navigateurs (avertissement de sécurité affiché aux        |
|          | utilisateurs)                                             |
|          |                                                           |
|          | → Seul un certificat d\'AC reconnue prouve                |
|          | l\'authenticité du site de la mairie (protection contre   |
|          | les sites frauduleux)                                     |
|          |                                                           |
|          | → Le RGPD impose la sécurisation des données personnelles |
|          | en transit → HTTPS obligatoire                            |
+----------+-----------------------------------------------------------+

**Règles de filtrage pare-feu -- Comment les écrire**

+----------+-----------------------------------------------------------+
| **✓      | Structure d\'une règle : N° \| Source \| Destination \|   |
| MÉTHODE  | Port/Protocole \| Action                                  |
| RÈGLES** |                                                           |
|          | Toujours spécifier le sens du trafic (ex : DMZ → VLAN_WEB |
|          | \| VPN → DMZ)                                             |
|          |                                                           |
|          | La règle de blocage total par défaut est IMPLICITE (ne    |
|          | pas l\'écrire)                                            |
|          |                                                           |
|          | En mode stateful : les règles de RETOUR sont implicites   |
|          | (ne pas les écrire non plus)                              |
|          |                                                           |
|          | Exemple HAProxy → Serveurs web (VLAN55) :                 |
|          |                                                           |
|          | → TCP port 80 si stratégie A (terminaison TLS)            |
|          |                                                           |
|          | → TCP port 443 si stratégie B (pass-through)              |
+----------+-----------------------------------------------------------+

  -----------------------------------------------------------------------
  **⑧ POWERSHELL ACTIVE DIRECTORY -- SCRIPTS**

  -----------------------------------------------------------------------

**Propriétés objet utilisateur AD à connaître**

  -----------------------------------------------------------------------
  **Propriété**            **Signification**
  ------------------------ ----------------------------------------------
  PasswordLastSet          Date de la DERNIÈRE MODIFICATION du mot de
                           passe

  LastLogonDate            Date de la DERNIÈRE CONNEXION du compte

  AccountExpirationDate    Date d\'expiration du compte

  PasswordNeverExpires     Si true = le mot de passe n\'expire jamais

  CannotChangePassword     Si true = l\'utilisateur ne peut pas changer
                           son mot de passe

  LogonCount               Nombre de connexions du compte

  Enabled                  Si true = compte actif
  -----------------------------------------------------------------------

**Structure de base d\'un script PowerShell AD**

  -----------------------------------------------------------------------
  \# Définir le seuil de date

  \$seuil = (Get-Date).AddDays(-365) \# 1 an

  \# Récupérer les membres d\'un groupe AD

  Get-ADGroupMember -Identity \'Nom du groupe\' -Recursive \|

  Get-ADUser -Properties PasswordLastSet, LastLogonDate \|

  Where-Object { \$\_.PasswordLastSet -lt \$seuil } \|

  Select-Object Name, SamAccountName, PasswordLastSet

  \# Opérateurs de comparaison PowerShell :

  \# -lt = inférieur à (less than)

  \# -gt = supérieur à (greater than)

  \# -eq = égal à (equal)

  \# -ne = différent de (not equal)

  \# -and = ET logique \| -or = OU logique
  -----------------------------------------------------------------------

+----------+-----------------------------------------------------------+
| **⚠      | Mot de passe non changé depuis X jours → utiliser la      |
| ERREURS  | propriété PasswordLastSet (pas LastLogonDate !)           |
| FRÉQ     |                                                           |
| UENTES** | Compte non connecté depuis X jours → utiliser             |
|          | LastLogonDate                                             |
|          |                                                           |
|          | Groupe \'Administrateurs de l\'entreprise\' ≠ \'Admins du |
|          | domaine\' : deux groupes distincts dans AD !              |
|          |                                                           |
|          | Toujours utiliser -Recursive pour Get-ADGroupMember pour  |
|          | inclure les sous-groupes                                  |
+----------+-----------------------------------------------------------+

**Recommandations ANSSI sur les mots de passe**

  -----------------------------------------------------------------------
  **Recommandation**    **Explication**
  --------------------- -------------------------------------------------
  R24 -- Comptes        Ne PAS imposer de délai d\'expiration si le mot
  standards             de passe est robuste et les systèmes le
                        permettent

  R25 -- Comptes à      IMPOSER un délai d\'expiration entre 1 et 3 ans
  privilèges            

  En cas de             Expiration IMMÉDIATE des mots de passe des
  compromission         comptes concernés
  -----------------------------------------------------------------------

+----------+-----------------------------------------------------------+
| **✗ À    | Durée trop courte (\< 1 mois) : contre-productif ! Les    |
| ÉVITER** | utilisateurs choisissent des mots de passe faibles et     |
|          | prévisibles (Mdp_janvier → Mdp_fevrier), ou notent leurs  |
|          | MDP.                                                      |
|          |                                                           |
|          | Durée illimitée pour les comptes à privilèges :           |
|          | inacceptable ! Un MDP compromis donne un accès persistant |
|          | à l\'attaquant.                                           |
+----------+-----------------------------------------------------------+

  -----------------------------------------------------------------------
  **⑨ VPN IPSec & INFRASTRUCTURE À CLÉS PUBLIQUES (PKI)**

  -----------------------------------------------------------------------

**Objectifs de sécurité garantis par un VPN**

  -----------------------------------------------------------------------
  **Objectif**       **Description**
  ------------------ ----------------------------------------------------
  Confidentialité    Données chiffrées en transit (AES, ChaCha20\...) →
                     interception impossible

  Intégrité          HMAC garantit que les données n\'ont pas été
                     modifiées → toute altération est détectée

  Authentification   Les deux extrémités s\'authentifient mutuellement →
                     protection contre le Man-in-the-Middle

  Non-répudiation    Avec certificats : impossible de nier avoir
                     participé à l\'échange
  -----------------------------------------------------------------------

**Les deux phases IKE du VPN IPSec**

+----------+-----------------------------------------------------------+
| **       | PHASE 1 (IKE) : Établissement du canal sécurisé de        |
| 117A65** | négociation                                               |
|          |                                                           |
|          | → Négociation des algorithmes de                          |
|          | chiffrement/authentification                              |
|          |                                                           |
|          | → Authentification mutuelle (certificats ou PSK)          |
|          |                                                           |
|          | → Résultat : tunnel ISAKMP-SA (IKEv1) ou PARENT-SA        |
|          | (IKEv2) chiffré                                           |
|          |                                                           |
|          | PHASE 2 (IPSec) : Établissement des tunnels de données    |
|          |                                                           |
|          | → Négociation du profil de chiffrement des données et des |
|          | réseaux autorisés                                         |
|          |                                                           |
|          | → Création de DEUX canaux (un par sens) avec deux clés    |
|          | différentes :                                             |
|          |                                                           |
|          | • ESP-SA1 (IKEv1) ou CHILD-SA1 (IKEv2) : clé pour le sens |
|          | Mairie → Site secours                                     |
|          |                                                           |
|          | • ESP-SA2 (IKEv1) ou CHILD-SA2 (IKEv2) : clé pour le sens |
|          | Site secours → Mairie                                     |
|          |                                                           |
|          | → Chaque extrémité possède les 2 clés : une pour          |
|          | CHIFFRER, une pour DÉCHIFFRER                             |
+----------+-----------------------------------------------------------+

+----------+-----------------------------------------------------------+
| **⚠      | Les 2 clés symétriques (ESP-SA1 et ESP-SA2) sont          |
| POINT    | DIFFÉRENTES ! Une par sens de communication.              |
| CLÉ      |                                                           |
| SOUVENT  | Ce n\'est PAS une clé asymétrique : les deux parties      |
| MAL      | connaissent les deux clés symétriques.                    |
| C        |                                                           |
| OMPRIS** | ESP-SA1 : Mairie CHIFFRE avec cette clé → Site secours    |
|          | DÉCHIFFRE avec cette clé                                  |
|          |                                                           |
|          | ESP-SA2 : Site secours CHIFFRE avec cette clé → Mairie    |
|          | DÉCHIFFRE avec cette clé                                  |
+----------+-----------------------------------------------------------+

**PKI vs PSK -- Comparaison à maîtriser**

  -----------------------------------------------------------------------
  **Critère**         **PKI / IGC               **PSK (clé
                      (certificats)**           pré-partagée)**
  ------------------- ------------------------- -------------------------
  Ajout d\'un         Facile : émettre un       Complexe : reconfigurer
  équipement          nouveau certificat depuis tous les autres
                      l\'AC → aucune modif sur  équipements avec la
                      les autres                nouvelle PSK

  Révocation en cas   Rapide : révoquer le      Lente et dangereuse :
  de vol              certificat → CRL publiée  changer manuellement la
                      → refus immédiat par tous PSK sur TOUS les
                      les équipements           équipements

  Sécurité            Élevée -- cryptographie   Risquée en production --
                      asymétrique (RSA/ECDSA)   PSK \< 100 bits = choix
                      -- recommandé ANSSI       risqué selon l\'ANSSI

  Usage               Production et             Tests et diagnostics
                      environnements réels      uniquement
  -----------------------------------------------------------------------

+----------+-----------------------------------------------------------+
| **À      | En cas de VOL d\'ordinateur avec PKI : révoquer le        |
| R        | certificat → l\'attaquant ne peut plus s\'authentifier    |
| ETENIR** | même avec l\'ordinateur volé.                             |
|          |                                                           |
|          | En cas de VOL avec PSK : la PSK est sur la machine →      |
|          | l\'attaquant peut immédiatement établir un tunnel VPN     |
|          | valide.                                                   |
+----------+-----------------------------------------------------------+

**Objectif d\'une PKI / IGC**

+----------+-----------------------------------------------------------+
| **DÉFI   | Une PKI (Infrastructure à Clés Publiques) est un ensemble |
| NITION** | de mécanismes permettant de créer, gérer, distribuer,     |
|          | révoquer des certificats numériques.                      |
|          |                                                           |
|          | Elle lie de façon fiable une CLEF PUBLIQUE à l\'IDENTITÉ  |
|          | d\'un équipement ou d\'un utilisateur, grâce à la         |
|          | signature d\'une Autorité de Certification (AC).          |
|          |                                                           |
|          | Elle garantit l\'authenticité des correspondants dans     |
|          | tous les échanges sécurisés (VPN, HTTPS, authentification |
|          | admin\...).                                               |
+----------+-----------------------------------------------------------+

  -----------------------------------------------------------------------
  **⑩ FLASHCARDS -- QUESTIONS RAPIDES**

  -----------------------------------------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Délai notification CNIL    → 72 heures maximum (Art. 33 RGPD)
  après violation ?**             

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Que signifie SPOF ?**      → Single Point of Failure = point de
                                  défaillance unique → à éviter

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Règle 3-2-1 ?**            → 3 copies \| 2 supports différents \|
                                  1 hors site

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Différence réplication vs  → Réplication = disponibilité.
  sauvegarde ?**                  Sauvegarde = retour à un état antérieur
                                  sain

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Que fait \'sticky\' sur un → Mémorise automatiquement la 1ère
  port Cisco ?**                  adresse MAC connectée comme adresse
                                  autorisée

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Violation \'shutdown\' vs  → Shutdown : désactive le port \|
  \'restrict\' ?**                Restrict : bloque + alerte SNMP +
                                  compteur

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Stratégie TLS A vs B sur   → A (terminaison) : chiffré jusqu\'à
  HAProxy ?**                     HAProxy puis HTTP \| B (pass-through) :
                                  chiffré de bout en bout

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ ESP-SA1 sert à quoi côté   → Chiffrer les données ENVOYÉES par la
  mairie ?**                      mairie vers le site distant

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Pourquoi doubler les       → HAProxy seul = SPOF. En doublant : si
  HAProxy ?**                     l\'un tombe, l\'autre prend le relais
                                  (actif/passif)

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Pourquoi PKI \> PSK en     → Révocation rapide \| Ajout facile de
  production ?**                  nouveaux équipements \| Sécurité
                                  cryptographique supérieure

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Ryuk scanne quelles plages → 10.0.0.0/8 \| 172.16.0.0/16 →
  IP ?**                          172.31.0.0/16 \| 192.168.0.0/16

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Ryuk exfiltre-t-il des     → Non. Il chiffre uniquement
  données ?**                     (contrairement à d\'autres ransomwares)

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Phase 2 SANS : que NE      → Ne pas réinitialiser le poste
  faut-il PAS faire ?**           immédiatement → collecter d\'abord les
                                  IoC

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ MAC spoofing : pourquoi    → Les adresses MAC sont en clair sur le
  c\'est simple ?**               réseau → copiables + modifiables avec
                                  des outils gratuits

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ DPO : obligatoire pour qui → Tout organisme PUBLIC (mairies,
  ?**                             hôpitaux, administrations\...)

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ EBIOS RM : publiée par qui → L\'ANSSI (Agence Nationale de la
  ?**                             Sécurité des Systèmes d\'Information)

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ ANSSI R24 = ?**            → Ne PAS imposer d\'expiration sur les
                                  MDP des comptes NON sensibles

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ ANSSI R25 = ?**            → Imposer une expiration de 1 à 3 ans
                                  sur les MDP des comptes à PRIVILÈGES

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Qu\'est-ce qu\'un IoC ?**  → Indicator of Compromise : indice
                                  d\'infection (IP malveillante, hash de
                                  fichier, clé de registre\...)

  ------------------------------- ---------------------------------------

  ------------------------------- ---------------------------------------
  **❓ Lien inter-site unique →   → Déployer un lien internet indépendant
  solution ?**                    sur le site de secours + VPN IPSec de
                                  repli via internet

  ------------------------------- ---------------------------------------

  -----------------------------------------------------------------------
  **⑪ POINTS AUXQUELS ON NE PENSE PAS TOUJOURS**

  -----------------------------------------------------------------------

**En analyse de risques EBIOS**

-   Toujours argumenter la vraisemblance avec des faits/statistiques (ex
    : \'20% des ransomwares 2021 = Ryuk\')

-   Toujours développer les 3 axes D/I/C séparément, même si un seul est
    principalement impacté

-   Les mesures déjà en place RÉDUISENT la vraisemblance et/ou la
    gravité → les citer dans la réponse

-   Application Guard agit aussi sur la VRAISEMBLANCE (pas seulement la
    gravité) car automatique

**En sécurité réseau**

-   Pare-feu stateful : les règles de RETOUR sont IMPLICITES → ne pas
    les écrire dans la table de filtrage

-   La règle DENY ALL par défaut est IMPLICITE → ne pas l\'écrire non
    plus

-   VLAN par MAC = insuffisant TOUJOURS → proposer VLAN par port
    physique

-   Désactiver les ports inutilisés du commutateur → souvent oublié dans
    la réponse sur le port-security

-   write memory ou copy run start → TOUJOURS sauvegarder la
    configuration Cisco à la fin

**En réponse à incident**

-   Qualifier l\'alerte : est-ce un INCIDENT CONFIRMÉ ou un FAUX POSITIF
    ? → justifier avec les IoC

-   Identifier les AUTRES machines potentiellement impactées → scanner
    tout le SI avec les IoC

-   La notification CNIL a un délai de 72h → très souvent oublié dans
    les réponses

-   Éradication : penser aux TÂCHES PLANIFIÉES et CLÉS DE REGISTRE
    malveillantes (pas juste les fichiers !)

-   Retour à la normale : surveiller le poste après réintégration réseau

**En PCA / sauvegarde**

-   Réplication ≠ protection contre la corruption → il faut absolument
    les deux (réplication + sauvegarde avec historique)

-   Conserver PLUSIEURS sauvegardes complètes (pas juste la dernière) →
    pour revenir avant une compromission

-   Archivage annuel uniquement = INSUFFISANT → archivage mensuel
    recommandé

-   Les exercices de RESTAURATION sont obligatoires → vérifier que les
    sauvegardes sont réellement utilisables

-   Obligation légale : tester les PCA régulièrement, pas seulement les
    sauvegardes

**En VPN / PKI**

-   PSK déconseillée en production par l\'ANSSI → le dire explicitement
    dans la réponse

-   Les 2 clés ESP-SA1 et ESP-SA2 sont SYMÉTRIQUES mais DIFFÉRENTES et
    chacune est connue des 2 extrémités

-   En cas de vol d\'ordinateur avec PKI : RÉVOQUER le certificat
    immédiatement → blocage instantané

-   Pour les règles de filtrage VPN nomade : restreindre par UTILISATEUR
    et par DESTINATION précise

**En mots de passe AD**

-   PasswordLastSet ≠ LastLogonDate → bien choisir la propriété selon la
    question posée

-   \'Administrateurs de l\'entreprise\' ≠ \'Admins du domaine\' → deux
    groupes AD différents !

-   -Recursive dans Get-ADGroupMember → souvent oublié mais important
    pour les groupes imbriqués

**Définitions à maîtriser (souvent demandées implicitement)**

  -----------------------------------------------------------------------
  **Terme**          **Définition rapide**
  ------------------ ----------------------------------------------------
  SPOF               Single Point of Failure : composant dont la panne
                     entraîne l\'arrêt complet du service

  Hardening          Durcissement : réduction de la surface d\'attaque
                     d\'un système (désactivation de services, ports,
                     comptes inutiles)

  DMZ                Zone démilitarisée : réseau intermédiaire entre
                     internet et le réseau interne, pour les services
                     exposés

  Botnet             Réseau de machines zombies contrôlées par un
                     attaquant, utilisé pour des attaques DDoS

  C2 (Command &      Serveur utilisé par un attaquant pour piloter ses
  Control)           malwares à distance

  IoC                Indicator of Compromise : signe d\'infection (IP,
                     hash, domaine, clé de registre\...)

  Failover           Basculement automatique vers un système de secours
                     en cas de panne du système principal

  Round-Robin        Algorithme de répartition de charge : les requêtes
                     sont distribuées à chaque serveur à tour de rôle

  Scrubbing center   Centre de nettoyage du trafic anti-DDoS : filtre le
                     trafic malveillant avant qu\'il n\'atteigne la cible

  VRRP / Keepalived  Protocole de redondance d\'adresses IP pour la haute
                     disponibilité (ex : 2 HAProxy)

  MFA                Multi-Factor Authentication : authentification
                     nécessitant au moins 2 facteurs

  iSCSI              Protocole de stockage réseau (SAN) utilisant TCP/IP
                     pour accéder à des disques distants

  RAID 50            Combinaison RAID 5+0 : tolérance aux pannes +
                     performances accrues
  -----------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **★ CONSEIL FINAL POUR L\'EXAMEN ★**                                  |
|                                                                       |
| Toujours s\'appuyer sur les annexes et documents fournis dans le      |
| sujet : les réponses y sont souvent présentes ou suggérées.           |
|                                                                       |
| Structurer chaque réponse : définir → expliquer le principe →         |
| illustrer avec un exemple du contexte → conclure.                     |
|                                                                       |
| Pour les analyses de risque : toujours D/I/C + Gravité +              |
| Vraisemblance + argument chiffré.                                     |
+-----------------------------------------------------------------------+