# 🔵 CHEAT SHEET DEEPBLUECLI

**DeepBlueCLI** est un script PowerShell pour analyser les logs Windows et détecter :

- Activités suspectes
- Attaques connues
- Indicateurs de compromission (IOCs)
- Techniques MITRE ATT&CK

**Avantage** : Analyse rapide sans avoir besoin de Splunk ou d'un SIEM.

---

### Commande de base

```powershell
.\DeepBlue.ps1 <fichier.evtx>
```

### Exemples d'utilisation

```powershell
# Analyser le log Security
.\DeepBlue.ps1 C:\Windows\System32\winevt\Logs\Security.evtx

# Analyser le log System
.\DeepBlue.ps1 C:\Windows\System32\winevt\Logs\System.evtx

# Analyser Sysmon
.\DeepBlue.ps1 C:\Windows\System32\winevt\Logs\Microsoft-Windows-Sysmon%4Operational.evtx

# Analyser PowerShell logs
.\DeepBlue.ps1 C:\Windows\System32\winevt\Logs\Microsoft-Windows-PowerShell%4Operational.evtx

# Analyser Application logs
.\DeepBlue.ps1 C:\Windows\System32\winevt\Logs\Application.evtx
```

---

## 🎯 TOP 10 COMMANDES ESSENTIELLES

### 1️⃣ ANALYSER LE LOG SECURITY (AUTHENTIFICATION)

**Détecte** : Brute force, authentifications suspectes

```powershell
.\DeepBlue.ps1 C:\Windows\System32\winevt\Logs\Security.evtx
```

**Ce que ça trouve** :

- Échecs de connexion multiples (Event 4625)
- Connexions réussies suspectes (Event 4624)
- Utilisations de compte admin
- Modifications de comptes

---

### 2️⃣ ANALYSER SYSMON (PROCESSUS ET RÉSEAU)

**Détecte** : Malware, exécutions suspectes, connexions réseau

```powershell
.\DeepBlue.ps1 C:\Windows\System32\winevt\Logs\Microsoft-Windows-Sysmon%4Operational.evtx
```

**Ce que ça trouve** :

- Processus suspects (mimikatz, psexec, etc.)
- Connexions réseau suspectes
- Créations de fichiers malveillants
- Modifications de registre

---

### 3️⃣ ANALYSER POWERSHELL LOGS

**Détecte** : Scripts PowerShell malveillants, obfuscation

```powershell
.\DeepBlue.ps1 C:\Windows\System32\winevt\Logs\Microsoft-Windows-PowerShell%4Operational.evtx
```

**Ce que ça trouve** :

- Commandes encodées (base64)
- DownloadString, Invoke-Expression
- Scripts obfusqués
- Empire, Cobalt Strike, Metasploit

---

### 4️⃣ ANALYSER AVEC UN FICHIER EXPORTÉ

**Quand** : Tu as exporté un .evtx depuis un autre système

```powershell
.\DeepBlue.ps1 C:\Users\analyst\Desktop\exported-logs\Security.evtx
```

---

### 5️⃣ SORTIE EN FORMAT CSV (POUR REPORTING)

```powershark
.\DeepBlue.ps1 Security.evtx | Export-Csv -Path results.csv -NoTypeInformation
```

---

### 6️⃣ FILTRER LES RÉSULTATS PAR GRAVITÉ

**Dans PowerShell après l'exécution :**

```powershell
.\DeepBlue.ps1 Security.evtx | Where-Object {$_.Severity -eq "High"}
.\DeepBlue.ps1 Security.evtx | Where-Object {$_.Severity -eq "Critical"}
```

---

### 7️⃣ ANALYSER PLUSIEURS FICHIERS À LA FOIS

```powershell
# Tous les .evtx dans un dossier
Get-ChildItem C:\logs\*.evtx | ForEach-Object { .\DeepBlue.ps1 $_.FullName }
```

---

### 8️⃣ CHERCHER UN ÉVÉNEMENT SPÉCIFIQUE

