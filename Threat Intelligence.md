[[BTL1]]

**SIGINT (Signal Intelligence)** Renseignement d'origine électromagnétique consiste à intercepter des signaux radios. Provient des systèmes de communications, des systèmes d'armes et des transmissions radar.
- **COMINT (Communication Intelligence)** -> Concerne les communications entre des personnes et des groupes de personnes (messages, et voix)
- **ELINT (Electronical Intelligence)** -> Le renseignement électronique est collecté à partir de systèmes qui ne sont pas utilisés directement pour les communications, tels que les communications de guidage pour les systèmes de missiles et les radars.
---
**OSINT (OpenSource Intelligence)** Les renseignements de source ouverte sont des informations recueillies auprès de sources publiques. Les types d'informations qui peuvent être collectées sont les dossiers de conduite, les numéros de téléphone, les adresses postales, les informations sur les messages sociaux et les réseaux sociaux, les adresses e-mail, les noms de domaine, etc. La quantité d'informations pouvant être utilisées pour détecter, suivre ou stopper les menaces est quasiment infinie.

---
**HUMINT (Human Intelligence)** Ces renseignements sont souvent recueillis par le biais de réunions en personne, de débriefings du personnel chargé d'obtenir des informations par le biais de l'observation, de la collecte de documents, etc. Ces informations peuvent être obtenues par le biais de l'espionnage ou de communications ouvertes entre diplomates, par exemple.

---
**GEOSIN (GeoSpatial Intelligence)** Renseignement qui rend ces modes d'engagement possibles en cas de catastrophes naturelles, en temps de guerre ou lors d'autres événements majeurs, tels que des troubles politiques. L'imagerie par satellite est très utilisée pour fournir au personnel du renseignement des cibles, des structures terrestres et, qu'elles soient artificielles ou naturelles, où se trouvent nos forces armées et leurs ennemis, afin de mieux coordonner les efforts d'attaque et de défense.

---
Catégories des acteurs malveillants : 

**Cybercriminels**
Ce groupe comprend les pirates informatiques et les pirates informatiques qui cherchent à gagner de l'argent grâce à des activités malveillantes et illégales, telles que les cyberattaques, les ransomwares et le phishing. Le niveau de compétence peut varier considérablement au sein de ce groupe. Par exemple, un hacker très expérimenté peut être considéré comme un acteur de cybercriminalité, mais vous pouvez également voir un « script kiddie » dans le même groupe, terme utilisé pour décrire une personne inexpérimentée qui dépend d'outils et de scripts prédéfinis et qui possède généralement un faible niveau de connaissances techniques.

**Etats-nations**
Il s'agit de pirates informatiques ou d'équipes de piratage qui travaillent pour les gouvernements du monde entier et qui disposent d'un très haut niveau de sophistication technique et de ressources, ce qui en fait des adversaires parmi les plus avancés du marché. Ils mènent généralement des cyberopérations secrètes prolongées, passant inaperçus pendant de longues périodes alors qu'ils atteignent silencieusement tous leurs objectifs sur le réseau cible. Les Etats-nations sont souvent appelés menaces persistantes avancées (APT).

**Hacktivistes**
Les individus ou les groupes classés dans cette catégorie sont généralement motivés par des raisons sociales ou politiques et utilisent les cyberattaques pour exprimer leurs points de vue et leurs convictions. Les hacktivistes mènent généralement des attaques par déni de service distribué (DDoS) qui mettent les systèmes hors ligne en surchargeant leurs ressources, provoquant ainsi leur blocage. Une autre attaque courante menée par les acteurs de ce groupe est la dégradation de sites Web, qui consiste à modifier le contenu de la page d'accueil d'un site Web pour afficher un message ou une image créé par l'attaque, généralement pour faire une déclaration liée à des opinions sociales ou politiques.

