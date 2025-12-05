# 🎯 TOP 10 REQUÊTES SPLUNK SIMPLES POUR BTL1

## 1️⃣ DÉTECTER DES ÉCHECS DE CONNEXION

**Scénario** : Trouver qui a échoué à se connecter plus de 5 fois

```splunk
index=windows EventCode=4625
| stats count by user, src_ip
| where count > 5
| sort -count
```

**Ce que ça détecte** : Tentatives de brute force **Niveau** : Basique - juste compter des échecs

---

## 2️⃣ TROUVER LES CONNEXIONS RÉUSSIES

**Scénario** : Voir qui s'est connecté avec succès

```splunk
index=windows EventCode=4624
| table _time, user, src_ip, ComputerName
```

**Ce que ça détecte** : Connexions réussies **Niveau** : Basique - affichage simple

---

## 3️⃣ DÉTECTER UN SCAN DE PORTS

**Scénario** : Qui essaie de se connecter à plein de ports différents ?

```splunk
index=firewall action=blocked
| stats dc(dest_port) as ports_tentés by src_ip
| where ports_tentés > 20
| sort -ports_tentés
```

**Ce que ça détecte** : Scan de ports (nmap) **Niveau** : Basique - compter des ports uniques

---

## 4️⃣ PROCESSUS POWERSHELL LANCÉS

**Scénario** : Voir tous les PowerShell qui ont été exécutés

```splunk
index=windows EventCode=4688 NewProcessName="*powershell.exe"
| table _time, User, ComputerName, CommandLine
```

**Ce que ça détecte** : Utilisation de PowerShell **Niveau** : Basique - simple filtrage

---

## 5️⃣ RECHERCHER UN UTILISATEUR SPÉCIFIQUE

**Scénario** : Voir toute l'activité d'un utilisateur

```splunk
index=windows user="john.doe"
| stats count by EventCode
| sort -count
```

**Ce que ça fait** : Liste toutes les actions d'un user **Niveau** : Basique - recherche par nom

---

## 6️⃣ COMPTES CRÉÉS

**Scénario** : Qui a créé de nouveaux comptes ?

```splunk
index=windows EventCode=4720
| table _time, user, NewAccountName, ComputerName
```

**Ce que ça détecte** : Création de comptes (persistence) **Niveau** : Basique - filtrage par Event ID

---

## 7️⃣ AJOUTS AU GROUPE ADMINISTRATEURS

**Scénario** : Qui a été ajouté aux admins ?

```splunk
index=windows EventCode=4732 TargetUserName="Administrators"
| table _time, SubjectUserName, MemberName, ComputerName
```

**Ce que ça détecte** : Élévation de privilèges **Niveau** : Basique - Event ID spécifique

---

## 8️⃣ CONNEXIONS RDP

**Scénario** : Qui se connecte en bureau à distance ?

```splunk
index=windows EventCode=4624 LogonType=10
| table _time, user, src_ip, ComputerName
```

**Ce que ça détecte** : Connexions RDP (mouvement latéral) **Niveau** : Basique - filtrer par LogonType

---

## 9️⃣ TÂCHES PLANIFIÉES CRÉÉES

**Scénario** : Nouvelles tâches planifiées créées

```splunk
index=windows EventCode=4698
| table _time, SubjectUserName, TaskName, ComputerName
```

**Ce que ça détecte** : Persistence via tâches planifiées **Niveau** : Basique - Event ID simple

---

## 🔟 TOP 10 DES UTILISATEURS ACTIFS

**Scénario** : Qui est le plus actif sur le réseau ?

```splunk
index=windows EventCode=4624
| top 10 user
```

**Ce que ça fait** : Classement des utilisateurs par activité **Niveau** : Basique - commande top simple

---

## 🎓 COMMENT UTILISER CES REQUÊTES À L'EXAMEN

### Les 3 commandes à maîtriser ABSOLUMENT :

1. **stats count by** → Compter des choses
2. **table** → Afficher des colonnes
3. **where** → Filtrer sur un nombre

### Autres commandes utiles :

**top/rare** - Les plus/moins fréquents

```splunk
| top 10 user
| rare dest_port
```

**dedup** - Supprimer les doublons

```splunk
| dedup user
```

**eval** - Créer un nouveau champ

```splunk
| eval is_suspicious=if(count>10, "YES", "NO")
```

**timechart** - Graphique temporel

```splunk
| timechart span=1h count by user
```

**search** - Filtrer dans le pipeline

```splunk
| search status=200
```

**head/tail** - Limiter les résultats

```splunk
| head 100
```

### Pattern de base à retenir :

```splunk
index=<index> EventCode=<code>
| stats count by champ1, champ2
| where count > seuil
| sort -count
```


---

## ⏰ FILTRES DE TEMPS (À CONNAÎTRE)

```splunk
earliest=-1h          # Dernière heure
earliest=-24h         # Dernières 24 heures
earliest=-7d          # 7 derniers jours
earliest=-1w          # Dernière semaine
earliest=-1mon        # Dernier mois
```

**Exemples concrets :**

```splunk
index=windows EventCode=4625 earliest=-1h
index=firewall earliest=-24h latest=-12h
```

---

## 🔍 WILDCARDS ET OPÉRATEURS

**Wildcards :**

```splunk
user="admin*"         # Commence par admin
user="*admin"         # Termine par admin
user="*admin*"        # Contient admin
```

**Opérateurs logiques :**

```splunk
user="admin" OR user="root"
user="admin" AND EventCode=4624
user="admin" NOT EventCode=4625
```

**Comparaisons (dans where) :**

```splunk
| where count > 10
| where count >= 5
| where count < 100
| where count != 0
```

