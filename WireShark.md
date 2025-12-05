
## 🎯 TOP 10 FILTRES ESSENTIELS

### 1️⃣ FILTRER PAR IP

**Voir tout le trafic d'une IP spécifique**

```wireshark
ip.addr == 192.168.1.100
```

**Source ou destination séparément**

```wireshark
ip.src == 192.168.1.100
ip.dst == 192.168.1.100
```

**Exclure une IP**

```wireshark
!(ip.addr == 192.168.1.100)
```

---

### 2️⃣ FILTRER PAR PORT

**Trafic sur un port spécifique**

```wireshark
tcp.port == 80
udp.port == 53
```

**Source ou destination**

```wireshark
tcp.srcport == 443
tcp.dstport == 3389
```

**Ports multiples**

```wireshark
tcp.port == 80 || tcp.port == 443
tcp.port in {80 443 8080}
```

---

### 3️⃣ FILTRER PAR PROTOCOLE

**Protocoles courants**

```wireshark
http
https
dns
ftp
ssh
telnet
rdp
smb
icmp
arp
```

**Combiner protocole et IP**

```wireshark
http && ip.addr == 192.168.1.100
dns && ip.src == 10.0.0.1
```

---

### 4️⃣ DÉTECTER DES SCANS

**Scan SYN (port scan)**

```wireshark
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

**Nombreux SYN depuis une même source**

```wireshark
tcp.flags.syn == 1 && tcp.flags.ack == 0 && ip.src == 192.168.1.50
```

---

### 5️⃣ TRAFIC HTTP SUSPECT

**Requêtes HTTP GET**

```wireshark
http.request.method == "GET"
```

**Requêtes POST (souvent upload de données)**

```wireshark
http.request.method == "POST"
```

**URLs spécifiques**

```wireshark
http.request.uri contains "admin"
http.request.uri contains ".php"
http.host contains "malicious"
```

**Codes de réponse**

```wireshark
http.response.code == 200
http.response.code == 404
http.response.code >= 400
```

---

### 6️⃣ REQUÊTES DNS

**Toutes les requêtes DNS**

```wireshark
dns.qry.name
```

**Domaine spécifique**

```wireshark
dns.qry.name contains "google.com"
dns.qry.name == "malware.example.com"
```

---

### 7️⃣ TRAFIC FTP

**Connexions FTP**

```wireshark
ftp
```

**Commandes FTP (USER, PASS)**

```wireshark
ftp.request.command == "USER"
ftp.request.command == "PASS"
```

**Transferts de fichiers**

```wireshark
ftp-data
```

---

### 8️⃣ TRAFIC SMB (PARTAGES WINDOWS)

**Trafic SMB**

```wireshark
smb || smb2
```

**Accès aux partages**

```wireshark
smb2.cmd == 5
```

**Fichiers transférés**

```wireshark
smb2.filename
```

---

### 9️⃣ CONNEXIONS RDP

**Trafic RDP**

```wireshark
tcp.port == 3389
rdp
```

---

### 🔟 EXFILTRATION DE DONNÉES

**Gros paquets sortants (upload)**

```wireshark
ip.src == 192.168.1.100 && frame.len > 1000
```

**Trafic sortant massif**

```wireshark
tcp.dstport == 443 && frame.len > 1400
```

**Connexions vers des IPs externes**

```wireshark
!(ip.dst == 192.168.0.0/16) && !(ip.dst == 10.0.0.0/8)
```

---

```
Exemples combinés :

ip.addr == 192.168.1.100 && tcp.port == 80
http && (ip.src == 10.0.0.1 || ip.src == 10.0.0.2)
tcp.flags.syn == 1 && tcp.flags.ack == 0 && !icmp
```

---

### Combinaisons importantes

```wireshark
# Three-way handshake
tcp.flags.syn == 1 && tcp.flags.ack == 0  # SYN
tcp.flags.syn == 1 && tcp.flags.ack == 1  # SYN-ACK
tcp.flags.syn == 0 && tcp.flags.ack == 1  # ACK

# Scan SYN (port scan)
tcp.flags.syn == 1 && tcp.flags.ack == 0

# Connexion refusée
tcp.flags.reset == 1

# Fin de connexion
tcp.flags.fin == 1
```

---

## 🔍 FILTRES AVANCÉS POUR DÉTECTION

### Détection de brute force SSH

```wireshark
tcp.port == 22 && tcp.flags.syn == 1
```

### Détection de scan ARP (ARP poisoning)

```wireshark
arp.opcode == 2
arp.duplicate-address-detected
```

### ICMP (Ping, scan)

```wireshark
icmp
icmp.type == 8   # Echo request (ping)
icmp.type == 0   # Echo reply
```


---

## 📊 STATISTIQUES UTILES (Menu Statistics)

### Protocol Hierarchy

**Menu :** Statistics > Protocol Hierarchy

- Vue d'ensemble des protocoles utilisés
- Identifier les protocoles inhabituels

### Conversations

**Menu :** Statistics > Conversations

- Voir toutes les conversations IP
- Identifier les transferts massifs
- Détecter les connexions suspectes

### Endpoints

**Menu :** Statistics > Endpoints

- Liste de toutes les IPs actives
- Volume de trafic par IP
- Identifier les IPs les plus actives

### HTTP

**Menu :** Statistics > HTTP > Requests

- Liste de toutes les requêtes HTTP
- URLs visitées
- User-Agents utilisés

---

## 🎯 FONCTIONS UTILES

### Follow Stream (Suivre le flux)

**Clic droit > Follow > TCP/UDP/HTTP Stream**

- Voir toute la conversation
- Utile pour lire les échanges en clair (HTTP, FTP, Telnet)

### Export Objects (Extraire les fichiers)

**Menu :** File > Export Objects > HTTP/SMB/FTP

- Extraire les fichiers transférés
- Analyser les fichiers suspects

### Display Filters vs Capture Filters

**Display Filters** (après capture) :

```wireshark
ip.addr == 192.168.1.100
tcp.port == 80
http
```

**Capture Filters** (pendant capture, syntaxe BPF) :

```wireshark
host 192.168.1.100
port 80
tcp port 443
not port 22
```

---

## 🚨 SCÉNARIOS DE DÉTECTION

### 1. Brute Force Detection

```wireshark
# SSH Brute Force
tcp.port == 22 && tcp.flags.syn == 1