**Menace interne**
Les personnes classées dans ce groupe ont, intentionnellement ou non, abusé de leur pouvoir et de leur connaissance d'une organisation dans laquelle elles travaillent afin de divulguer des informations confidentielles. Les cas intentionnels peuvent inclure des employés mécontents qui se vengent de l'entreprise, et les cas non intentionnels peuvent inclure des employés qui envoient accidentellement des documents par e-mail à la mauvaise adresse e-mail ou qui sont victimes d'une attaque d'ingénierie sociale.

---
![[Pasted image 20250925154502.png]]

---

# Exemple d'IOCs

Vous trouverez ci-dessous une liste d'indicateurs typiques de compromis qui sont partagés publiquement et entre les organisations.

- **Adresses e-mail :** il s'agit de boîtes aux lettres qui agissent de manière malveillante, par exemple en envoyant des e-mails contenant des URL ou des pièces jointes malveillantes, ou en tentant d'influencer socialement les destinataires d'e-mails pour qu'ils prennent des mesures qu'ils n'auraient pas l'habitude de prendre, telles que la diffusion d'informations.
- **Adresses IP : ces adresses IP** ont agi de manière malveillante, par exemple en effectuant des analyses de ports ou de vulnérabilités non autorisées, en hébergeant du contenu ou des sites Web malveillants, ou ont été liées à une infrastructure d'acteurs malveillants telle que des serveurs de commande et de contrôle (C2). Des recherches WHOIS peuvent également être effectuées pour obtenir plus d'informations, telles que le propriétaire de l'adresse IP, son lieu de résidence géographique, le nom d'hôte et parfois ses coordonnées.
- **Noms de domaine/URL :** sites qui ont agi de manière malveillante, tels que l'hébergement de logiciels malveillants, de sites de phishing ou d'autres contenus malveillants.
- **Hachages de fichiers/noms de fichiers —** Nous pouvons facilement partager des informations sur les malwares ou d'autres fichiers malveillants, souvent en les désignant par leurs valeurs de hachage uniques (généralement MD5, sha256 ou sha1). Les équipes de sécurité peuvent les utiliser pour mettre sur liste noire les hachages de fichiers spécifiques afin qu'ils soient détectés et supprimés par des solutions de sécurité telles que la détection et la réponse des terminaux (EDR).
---
## **STIX :**

Structured Threat Information eXpression, ou STIX, a été développé par MITRE et le comité technique d'OASIS Cyber Threat Intelligence en tant que langage standardisé pour le partage d'informations sur les menaces. Pour certaines organisations et certains comités d'échange d'informations, c'est la norme et elle est largement utilisée. Bien que STIX soit conçu pour être utilisé conjointement avec TAXII, il peut être partagé sans celui-ci. STIX est conçu pour partager non seulement les ICO, mais également les menaces :

- Motivations
- Capacités
- Capacités
- Réponse

## **TAXI :**

Trusted Automated eXchange of Intelligence Information, ou TAXII, définit la manière dont les informations sur les cybermenaces peuvent être partagées à l'aide de services et d'échanges de messages. Conçue pour gérer les informations STIX, cette plateforme est exécutée sur un serveur et permet le partage d'informations entre des groupes spécifiques ou fournit un « flux de menaces » public auquel les individus peuvent s'inscrire et recevoir des informations.


Logiciel MISP
ISAC -> Intelligence Sharing and Correlation
**TIP :** Threat Intelligence Platform
Faire des rooms MISP sur tryhackme


**Traffic Light Protocol :**

|TLP label|Sharing boundary|Typical SOC L1 behaviour|
|---|---|---|
|**TLP: CLEAR**|No restriction|Post to the internal wiki or platform.|
|**TLP: GREEN**|Share with peer community but not publicly|Upload to MISP/Slack workspace restricted to partner SOCs.|
|**TLP: AMBER**|Organisation-wide, external sharing only with need-to-know clients|Keep within the company CTI platform; reference, do not copy, in tickets.|
|**TLP: RED**|Named recipients only|Store in an encrypted note; do not post to the ticketing system without clearance.|