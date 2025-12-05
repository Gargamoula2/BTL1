
## 📖 QU'EST-CE QU'AUTOPSY ?

**Autopsy** est un outil d'analyse forensique open-source pour :

- Analyser des disques durs, images disque, fichiers
- Récupérer des fichiers supprimés
- Analyser des timelines
- Chercher des IOCs (Indicators of Compromise)
- Examiner les artefacts Windows (registry, logs, browser history)

**Format supporté** : Images disque (.E01, .dd, .raw, .vmdk, etc.)

---

### Créer un nouveau cas

1. **File > New Case**
2. Nom du cas : `Investigation-2024`
3. Base Directory : Où sauvegarder
4. Case Number : Optionnel
5. Examiner : Ton nom

### Ajouter une source de données

1. **Add Data Source**
2. Choisir le type :
    - **Disk Image or VM File** (.E01, .dd, .raw)
    - **Local Disk**
    - **Logical Files** (dossiers/fichiers individuels)
3. Sélectionner le fichier
4. Configurer les modules (laisser par défaut pour commencer)
5. **Next** puis attendre l'indexation

---

## 🎯 INTERFACE AUTOPSY - LES 5 ZONES

```
┌─────────────────────────────────────────────────┐
│  1. TREE VIEWER (gauche)                        │
│  Navigation dans la structure de données         │
├─────────────────────────────────────────────────┤
│  2. RESULT VIEWER (centre-haut)                 │
│  Liste des fichiers/résultats                    │
├─────────────────────────────────────────────────┤
│  3. CONTENT VIEWER (centre-bas)                 │
│  Contenu du fichier sélectionné                  │
├─────────────────────────────────────────────────┤
│  4. STATUS BAR (bas)                            │
│  Progression, messages                           │
├─────────────────────────────────────────────────┤
│  5. KEYWORD SEARCH (haut à droite)              │
│  Recherche de mots-clés                          │
└─────────────────────────────────────────────────┘
```

---

## 🔎 TOP 10 ANALYSES ESSENTIELLES

### 1️⃣ RÉCUPÉRER DES FICHIERS SUPPRIMÉS

**Emplacement** : Data Sources > File Views > **Deleted Files**

**Étapes** :

1. Tree Viewer (gauche) > **Deleted Files**
2. Parcourir les fichiers supprimés
3. Clic droit > **Extract File(s)** pour récupérer

**Utile pour** :

- Fichiers supprimés par un attaquant
- Documents effacés
- Outils malveillants supprimés

---

### 2️⃣ ANALYSER LA TIMELINE

**Emplacement** : Tools > **Timeline**

**Étapes** :

1. Menu **Tools > Timeline**
2. Choisir les types d'événements (File Activity, Web Activity, etc.)
3. Analyser la chronologie

**Filtres utiles** :

- Par date/heure
- Par type d'activité
- Par fichier

**Utile pour** :

- Reconstituer les événements
- Trouver quand l'attaque a eu lieu
- Corréler les activités

---

### 3️⃣ RECHERCHE PAR MOTS-CLÉS

**Emplacement** : Tools > **Keyword Search**

**Étapes** :

1. **Tools > Keyword Search** (ou Ctrl+F)
2. Créer une liste de mots-clés
3. Lancer la recherche

**Mots-clés suspects** :

```
password
mimikatz
psexec
admin
backdoor
malware
confidential
secret
exploit
payload
```

**Options de recherche** :

- Exact Match
- Substring Match
- Regular Expression

---

### 4️⃣ ANALYSER L'HISTORIQUE WEB

**Emplacement** : Data Sources > **Web History**

**Ce qu'on trouve** :

- Sites visités
- Téléchargements
- Cookies
- Cache
- Bookmarks

**Navigateurs supportés** :

- Chrome
- Firefox
- Edge
- Internet Explorer
- Safari

**Utile pour** :

- Sites malveillants visités
- Téléchargements de malware
- Phishing

---

### 5️⃣ EXAMINER LES FICHIERS RÉCENTS

**Emplacement** : Data Sources > Views > File Types > **Recent Documents**

**ou** Data Sources > **Recent Activity**

**Ce qu'on trouve** :