```powershell
# Chercher "mimikatz" dans les résultats
.\DeepBlue.ps1 Security.evtx | Select-String "mimikatz"

# Chercher "password spray"
.\DeepBlue.ps1 Security.evtx | Select-String "password spray"
```

---

### 9️⃣ SAUVEGARDER LES RÉSULTATS

```powershell
.\DeepBlue.ps1 Security.evtx > analysis-results.txt
.\DeepBlue.ps1 Security.evtx | Out-File -FilePath report.txt
```

---

## 🚨 CE QUE DEEPBLUECLI DÉTECTE

### Authentification

✅ **Brute Force** (nombreux Event 4625) ✅ **Password Spray** (échecs multiples sur différents comptes) ✅ **Connexions suspectes** (horaires inhabituels, comptes admin)

### Exécution

✅ **PowerShell encodé** (base64, obfuscation) ✅ **Mimikatz** (credential dumping) ✅ **PSExec** (lateral movement) ✅ **WMI** (exécution à distance) ✅ **Service installation** (persistence)

### Persistence

✅ **Création de comptes** (Event 4720) ✅ **Ajout aux groupes admin** (Event 4732) ✅ **Tâches planifiées** (Event 4698) ✅ **Modifications de registre**

### Lateral Movement

✅ **Pass-the-Hash** ✅ **Connexions RDP suspectes** ✅ **Accès aux partages admin** (C$, ADMIN$)

### Command & Control

✅ **Connexions réseau suspectes** ✅ **Beaconing patterns** ✅ **DNS tunneling**

### Exfiltration

✅ **Transferts de fichiers massifs** ✅ **Accès aux données sensibles**

---

## 📊 COMPRENDRE LA SORTIE

### Format de sortie typique

```
Date    : 2024-01-15 14:32:10
Log     : Security
EventID : 4625
Message : Failed logon - Brute force attack detected
User    : administrator
Source  : 192.168.1.50
Count   : 47
Severity: High
```

### Niveaux de gravité

- **Critical** = Compromission confirmée ou très probable
- **High** = Activité très suspecte
- **Medium** = Activité inhabituelle à investiguer
- **Low** = Information, pas forcément malveillant

---

## 🔍 LOGS WINDOWS À ANALYSER

### Priorité 1 - CRITIQUE

```powershell
# Security (authentification, comptes, privilèges)
C:\Windows\System32\winevt\Logs\Security.evtx

# Sysmon (processus, réseau, fichiers)
C:\Windows\System32\winevt\Logs\Microsoft-Windows-Sysmon%4Operational.evtx

# PowerShell (scripts malveillants)
C:\Windows\System32\winevt\Logs\Microsoft-Windows-PowerShell%4Operational.evtx
```

### Priorité 2 - IMPORTANT

```powershell
# System (services, drivers, système)
C:\Windows\System32\winevt\Logs\System.evtx

# Application (crashes, erreurs)
C:\Windows\System32\winevt\Logs\Application.evtx

# Task Scheduler (persistence)
C:\Windows\System32\winevt\Logs\Microsoft-Windows-TaskScheduler%4Operational.evtx
```

### Priorité 3 - OPTIONNEL

```powershell
# Windows Defender
C:\Windows\System32\winevt\Logs\Microsoft-Windows-Windows Defender%4Operational.evtx

# Firewall
C:\Windows\System32\winevt\Logs\Microsoft-Windows-Windows Firewall With Advanced Security%4Firewall.evtx

# Terminal Services (RDP)
C:\Windows\System32\winevt\Logs\Microsoft-Windows-TerminalServices-LocalSessionManager%4Operational.evtx
```

---

## 🎯 SCÉNARIOS D'ANALYSE BTL1

### Scénario 1 : Suspicion de Brute Force

```powershell
# Analyser Security.evtx
.\DeepBlue.ps1 Security.evtx

# Chercher "brute force" ou "password spray"
.\DeepBlue.ps1 Security.evtx | Select-String "brute force"
```

**Indicateurs** :