---

## 📋 MÉMO EVENT IDS À CONNAÎTRE PAR CŒUR

### 🔐 Windows Security Log (EventCode)

**Authentification :**

- **4624** = Connexion réussie (logon success)
- **4625** = Échec de connexion (logon failure)
- **4634** = Déconnexion (logoff)
- **4647** = Déconnexion initiée par l'utilisateur
- **4648** = Connexion avec identifiants explicites (runas)
- **4672** = Privilèges spéciaux assignés à une connexion

**Gestion des comptes :**

- **4720** = Compte utilisateur créé
- **4722** = Compte utilisateur activé
- **4723** = Tentative de changement de mot de passe
- **4724** = Tentative de réinitialisation de mot de passe
- **4725** = Compte utilisateur désactivé
- **4726** = Compte utilisateur supprimé
- **4738** = Compte utilisateur modifié
- **4740** = Compte verrouillé (lockout)
- **4767** = Compte déverrouillé

**Gestion des groupes :**

- **4728** = Membre ajouté à un groupe de sécurité global
- **4732** = Membre ajouté à un groupe de sécurité local
- **4733** = Membre retiré d'un groupe de sécurité local
- **4756** = Membre ajouté à un groupe de sécurité universel
- **4735** = Groupe de sécurité local modifié

**Processus et objets :**

- **4688** = Nouveau processus créé
- **4689** = Processus terminé
- **4698** = Tâche planifiée créée
- **4699** = Tâche planifiée supprimée
- **4700** = Tâche planifiée activée
- **4701** = Tâche planifiée désactivée
- **4702** = Tâche planifiée mise à jour

**Accès réseau :**

- **5140** = Partage réseau accédé
- **5142** = Partage réseau créé
- **5143** = Partage réseau modifié
- **5144** = Partage réseau supprimé
- **5145** = Vérification d'accès à un objet partagé
- **5156** = Connexion réseau autorisée par le pare-feu

**Politique et système :**

- **4719** = Politique d'audit système modifiée
- **1102** = Journal d'audit effacé (LOG CLEARING - TRÈS SUSPECT!)
- **4616** = Heure système modifiée
- **4657** = Valeur de registre modifiée

---

### 🔍 Sysmon Event IDs

**Processus :**

- **1** = Création de processus (Process Create)
- **5** = Processus terminé (Process Terminated)
- **10** = Accès à un processus (ProcessAccess) - injection possible

**Réseau :**

- **3** = Connexion réseau (Network Connection)
- **22** = Requête DNS (DNSEvent)

**Fichiers :**

- **11** = Création de fichier (FileCreate)
- **23** = Suppression de fichier (FileDelete)
- **26** = Suppression de fichier (FileDeleteDetected)

**Registre :**

- **12** = Création/suppression de clé de registre (RegistryEvent)
- **13** = Modification de valeur de registre (RegistryEvent)
- **14** = Renommage de clé de registre (RegistryEvent)

**Image/DLL :**

- **6** = Driver chargé (Driver Loaded)
- **7** = Image/DLL chargée (Image Loaded)

**Avancé (Injection/Manipulation) :**

- **8** = CreateRemoteThread détecté (injection de code)
- **9** = RawAccessRead (accès direct au disque)
- **15** = FileCreateStreamHash (Alternate Data Streams)
- **17** = Pipe créé (PipeEvent)
- **18** = Pipe connecté (PipeEvent)
- **19** = WMI Event Filter activity
- **20** = WMI Event Consumer activity
- **21** = WMI Event Consumer-to-Filter binding

---

### 🪟 Windows System/Application Logs

**Services :**

- **7034** = Service crashed
- **7035** = Service envoyé un contrôle
- **7036** = Service entré dans un état (démarré/arrêté)
- **7040** = Paramètres de démarrage du service modifiés
- **7045** = Nouveau service installé dans le système

**Erreurs système :**

- **1000** = Application crashed
- **1001** = Application hang
- **6005** = Event Log service démarré (boot)
- **6006** = Event Log service arrêté (shutdown)
- **6009** = Version du système d'exploitation au démarrage

**Defender :**

- **1116** = Malware détecté
- **1117** = Action prise contre un malware
- **5001** = Protection temps réel désactivée
- **5010** = Analyse désactivée
- **5012** = Analyse modifiée

---

### 🔑 LogonType (Event 4624/4625)

- **2** = Interactive (clavier physique)
- **3** = Network (accès réseau/SMB)
- **4** = Batch (tâche planifiée)
- **5** = Service (service Windows)
- **7** = Unlock (déverrouillage session)
- **8** = NetworkCleartext (IIS, HTTP Basic Auth)
- **9** = NewCredentials (RunAs avec /netonly)
- **10** = RemoteInteractive (RDP/Terminal Services)
- **11** = CachedInteractive (identifiants en cache)

---

### 🎯 PRIORITÉS POUR BTL1

**Les 5 Event IDs ABSOLUMENT à connaître :**

1. **4624** - Connexion réussie
2. **4625** - Échec connexion
3. **4688** - Nouveau processus
4. **Sysmon 1** - Création processus
5. **Sysmon 3** - Connexion réseau

**Les LogonType critiques :**

- **10** = RDP (mouvement latéral)
- **3** = Réseau (partages, PsExec)

**Les Event IDs de persistence :**

- **4698** - Tâche planifiée
- **4720/4732** - Nouveau compte admin
- **7045** - Nouveau service

**Les Event IDs suspects :**

- **1102** - Log effacé = cover-up !
- **Sysmon 8** - Injection de code
- **4672** - Privilèges élevés