- Fichiers ouverts récemment
- Documents modifiés
- Applications lancées

**Utile pour** :

- Voir ce que l'utilisateur a fait
- Identifier les fichiers suspects consultés

---

### 6️⃣ ANALYSER LES EMAILS

**Emplacement** : Data Sources > Views > File Types > **E-Mail Messages**

**ou** Data Sources > **Communications**

**Formats supportés** :

- PST (Outlook)
- MBOX
- EML

**Utile pour** :

- Emails de phishing
- Exfiltration de données
- Communications malveillantes

---

### 7️⃣ TROUVER DES EXÉCUTABLES SUSPECTS

**Emplacement** : Data Sources > Views > File Types > **Executables**

**Filtres utiles** :

```
Extension: .exe, .dll, .scr, .bat, .ps1
Emplacement: Temp, Downloads, AppData
Nom: random strings (ex: asdkfj.exe)
```

**Vérifier** :

- Nom suspect
- Emplacement inhabituel (C:\Temp, C:\Users\Public)
- Date de création récente
- Hash (avec VirusTotal)

---

### 8️⃣ EXAMINER LE REGISTRE WINDOWS

**Emplacement** : Data Sources > **OS Accounts** ou **Registry**

**Clés importantes** :

```
Run Keys (persistence)
USB History
Installed Programs
User Accounts
Network Shares
Recent Files
```

**Utile pour** :

- Détection de persistence
- Comptes créés
- Programmes installés

---

### 9️⃣ ANALYSER LES HASH DE FICHIERS

**Emplacement** : Data Sources > Views > File Types > **By Hash Value**

**Étapes** :

1. Tools > **Hash Database**
2. Importer des hash connus (malware, NSRL)
3. Comparer avec les fichiers

**Hash Sets utiles** :

- Known Bad (malware)
- Known Good (NSRL - fichiers Windows légitimes)

**Utile pour** :

- Identifier des malwares connus
- Exclure les fichiers système légitimes

---

### 🔟 EXTRAIRE DES ARTEFACTS WINDOWS

**Emplacement** : Data Sources > **Operating System Information**

**Artefacts** :

- **Prefetch** (programmes exécutés)
- **LNK Files** (raccourcis, fichiers récents)
- **Jump Lists** (fichiers récents par application)
- **SRUM** (System Resource Usage Monitor)
- **Event Logs** (.evtx)
- **ShellBags** (dossiers ouverts)
- **UserAssist** (programmes lancés)

---

## 🗂️ NAVIGATION DANS L'ARBORESCENCE

### Tree Viewer - Sections principales

**Data Sources**

```
├── [Image Name]
│   ├── File Views
│   │   ├── File Types (par extension)
│   │   ├── Deleted Files
│   │   ├── File Size
│   │   └── Extension Mismatch
│   ├── Results
│   │   ├── Extracted Content
│   │   ├── Keyword Hits
│   │   ├── Hashset Hits
│   │   └── Interesting Items
│   ├── Operating System Information
│   │   ├── Program Execution
│   │   ├── Installed Programs
│   │   └── User Accounts
│   ├── Web History
│   ├── Recent Activity
│   └── Tags
```

---

## 🔍 MODULES D'INGEST (ANALYSE AUTOMATIQUE)

### Modules importants à activer

**Recent Activity** ✅

- Analyse l'activité récente de l'utilisateur

**Hash Lookup** ✅

- Compare les hash avec des bases connues

**Extension Mismatch Detector** ✅

- Détecte les fichiers avec extensions modifiées (ex: malware.txt qui est vraiment un .exe)

**Embedded File Extractor** ✅

- Extrait les fichiers dans les archives, documents

**Email Parser** ✅

- Parse les emails

**Keyword Search** ✅

- Recherche automatique de mots-clés

**Interesting Files Identifier** ✅

- Identifie automatiquement les fichiers suspects

**PhotoRec Carver** (optionnel)

- Récupération de fichiers supprimés (lent)

---

## 🎯 WORKFLOWS D'INVESTIGATION

### Workflow 1 : Investigation de Malware

**Étape 1 : Chercher les exécutables**

```
File Views > File Types > Executables
Trier par : Date Created (récent)
```