- Event 4625 (échecs de connexion) en grand nombre
- Même source IP, différents comptes
- Courte période de temps

---

### Scénario 2 : Détection de Mimikatz

```powershell
# Analyser Security et Sysmon
.\DeepBlue.ps1 Security.evtx | Select-String "mimikatz"
.\DeepBlue.ps1 Sysmon.evtx | Select-String "mimikatz"
```

**Indicateurs** :

- Event 4673 (utilisation de privilèges sensibles)
- LSASS access
- Processus "mimikatz.exe" ou similaire

---

### Scénario 3 : PowerShell Malveillant

```powershell
# Analyser PowerShell logs
.\DeepBlue.ps1 PowerShell-Operational.evtx

# Chercher des commandes encodées
.\DeepBlue.ps1 PowerShell-Operational.evtx | Select-String "encoded"
```

**Indicateurs** :

- Base64 encoded commands
- DownloadString, Invoke-Expression
- Obfuscation (caractères aléatoires)

---

### Scénario 4 : Mouvement Latéral

```powershell
# Analyser Security pour PsExec/RDP
.\DeepBlue.ps1 Security.evtx | Select-String "psexec"
.\DeepBlue.ps1 Security.evtx | Select-String "lateral"
```

**Indicateurs** :

- Event 4624 LogonType 3 (Network)
- Event 4624 LogonType 10 (RDP)
- Event 5140 (partages réseau)

---

### Scénario 5 : Création de Compte Backdoor

```powershell
# Chercher création de comptes
.\DeepBlue.ps1 Security.evtx | Select-String "user created"
.\DeepBlue.ps1 Security.evtx | Select-String "added to"
```

**Indicateurs** :

- Event 4720 (compte créé)
- Event 4732 (ajouté au groupe Administrators)
- Horaire suspect (nuit, week-end)

---

### Scénario 6 : Persistence via Services

```powershell
# Analyser System logs
.\DeepBlue.ps1 System.evtx | Select-String "service"
```

**Indicateurs** :

- Event 7045 (nouveau service installé)
- Nom de service suspect
- Chemin d'exécution inhabituel (temp, appdata)

---

### Scénario 7 : Effacement de Logs (Anti-Forensics)

```powershell
.\DeepBlue.ps1 Security.evtx | Select-String "log clear"
.\DeepBlue.ps1 System.evtx | Select-String "1102"
```

**Indicateurs** :

- Event 1102 (log effacé)
- Event 104 (log effacé)
- Très suspect = cover-up !

---

## 🛠️ COMBINAISONS AVEC POWERSHELL

### Filtrer par date

```powershell
.\DeepBlue.ps1 Security.evtx | Where-Object {$_.Date -gt "2024-01-15"}
```

### Compter les événements par type

```powershell
.\DeepBlue.ps1 Security.evtx | Group-Object EventID | Sort-Object Count -Descending
```

### Exporter en HTML

```powershell
.\DeepBlue.ps1 Security.evtx | ConvertTo-Html | Out-File report.html
```

### Top 10 des événements

```powershell
.\DeepBlue.ps1 Security.evtx | Select-Object -First 10
```

### Chercher par utilisateur

```powershell
.\DeepBlue.ps1 Security.evtx | Where-Object {$_.User -like "*admin*"}
```

---

## 🚩 INDICATEURS DE COMPROMISSION (IOCs)

### Processus suspects détectés par DeepBlueCLI

```
mimikatz.exe          - Credential dumping
psexec.exe            - Lateral movement
powershell.exe -enc   - Encoded commands
wmic.exe              - WMI execution
reg.exe               - Registry modification
net.exe               - Network commands
whoami.exe            - Reconnaissance
ipconfig.exe          - Reconnaissance
netstat.exe           - Reconnaissance
tasklist.exe          - Reconnaissance
```

### Commandes PowerShell suspectes