# RDP Brute Force
tcp.port == 3389 && tcp.flags.syn == 1

# Puis Statistics > Conversations pour voir le nombre de tentatives
```

### 2. Port Scan Detection

```wireshark
# Scan SYN
tcp.flags.syn == 1 && tcp.flags.ack == 0

# Puis regarde Statistics > Conversations
# Une IP qui contacte plein de ports = scan
```

### 3. Exfiltration Data

```wireshark
# Gros uploads
http.request.method == "POST" && http.content_length > 100000

# Trafic sortant massif
ip.src == 192.168.1.100 && frame.len > 1000

# Puis Statistics > Conversations pour voir les volumes
```

### 4. DNS Tunneling

```wireshark
# Requêtes DNS longues
dns && frame.len > 512

# Beaucoup de requêtes DNS vers un même domaine
dns.qry.name contains "suspecious.com"
```

### 5. Malware C2 Communication

```wireshark
# Connexions HTTPS régulières (beacon)
tcp.port == 443 && tcp.len > 0

# Vérifier la régularité dans Statistics > IO Graph
```

### 6. ARP Poisoning

```wireshark
arp.duplicate-address-detected
arp.opcode == 2

# Plusieurs réponses ARP pour la même IP
```

### 7. Man-in-the-Middle (MITM)

```wireshark
# Certificats SSL suspects
ssl.handshake.type == 11

# Redirections HTTP inhabituelles
http.response.code == 302
```

### 8. SMB Lateral Movement

```wireshark
# Accès aux partages admin
smb2 && ip.addr == 192.168.1.0/24

# Transferts de fichiers via SMB
smb2.filename contains ".exe"
```

---

## 📋 PROTOCOLES ET PORTS À CONNAÎTRE

### Ports TCP courants

```
20/21   - FTP (File Transfer)
22      - SSH
23      - Telnet
25      - SMTP (Email)
80      - HTTP
443     - HTTPS
445     - SMB (Windows shares)
3389    - RDP (Remote Desktop)
8080    - HTTP Proxy
```

### Ports UDP courants

```
53      - DNS
67/68   - DHCP
69      - TFTP
161/162 - SNMP
```

### Protocoles importants

```
ARP     - Address Resolution Protocol
ICMP    - Ping, traceroute
DNS     - Domain Name System
DHCP    - Dynamic Host Configuration
HTTP    - Web traffic
HTTPS   - Encrypted web (TLS/SSL)
FTP     - File Transfer Protocol
SMB     - Windows file sharing
RDP     - Remote Desktop Protocol
SSH     - Secure Shell
```

---

## 🎓 WORKFLOW D'ANALYSE

### Étape 1 : Vue d'ensemble

1. **Statistics > Protocol Hierarchy** → Quels protocoles ?
2. **Statistics > Conversations** → Qui parle à qui ?
3. **Statistics > Endpoints** → IPs actives et volumes

### Étape 2 : Identifier les anomalies

```wireshark
# Protocoles inhabituels
!(http || https || dns || icmp)

# Ports inhabituels
tcp.port > 1024 && tcp.port != 3389 && tcp.port != 8080
```

### Étape 3 : Focus sur le suspect

```wireshark
ip.addr == <IP_SUSPECTE>
# Puis Follow TCP Stream pour voir les échanges
```

---

## 🔐 DÉTECTION DE TECHNIQUES MITRE ATT&CK

### Reconnaissance (TA0043)

```wireshark
# Network scanning
tcp.flags.syn == 1 && tcp.flags.ack == 0

# Port scanning
tcp.flags.reset == 1

# ICMP scanning
icmp.type == 8
```

### Initial Access (TA0001)

```wireshark
# Brute force
tcp.port == 22 || tcp.port == 3389

# Phishing (fichiers suspects)
http.request.method == "POST"
smtp
```

### Lateral Movement (TA0008)

```wireshark
# RDP
tcp.port == 3389

# SMB
smb2 && tcp.port == 445

# PsExec
smb2.filename contains "psexe"
```

### Exfiltration (TA0010)

```wireshark
# Large uploads
http.request.method == "POST" && http.content_length > 1000000

# DNS tunneling
dns && frame.len > 512

# HTTPS exfiltration
tcp.port == 443 && frame.len > 1400
```

### Command & Control (TA0011)

```wireshark
# Beaconing (connexions régulières)
tcp.port == 443 || tcp.port == 80

# Analyse avec Statistics > IO Graph
```


---

## 🎯 LES 5 FILTRES ABSOLUMENT ESSENTIELS

1. **ip.addr == X** → Filtrer une IP
2. **tcp.port == X** → Filtrer un port
3. **tcp.flags.syn == 1 && tcp.flags.ack == 0** → Détecter un scan
4. **http.request.method == "POST"** → Upload de données
5. **dns.qry.name contains "X"** → Requêtes DNS