**Étape 2 : Filtrer les emplacements suspects**

```
Chercher dans :
- C:\Users\[user]\Downloads
- C:\Users\[user]\AppData\Local\Temp
- C:\Windows\Temp
- C:\Users\Public
```

**Étape 3 : Vérifier les hash**

```
Clic droit > Search for files with the same MD5 hash
Copier le hash > Vérifier sur VirusTotal
```

**Étape 4 : Examiner la timeline**

```
Tools > Timeline
Filtrer par la date de création du malware
Voir quels autres fichiers ont été créés/modifiés
```

**Étape 5 : Chercher la persistence**

```
Operating System Information > Program Execution
Examiner les Run Keys dans le registre
```

---

### Workflow 2 : Investigation de Compromission de Compte

**Étape 1 : Examiner les comptes**

```
Operating System Information > OS Accounts
Chercher les comptes créés récemment
```

**Étape 2 : Analyser les connexions**

```
Recent Activity > Recent Documents
Web History
```

**Étape 3 : Chercher des outils d'attaque**

```
Keyword Search : "mimikatz", "password", "dump"
```

**Étape 4 : Timeline des événements**

```
Tools > Timeline
Filtrer par le compte suspect
```

---

### Workflow 3 : Investigation d'Exfiltration

**Étape 1 : Analyser les emails**

```
Communications > E-Mail Messages
Chercher les pièces jointes
Filtrer par taille (gros fichiers)
```

**Étape 2 : Historique web**

```
Web History > Web Downloads
Chercher les uploads (sites de partage)
```

**Étape 3 : Fichiers récents**

```
Recent Activity > Recent Documents
Voir quels documents ont été accédés
```

**Étape 4 : USB/Périphériques**

```
Operating System Information > USB Devices
Voir si des périphériques ont été connectés
```

---

### Workflow 4 : Investigation de Phishing

**Étape 1 : Analyser les emails**

```
Communications > E-Mail Messages
Chercher : "urgent", "password", "verify", "account"
```

**Étape 2 : Pièces jointes suspectes**

```
Regarder les .zip, .exe, .scr, .js dans les emails
```

**Étape 3 : Liens cliqués**

```
Web History
Voir si l'utilisateur a visité des sites suspects
```

**Étape 4 : Téléchargements**

```
Web History > Web Downloads
Voir ce qui a été téléchargé après l'email
```

---

## 🔎 RECHERCHES AVANCÉES

### Recherche par attributs

```
Clic droit dans Result Viewer > Add a filter
Filtrer par :
- Extension
- Size
- Modified Date
- Path
- Hash
```

### Recherche de fichiers cachés

```
File Views > File Types > By Extension
Chercher : ADS (Alternate Data Streams)
```


---

## 🚩 ARTEFACTS WINDOWS IMPORTANTS

### Prefetch (C:\Windows\Prefetch)

**Ce que ça contient** :

- Programmes exécutés
- Nombre d'exécutions
- Dernière exécution

**Emplacement Autopsy** :

```
Operating System Information > Program Execution > Prefetch
```

### LNK Files (Raccourcis)

**Ce que ça contient** :

- Fichiers récemment ouverts
- Chemins complets
- Timestamps

**Emplacement Autopsy** :

```
Operating System Information > Recent Documents > Link Files
```

### Registry Run Keys

**Ce que ça contient** :

- Programmes lancés au démarrage (persistence)

**Clés importantes** :

```
HKCU\Software\Microsoft\Windows\CurrentVersion\Run
HKLM\Software\Microsoft\Windows\CurrentVersion\Run
```

### Jump Lists

**Ce que ça contient** :

- Fichiers récents par application
- Destinations fréquentes

**Emplacement** :

```
C:\Users\[user]\AppData\Roaming\Microsoft\Windows\Recent\AutomaticDestinations
```

### Event Logs

**Ce que ça contient** :

- Security events (connexions, échecs)
- System events (services, crashes)
- Application events

**Emplacement Autopsy** :

```
Operating System Information > Installed Programs
ou extraire manuellement depuis Windows\System32\winevt\Logs
```

### Browser History

**Ce que ça contient** :

- URLs visitées
- Téléchargements
- Cookies
- Cache