```
DownloadString        - Téléchargement de malware
Invoke-Expression     - Exécution de code
Invoke-Mimikatz       - Credential dumping
Invoke-WebRequest     - Téléchargement
New-Object Net.WebClient - Téléchargement
-EncodedCommand       - Obfuscation
-WindowStyle Hidden   - Exécution cachée
Bypass -ExecutionPolicy - Contournement de sécurité
```

### Chemins suspects

```
C:\Windows\Temp\
C:\Users\Public\
%APPDATA%\
%TEMP%\
C:\ProgramData\
```

---

## 📋 WORKFLOW D'ANALYSE COMPLÈTE

### Étape 1 : Analyse initiale

```powershell
# Commencer par Security (authentification)
.\DeepBlue.ps1 Security.evtx > security-analysis.txt

# Puis Sysmon (processus et réseau)
.\DeepBlue.ps1 Sysmon.evtx > sysmon-analysis.txt

# Ensuite PowerShell (scripts)
.\DeepBlue.ps1 PowerShell-Operational.evtx > powershell-analysis.txt
```

### Étape 2 : Identifier les alertes critiques

```powershell
# Filtrer par gravité
Get-Content security-analysis.txt | Select-String "Critical"
Get-Content security-analysis.txt | Select-String "High"
```

### Étape 3 : Chercher des IOCs connus

```powershell
# Mimikatz
Get-Content *.txt | Select-String "mimikatz"

# PsExec
Get-Content *.txt | Select-String "psexec"

# Encoded commands
Get-Content *.txt | Select-String "encoded"
```

---

## 💡 ASTUCES PRATIQUES BTL1

### 1. Toujours commencer par Security.evtx

C'est le log le plus important pour détecter les compromissions.

### 2. Chercher les mots-clés

```powershell
"mimikatz", "psexec", "encoded", "brute force", "password spray"
```

### 3. Vérifier les Event IDs suspects

```
Event 4625 (échecs connexion) > 10 = Brute Force
Event 4720 + 4732 = Nouveau compte admin = Backdoor
Event 4688 avec PowerShell = Exécution suspecte
Event 1102 = Log effacé = Cover-up
```

### 4. Utiliser Sysmon pour les détails

Sysmon donne beaucoup plus de détails (command line, hashes, connexions réseau).

### 5. Chercher les horaires suspects

Activité la nuit ou le week-end = suspect.

### 6. Suivre les connexions réseau (Sysmon Event 3)

Connexions vers des IPs externes = possible C2.

### 7. Vérifier les modifications de registre (Sysmon Event 13)

Persistence via Run keys.

---

## 🔐 TECHNIQUES MITRE ATT&CK DÉTECTÉES

### Initial Access (TA0001)

- Brute Force (T1110)
- Valid Accounts (T1078)

### Execution (TA0002)

- PowerShell (T1059.001)
- Windows Command Shell (T1059.003)
- WMI (T1047)

### Persistence (TA0003)

- Create Account (T1136)
- Scheduled Task (T1053)
- Registry Run Keys (T1547.001)
- New Service (T1543.003)

### Privilege Escalation (TA0004)

- Valid Accounts (T1078)
- Access Token Manipulation (T1134)

### Credential Access (TA0006)

- OS Credential Dumping (T1003) - Mimikatz
- Brute Force (T1110)

### Lateral Movement (TA0008)

- Remote Services RDP (T1021.001)
- Remote Services SMB (T1021.002)
- PsExec (T1569.002)

### Defense Evasion (TA0005)

- Obfuscated Files/Information (T1027)
- Indicator Removal - Clear Logs (T1070.001)

---

## 🎯 LES 5 COMMANDES ABSOLUMENT ESSENTIELLES

1. **.\DeepBlue.ps1 Security.evtx** → Analyser l'authentification
2. **.\DeepBlue.ps1 Sysmon.evtx** → Analyser les processus
3. **.\DeepBlue.ps1 PowerShell.evtx** → Détecter scripts malveillants
4. **| Select-String "mimikatz"** → Chercher des IOCs
5. **| Where-Object {$_.Severity -eq "High"}** → Filtrer par gravité