**Emplacement Autopsy** :

```
Web History > [Browser Name]
```

### USB History

**Ce que ça contient** :

- Périphériques USB connectés
- Dates de connexion
- Lettres de lecteur

**Emplacement Autopsy** :

```
Operating System Information > USB Device Attached
```

### SRUM (System Resource Usage Monitor)

**Ce que ça contient** :

- Utilisation réseau par application
- Consommation de ressources

**Emplacement** :

```
C:\Windows\System32\sru\SRUDB.dat
```

---

## 🔐 RECHERCHE D'IOCs

### Noms de fichiers suspects

```
mimikatz
psexec
procdump
lazagne
nc.exe (netcat)
pwdump
fgdump
gsecdump
wce.exe
```

### Extensions suspectes

```
.ps1 (PowerShell)
.vbs (VBScript)
.bat (Batch)
.scr (Screensaver - souvent malware)
.hta (HTML Application)
.jar (Java)
```

### Chemins suspects

```
C:\Windows\Temp
C:\Users\[user]\AppData\Local\Temp
C:\Users\Public
C:\ProgramData
C:\$Recycle.Bin
```

### Registry Run Keys (Persistence)

```
HKCU\Software\Microsoft\Windows\CurrentVersion\Run
HKLM\Software\Microsoft\Windows\CurrentVersion\Run
HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce
```

---

## 📋 CHECKLIST D'INVESTIGATION

### Phase 1 : Reconnaissance

- [ ] Ajouter la source de données
- [ ] Attendre la fin de l'indexation
- [ ] Vérifier les modules d'ingest activés

### Phase 2 : Identification

- [ ] Timeline : Trouver la fenêtre de compromission
- [ ] Deleted Files : Récupérer les fichiers supprimés
- [ ] Keyword Search : Chercher des IOCs
- [ ] Interesting Items : Vérifier les alertes auto

### Phase 3 : Analyse

- [ ] Executables : Examiner les .exe suspects
- [ ] Web History : Sites visités
- [ ] Email : Phishing ou exfiltration
- [ ] Registry : Persistence
- [ ] Recent Activity : Activités de l'utilisateur

### Phase 4 : Documentation

- [ ] Tagger les fichiers importants
- [ ] Extraire les preuves
- [ ] Créer une timeline des événements
- [ ] Générer un rapport

---

## 🎯 LES 5 ACTIONS ABSOLUMENT ESSENTIELLES

1. **Timeline** → Reconstituer la chronologie
2. **Deleted Files** → Récupérer les fichiers supprimés
3. **Keyword Search** → Chercher "mimikatz", "password", etc.
4. **Web History** → Sites visités, téléchargements
5. **Executables** → Fichiers .exe suspects

**Maîtrise ces 5 et t'es prêt pour Autopsy au BTL1 ! 🔍**

---

## 📚 RESSOURCES SUPPLÉMENTAIRES

**Site officiel** : https://www.autopsy.com/ **Documentation** : https://sleuthkit.org/autopsy/docs/ **Tutoriels** : https://www.autopsy.com/support/training/

---

## 🎓 TIPS POUR L'EXAMEN BTL1

### 1. Commence toujours par la Timeline

Ça te donne une vue d'ensemble de ce qui s'est passé.

### 2. Cherche les fichiers supprimés en premier

Les attaquants suppriment souvent leurs outils.

### 3. Les noms de fichiers random = suspect

Ex: `asdkjfh.exe`, `temp123.bat`

### 4. Vérifie les emplacements Temp

`C:\Windows\Temp` et `%TEMP%` sont des caches d'attaquants.

### 5. Extension Mismatch = alerte rouge

Un `.txt` qui est vraiment un `.exe` = déguisement.

### 6. Les hash sont tes amis

Compare toujours avec VirusTotal ou des bases de hash.

### 7. Registry Run Keys = persistence

C'est LA première chose à vérifier pour la persistence.

### 8. Tag tout ce qui est important

Tu devras extraire les preuves et faire un rapport.

### 9. Les timestamps mentent pas

Utilise la timeline pour corréler les événements.

### 10. Export tes trouvailles

À la fin, extrais les fichiers suspects et génère un rapport.