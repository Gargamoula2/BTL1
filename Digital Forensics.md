[[BTL1]]

1. **Identification** — La première étape consiste à identifier les sources potentielles de preuves ou d'informations pertinentes (dispositifs), ainsi que les principaux dépositaires et l'emplacement des données.
2. **Préservation** — Processus de conservation des informations pertinentes stockées électroniquement (ESI). Cela se fait en protégeant la scène du crime ou de l'incident, en capturant des images visuelles de la scène et en documentant toutes les informations pertinentes concernant les preuves et la manière dont elles ont été obtenues.
3. **Collecte** — Collecte d'informations numériques pouvant être pertinentes pour l'enquête. La collecte peut comprendre le retrait du ou des dispositifs électroniques de la scène du crime ou de l'incident, puis l'imagerie, la copie ou l'impression de leur contenu.
4. **Analyse** — Recherche systématique approfondie des preuves relatives à l'incident faisant l'objet de l'enquête. Les résultats de l'examen sont des objets de données trouvés dans les informations collectées. Ces sorties peuvent inclure des fichiers générés par le système et par l'utilisateur. L'analyse vise à tirer des conclusions sur la base des preuves trouvées.
5. **Rapports** — Les rapports sont basés sur des techniques et des méthodes éprouvées et d'autres légistes compétents devraient être en mesure de reproduire les mêmes résultats.

**Kroll Artifact Parser and Extractor – KAPE** est utilisé pour l’acquisition rapide de preuves numériques et de fichiers pouvant intéresser un examinateur forensic.  
L’opérateur peut définir les informations qu’il souhaite collecter en utilisant des modules, et KAPE se mettra au travail, récupérant les informations importantes en quelques minutes, alors qu’une copie forensic complète pourrait prendre des heures.

**Forensic Tool Kit Imager – FTK Imager** est un outil gratuit qui permet de prendre des images bit à bit de disques durs, de monter des images disque en mode lecture seule (bloqueur logiciel d’écriture) et offre des fonctionnalités d’analyse pour examiner les images disque.

**Browser History Capturer – BHC** est un outil gratuit qui permet à l’opérateur de collecter les fichiers principaux des navigateurs web courants, qui peuvent être examinés manuellement ou importés dans Browser History Viewer pour analyser l’historique web.

**Browser History Viewer – BHV** est un outil gratuit qui permet à l’opérateur de capturer certains fichiers principaux du navigateur (il est préférable d’utiliser **BHC** pour collecter les fichiers à analyser) et fournit ensuite des fonctionnalités d’analyse, permettant d’examiner l’historique web sur le long terme, les images mises en cache et les pages web.

/etc/passwd -> Contient des informations sur les utilisateurs de la machine
/etc/shadow -> Contient les mots de passe chiffrés pour tous les comptes de la machine 

Files system :
- **FAT16** :
	- La table d'allocation de fichiers est la méthode qui consiste à utiliser une table pour marquer la position des fichiers. FAT16 est le système de fichiers d'origine utilisé sous DOS et Windows 3. x. À l'origine, il a été conçu uniquement pour être utilisé sur des partitions relativement petites. En cas de problème et que la table d'allocation de fichiers est perdue ou endommagée, les données du disque dur ne peuvent pas être utilisées car le système d'exploitation ne parvient pas à localiser les fichiers.
- **FAT32**
	- **FAT32** est une version révisée de **FAT16** qui peut être utilisée pour créer des partitions beaucoup plus volumineuses. Elle prend en charge nativement les noms de fichiers longs. Elle a été introduite avec Win98. La partie 32 de son nom vient du fait que FAT32 utilise 32 bits de données pour identifier les clusters de données sur le périphérique de stockage. Les avantages importants de l'utilisation de _FAT32_ aujourd'hui sont les suivants :
		- Il est compatible avec une grande variété d'appareils : smartphones, tablettes, ordinateurs, appareils photo numériques, consoles de jeu, caméras de surveillance, etc.
		- Il est également compatible avec presque tous les systèmes d'exploitation lancés depuis 1995. **FAT32 fonctionne avec Windows 95 OSR2, Windows 98, XP, Vista, Windows 7, 8 et 10. MacOS et** le supportent Linux également.
		
	**D'autre part, l'utilisation de FAT32 présente de sérieux inconvénients :**
	- FAT32 ne peut fonctionner qu'avec des fichiers d'une taille inférieure à 4 Go.
	- FAT32 ne fonctionne qu'avec des partitions d'une capacité maximale de 8 To.
	- Si vous possédez un lecteur formaté en FAT32, vous ne bénéficiez d'aucune protection des données en cas de coupure de courant.
	- Le système de fichiers FAT32 n'inclut aucune fonctionnalité de compression de fichiers intégrée.
	- FAT32 n'a pas été conçu pour être sécurisé et n'inclut aucune fonctionnalité de cryptage intégrée.

- **NTFS:**
	- **NTFS** (**NT File System**) est un système de fichiers de journalisation propriétaire développé par Microsoft. À partir de **Windows NT 3.1**, il s'agit du système de fichiers par défaut de la famille Windows NT.

	- NTFS comporte plusieurs améliorations techniques par rapport aux deux systèmes de fichiers qu'il a remplacés, à savoir la table d'allocation de fichiers (FAT) et le système de fichiers à hautes performances (HPFS), telles qu'une meilleure prise en charge des métadonnées et des structures de données avancées pour améliorer les performances, la fiabilité et l'utilisation de l'espace disque. Les extensions supplémentaires incluent un système de sécurité plus élaboré basé sur des listes de contrôle d'accès (ACL) et la journalisation du système de fichiers.

	- Le NTFS est également pris en charge dans d'autres systèmes d'exploitation de bureau et de serveur. Linux et BSD disposent d'un pilote NTFS gratuit et open source, appelé NTFS-3G, doté à la fois de fonctionnalités de lecture et d'écriture. macOS est doté d'un support en lecture seule pour NTFS, mais en raison de l'instabilité du support d'écriture pour NTFS, l'écriture de fichiers est désactivée par défaut.

- **EXT3/ EXT4:**
- **Linux Architecture**
	Avant d'examiner EXT3 et EXT4, nous allons rapidement aborder l'architecture des systèmes de Linux fichiers. Ces systèmes de fichiers sont divisés en trois parties :
	- **Espace utilisateur :** les applications se trouvent dans l'espace utilisateur, qui envoie les appels système à l'interface d'appel système. Un appel système n'est rien d'autre qu'une demande envoyée au noyau du système d'exploitation pour un service.
	- **Espace noyau —** Le noyau est le cœur du système d'exploitation qui répond aux appels système depuis l'espace utilisateur en fournissant les ressources demandées, en gérant les périphériques d'E/S (entrée/sortie), les dispositifs de mémoire, la gestion des fichiers, etc.
	- **Espace disque :** le pilote de périphérique situé dans l'espace du noyau envoie la demande d'E/S au disque dur du système qui contient des données de fichiers critiques.

- **Troisième système de fichiers étendu (Ext3)**
	Le troisième système de fichiers étendu (Ext3) est un système de fichiers journalisé couramment utilisé par le noyau. Linux Il s'agit du **système de fichiers par défaut de nombreuses Linux distributions populaires**. Les modifications apportées au journal, qui est un journal circulaire présent dans le système de fichiers, sont surveillées par ext3, appelé journalisation. La journalisation du système de fichiers est une fonctionnalité supplémentaire d'ext3, qui n'était pas disponible dans ext2. Dans un système de fichiers non journalisé, la restauration des données et la détection des erreurs prenaient plus de temps, car nous devions peut-être parcourir toute la structure de données du répertoire. Mais, dans un système de fichiers journalisé, nous avons un journal qui assure le suivi des modifications que nous apportons au système de fichiers. Ainsi, pour détecter les erreurs ou récupérer des données, après un crash, il suffit de lire le journal au lieu de traiter l'ensemble de la structure des données.

- **Quatrième système de fichiers étendu (Ext4)**
	La version stable d'ext4 a été introduite en 2008 par Linux . La taille de volume maximale des données prises en charge par ext4 est de 1 exbioctet et la taille du fichier peut atteindre 16 tebioctets. La longueur maximale du nom de fichier est de 56 octets. La fragmentation en termes de blocs physiques dans lesquels les données sont stockées est remplacée par des étendues. Cette modification, qui n'était pas disponible dans ext2 et ext3, a amélioré les performances du système de fichiers. L'étendue est une zone de stockage de données qui réduit la fragmentation et la dispersion des fichiers. 


**Ordre de volatilité :**
- **Registres et cache**
	Le contenu du cache et des registres du processeur est extrêmement volatil car il change constamment. Un enquêteur doit récupérer les données du cache et s'enregistrer immédiatement avant que ces preuves ne soient perdues.

- **Mémoire**
	Les informations situées sur la mémoire vive (RAM) peuvent être perdues en cas de pic de tension ou si le système est déconnecté de l'alimentation. Il s'agit d'un type de mémoire rapide et temporaire dans lequel les programmes, les applications et les données sont stockés. Cela peut inclure des données très utiles sur les processus en cours d'exécution, les connexions réseau et bien plus encore.

- **Disque (HDD et SSD)**
	Comme nous l'avons expliqué dans les leçons de base relatives aux disques durs (HDD) et aux disques SSD (Solid State Disk), nous savons qu'une fois que les données ont été écrasées, il est impossible de les récupérer et que les SSD présentent le risque supplémentaire que Garbage Collection ou TRIM suppriment des fichiers qui pourraient être utilisés comme preuves. Si le système est hors ligne, l'espace disque ne peut pas être remplacé et le disque n'est plus considéré comme volatil.

- **Enregistrement et surveillance à distance des données**
	Le risque de modification des données d'enregistrement et de surveillance à distance est bien supérieur à celui des données stockées sur un disque dur, mais les informations ne sont pas aussi vitales. Ainsi, même si la volatilité des données est plus élevée ici, nous voulons tout de même d'abord les données du disque dur.

- **Configuration physique, topologie du réseau, supports d'archivage**
	Nous avons ici des éléments qui ne sont pas très vitaux en termes de données ou qui ne sont pas du tout volatils. La configuration physique et la topologie du réseau sont des informations qui peuvent aider à une enquête, mais elles n'auront probablement pas d'impact majeur. Enfin, les données archivées se trouvent généralement sur un périphérique physique distinct, tel qu'une clé USB ou un disque dur externe.

Il est impératif que les analystes Forensic tiennent compte de la volatilité lorsqu'ils entament le processus de collecte de preuves. Des méthodes doivent être utilisées pour garantir que les preuves volatiles sont collectées et transférées sur un support non volatil, tel qu'un disque dur externe, le plus rapidement possible.

**Vérifier quand un fichier a été consulté ou modifié sur Linux :**
"stats FICHIER" ou "ls -lisap FICHIER"
**Récupérer les métadonnées d'un fichier sur Linux :**
exiftool FICHIER
**Récupérer des fichiers supprimés :**
Paramétrer le fichier de conf pour dire ce qu'on cherche (sur linux) : /etc/scalpel/scalpel.conf
Ensuite il faut décommenter la ligne qui nous intéresse dans ce fichier de conf
Lancer avec : `scalpel -o <OUTPUT> <FICHIER>`
OUTPUT : Endroit où on veut que le résultat arrive
FICHIER : Fichier de type "image" du disque dur, en gros le fichier qui contient les infos du disque dur qu'on veut scrap

Créer un fichier de swap sous Linux :
**`sudo fallocate -l taille du fichier /swapfile`**
Vérifier la quantité d'espace d'échange disponible sur le système :
`free -h`
`swapon -show` peut ensuite être utilisée pour identifier si l'espace de swap est un fichier ou une partition.

Recuperer le hash :
`get-filehash** FICHIER -alorithme SHA256`
`sha256sum FICHIER`
`echo -n TEXT | SHA256`

A write blocker is a device that prevents writing to a hard drive, but allows someone to read from it.

---

✅ **FTK Imager** s’utilise pour **créer une image forensique complète et préservée d’un disque ou support** avant toute analyse.  
✅ **KAPE** s’utilise pour **collecter et analyser rapidement les artefacts clés d’un système Windows** lors d’une réponse à incident ou d’un triage.
# FTK Imager

***Ce que peut faire FTK Imager :***
- **Videz la RAM** et stockez-la dans un fichier `**.mem**`, afin que nous puissions l'exporter vers d'autres outils, par exemple à des fins Volatility d'analyse.
- **Prendre des images de disque** qui peuvent être analysées à l'aide d'outils tels que Autopsy
- **Exportez des fichiers** directement à partir d'images de disque.
- **Générez des hachages MD5 et SHA1 pour les fichiers** de preuves.
- **Fournissez une vue en lecture seule** du contenu d'une image disque, exactement comme l'utilisateur l'aurait vue.
- **Et bien plus encore !**
- 
FTK Imager est un outil extrêmement puissant qui est utilisé dans le cadre d'enquêtes réelles par les enquêteurs et les équipes de sécurité. Passons rapidement en revue certaines des fonctionnalités :


**Dump de mémoire**
  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/ba9219ef95d2f4558f265739e660ea05bffef5c5684b88bd82f5cbaf8b1be70b41567e3aa695dbbf2964e3dd7e50.png)

La première chose que l'on peut faire est de prendre une copie instantanée de la RAM du système. Pour ce faire, nous allons dans **Fichier > Capturer la mémoire**.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/8d7d686cd8b967effdca6b989bc75a029820918c2a0846a3ac2777bdd3332ccd26443e3cab36c3ddf77cb7ec3c06.png)

Nous sommes ensuite invités à saisir l'emplacement dans lequel le fichier doit être enregistré. Nous avons donc créé un nouveau répertoire sur notre bureau nommé « Memory Dump ». En bas de la page, vous pouvez créer un fichier AD1, le type de fichier de signature de The Forensic Toolkit (TFK), un autre outil développé par AccessData. Nous laisserons ces deux options décochées et cliquerons sur « Capturer la mémoire ». FTK Imager va maintenant se mettre au travail en vidant tout ce qui se trouve dans la RAM et en le stockant dans un fichier .mem.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/4f6d3ad23b7fb17ba2a9024f5b0d4a57ecc3b27a1e69ca48710a182ff07be2b34d2657c7d9943f8aa2a159c6475f.png)

Une fois l'opération terminée, nous aurons désormais un fichier mémoire du systeme. Nous pouvons utiliser des outils tels que Volatility pour analyser le dump mémoire.

**Imagerie du disque dur**

Dans le monde réel, un disque dur prélevé sur une scène de crime sera connecté à un poste de travail auquel un disque dur propre sera connecté. Un bloqueur d'écriture sera utilisé entre le poste de travail et le disque dur suspect, afin d'empêcher le poste de travail de modifier accidentellement quoi que ce soit sur le disque dur, ce qui pourrait entraîner le rejet de preuves pour falsification. L'analyste judiciaire commencera ensuite à copier bit par bit le disque dur du suspect sur le disque vierge. Cela peut prendre beaucoup de temps, car il s'agit d'une copie exacte de chaque donnée, de sorte que rien n'est oublié.

Nous pouvons créer un fichier image système (`**.img**`) à l'aide FTK Imager duquel nous pouvons ensuite l'analyser pour rechercher des preuves numériques. Pour cet exemple, nous allons prendre une image disque d'une clé USB de 15 Go que nous avons. À des fins de démonstration, nous avons placé des fichiers aléatoires sur la clé USB.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/c92d5a33b41fda82f289c708b25bd3ff1b03b2a6b52eaea552f27252db646971f0933d57da6d5126fa27948d4822.png)

Dans FTK Imager ce document, nous voulons cliquer sur **Fichier**, puis aller sur **Créer une image de disque**.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/47c9705eeca789fd2b6c268703bb95e7e43745f7a93d27eb4278c1a4a2aa7e37e3ae2eef9226605d1544a77d02b3.png)

Ensuite FTK Imager , nous demanderons quelle sera la source des preuves. Lorsque nous prenons une copie des données d'une clé USB, nous devons sélectionner **Physical Drive**.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/572a30babec765d460b7dd138e95b72901f8bda320e0de5dc212f6559b9388a03de83b67232948b05cb19ab6f4c3.png)

Comme nous avons sélectionné Physical Drive, nous FTK Imager allons maintenant nous demander de sélectionner les lecteurs actuellement connectés au système exécutant l'outil. Dans la liste déroulante, vous pouvez voir le SSD de 500 Go et le port USB de 15 Go. Nous devons sélectionner la clé USB.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/96c5e38e23f3b15a261583cfc57f4492919b4dd30f36ae29dc1c8da46c77e90d7d204d55527c79f05e1e5924d13b.png)

On peut ensuite preciser le type d'image que l'on veut. En l'occurence, le logiciel "EnCase" prefere les images de type E01

![[Pasted image 20251011162150.png]]

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/246e744f8978aec3599633e0902d2d1c894dd41664bf28802a81831c99c61433fe887e9234a74eb98c2acc1075ed.png)

Nous devons maintenant attribuer une destination de sortie et le nom de fichier que nous voulons attribuer à notre image disque lors de l'exportation FTK Imager . Nous voulons que le fichier `.img` soit nommé USBImage.img et qu'il soit placé sur notre bureau. Nous voulons également définir la taille du fragment d'image à 0 Mo, ce qui signifie que l'image du disque ne sera pas divisée en segments plus petits, car nous voulons tout cela dans un seul fichier.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/b1e40b19556f4892ed6177a89edd9d34dde2208d588d62332ed08ad737bbf188ead04d9bd264517ff841ff73a2c6.png)

  
Après avoir cliqué sur Terminer, nous FTK Imager allons commencer à copier chaque bit de données de la clé USB sur notre disque dur.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/189cdd1fc9c18df3dff82c4aad9b17b12ff733996c62fbfbe90f1b6a43be3cf58b4d41e813b86225fc6d11e69563.png)

Pour cet exemple, cela se fait rapidement, car l'espace total de la clé USB est de 15 Go. Il s'agit également d'une toute nouvelle clé USB, ce qui signifie qu'aucune donnée existante n'a été supprimée mais n'a pas encore été remplacée (souvenez-vous de notre leçon de base sur le disque dur, où nous avons mentionné que les données supprimées se trouvent toujours sur le disque !). Si vous preniez la copie d'un disque dur de 1 To utilisé depuis un an, cela va prendre beaucoup de temps. Une fois la copie FTK Imager terminée, la fenêtre ci-dessous apparaît, comparant les hachages des fichiers pour s'assurer que la copie est saine du point de vue médico-légal.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/3d46610b89ec6c16c7f4b7ae6113b564078b953c9057c00a9524d69ddcf4d59522c71c9e0400981372ee906878b8.png)

Alors, comment cela fonctionne-t-il dans le monde réel ? Les diagrammes ci-dessous montrent comment un analyste judiciaire ou un agent des forces de l'ordre prélèverait une copie médico-légale d'un disque dur faisant l'objet d'une enquête. Le premier schéma montre comment un disque dur est copié pour créer un fichier .img qui reste sur la station de travail Forensic.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/480069c446c6a61534ab695e7fb30fbeace2ff37f1302f2941fb17e61064e68c90100644b60b10bb9921dcd10a9a.png)

Le deuxième schéma ci-dessous montre comment l'imageur FTK peut être utilisé pour écrire le contenu du disque dur étudié sur un disque dur vierge.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/fd0d1284bdb6975c94fbd676b13602ae0b8f5d7c32190e9da9d8cc7b2770b7ce898c7ac45af0149bc26c71e430a7.png)

Vous voulez vous entraîner avec FTK Imager  ? Vous pouvez essayer de créer une image d'une ancienne clé USB ou, lorsque vous sélectionnez le type de source de preuve, vous pouvez copier des dossiers à l'aide de l'option « Contenu d'un dossier ».

---
# KAPE

En consultant le dossier KAPE, vous trouverez deux fichiers exécutables, kape.exe et gkape.exe. Nous allons utiliser gkape.exe, qui est la version graphique de cet outil. Exécutons-le. Nous pouvons diviser l'interface en trois sections :

- **En haut à gauche —** Les cibles nous permettent de choisir exactement les informations que nous voulons récupérer du système cible, afin de pouvoir les obtenir le plus rapidement possible. Cela peut aller de la mémoire système aux données du navigateur Web.
- **En haut à droite :** les modules fournissent des fonctionnalités supplémentaires et permettent d'effectuer des opérations avec les données récupérées, telles que l'analyse des informations collectées à partir du système cible. Elles s'appuient sur les options Target et nous permettent d'affiner les informations que nous voulons collecter.
- **En bas :** la section Ligne de commande génère la requête qui est transmise KAPE pour exécution.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/8c3e09e8343034128158ebed1654453d17c06e49232cd7d98423acd6e5332fd9e2972bbd45b06ecc051b96c181e6.png)

En cliquant sur "Use Target Options" On peut ensuite préciser la source, donc dans quel répertoire on veut récupérer les infos (Ici on veut récupérer des infos dans tout le disque C), target destination c'est le dossier dans lequel ira tout ce que le logiciel a trouve 

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/becab6a7e2586f4d056ec4a5027ea0341d2c99bd84d27ae9affb201287835584703e75e94a3f519c6a636a37fc4d.png)

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/6df632c3be344227ebc38a11f14baea985d52bf8859dae448e388cb7e2fcc9b5e4c1ea291973e3c735426266df53.png)

Ensuite, nous pouvons sélectionner nos cibles. Pour le premier exemple, collectons des informations à partir des navigateurs Web les plus populaires : Chrome, Edge et Firefox. Nous pouvons faire défiler la zone Cibles vers le bas et les trouver.  Ou utiliser la barre de recherche (En général il faut cliquer dans la zone pour la faire apparaitre)
![[Pasted image 20251011164145.png]]

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/86fd20b0d23a3dce3f3740db925b46db879000e3e155198bf010166e2f791f873c58af3a3065856c0f800e79b90b.png)

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/853dee97f608ff6fd08c5ef69c95cb9a55b0f3b5df521b088e2190f4479347b0d57076e01c6af9be4610704c7442.png)

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/e152803c6ea10414967d0428713ab6dd7508dbe354b283a92f57f87f4fe3c9a6a1f2a6c915223b31a2d36ead21ca.png)

Une fois que nous avons sélectionné toutes nos cibles, nous pouvons cliquer sur le bouton Exécuter en bas à droite pour commencer KAPE .

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/ee74ebd5dc5ca5e5de11798fd64681e89ebff663892d77caaf994818fab10c5b1bbf694bb21112a146175f90ee8b.png)

KAPE va ouvrir un terminal et commencer à récupérer les copies des fichiers que nous avons demandés.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/7a4128714ec8bfe04c12aaab9fbc8be34c5f94c353514cb2626cbf7c0e67e85d9e3df9fc4e930b25700e30eccf7f.gif)

Voyons ce que KAPE a trouvé en accédant au répertoire que nous avons défini comme destination cible plus tôt. Nous pouvons voir qu'il existe un certain nombre de journaux qui nous indiquent exactement ce qui s'est passé lors de l'acquisition. Nous avons également un dossier nommé « C » d'après le lecteur C de notre système hôte.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/7cbce1a9606ed0dfd1064e9043c31cbf45b6ab00db65b3608041f9361a02fb764b0bd82ca51142d9ef20bc510258.png)

Nous pouvons voir que KAPE a trouvé des fichiers intéressants concernant l'activité menée à l'aide du navigateur Firefox sur ce système, y compris les cookies (qui peuvent nous indiquer les sites visités par l'utilisateur) et l'historique des formulaires qui peut inclure des informations personnelles telles que les adresses, les noms, la date de naissance, etc.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/e65860cf1997552f9ef6def5015e8808e7aa49dc5fa3b28e59b59308ab8e1f8ec08c6d532fae2f35234b73aa5f64.png)

Dans la capture d'écran ci-dessous, nous pouvons voir que KAPE a également récupéré des informations très utiles concernant Google Chrome.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/ba971f8b0c24834667dbeebef6a028b99c11f75f63cd418d1353bd0e1e1e5dc1e7a790639062701eba014ad81b10.png)

Enfin, nous avons certains fichiers provenant d'Internet Explorer/Edge tels que des caches Web.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/f984921f4546fedebab2395b78cdecdd80954bb7a563130f5a3061c30d22517db512ed960d9a2923f350f9f085ec.png)

**KAPE** peut être utilisé pour récupérer rapidement des tonnes d'informations, telles que les journaux d'événements Windows, les journaux antivirus, les métadonnées du système de fichiers, les fichiers journaux, les fichiers supprimés, les e-mails et bien plus encore

==**Préférer gKAPE qui est la version graphique de KAPE**==

---

Récupérer le PID d'un process sur windows : `Get-Process | findstr -I calc`
"calc" étant le process que l'on recherche, calculatrice en l'occurrence

Créer un memory dump du process : `.\procdump.exe -ma PID`

Mettre le PID récupéré par Get-Process

Les fichiers LNK se trouvent à l'adresse suivante : **`C:\Users \ $USER$ \ AppData \ Roaming \ Microsoft \ Windows \ Recent`**

Pour afficher ces fichiers dans un format lisible par l'homme, nous pouvons utiliser **`Windows File Analyzer`**

Les fichiers Prefetch peuvent nous fournir des informations extrêmement utiles sur les programmes, notamment le nom de l'application, le chemin d'accès au fichier exécutable, la date de la dernière exécution du programme et la date de création/installation du programme.

**`Les fichiers Prefetch se trouvent à l'adresse suivante : C:\Windows\Prefetch`**

.\PECmd.exe -f FILE.pf                 (NE PAS OUBLIER LE .\)

FILE étant le fichier qu'on veut analyser et qui a été récupéré dans la liste des fichiers Preftech

En haut de la sortie, nous pouvons voir combien de fois ce fichier a été exécuté, l'heure de création, l'heure de modification et la date du dernier accès. Nous avons également l'heure de la dernière exécution et d'autres fois où cette application a été exécutée. Toutes les autres lignes de cette sortie sont des fichiers liés à l'application, indiquant leurs chemins de fichiers complets.

Les fichiers de la liste de raccourcis se trouvent à l'adresse suivante : 
`C:\Users \ % USERNAME% \ AppData \ Roaming \ Microsoft \ Windows \ Recent \ AutomaticDestinations   
`C:\Users \ %USERNAME% \` `AppData \ Roaming \ Microsoft \ Windows \ Recent \ CustomDestinations`

Ces fichiers contiennent des informations sur les applications qui sont épinglées à la barre des tâches, telles que le chemin du fichier, les horodatages et les identificateurs d'applications (AppID).

Pour analyser ces fichiers, nous pouvons utiliser des outils tels que JumpList Explorer



`.\PECmd.exe -d "C:\Users\BTLOTest\Desktop\Windows Investigation One\Prefetch" -k plaguerat.ps1`

-d Pour préciser que c'est pas un fichier précis qu'il va analyser mais un dossier repli de fichier en .pf
-k Pour mettre en surbrillance rouge toutes les chaines de caractères qui contiennent le texte en question

Chercher les lignes rouges qui contiennent "plaguerat.ps1" et remonter pour voir quel fichier a lance le processus 
En remontant la liste on va trouver dans le paragraphe concerne : "Executable name: WINLOGON.EXE"
C'est donc le logiciel WINLOGON.EXE qui a lance le script plaguerat.ps1

**Tous les fichiers téléchargés dans BHV sont préfixés par « file :///»**

---

Exemple d'analyse sur windows :

**Question 1 - Quels navigateurs Web ont été utilisés par l'employé, classés par ordre alphabétique ? (Utilisez des noms de navigateur simplifiés)**

Tout d'abord, nous allons ouvrir Browser History Viewer (BHV) dans le dossier Windows Investigation Two sur le bureau. Une fois qu'il est chargé, nous allons accéder à Fichier > Historique des chargements.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/5a24e8413213154e2d55474455cdaee04eaa18dc1ffbb2bb37eed78f22740c986503faabaeba2196adcd8aef1f86.PNG)

Lorsque nous sommes invités à charger la capture de l'historique, nous cliquons sur le bouton «... » et nous trouvons le dossier Capture.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/30b4e9a667391b8e7214aa0a8ba7ac4b47d0ed05fb7848b9cbb5c19d2dfec75d46b38b4095eb05ff77bcc36c3bd5.PNG)

Une fois que le BHV aura importé les données, nous pourrons commencer à répondre aux questions !

Sur le premier écran, nous pouvons voir que la colonne à l'extrême droite s'intitule « Navigateur Web (profil) ». Cela nous permet d'identifier les navigateurs Web utilisés sur le système. Il suffit de parcourir la liste et de prendre note des noms des navigateurs. Il est très important de noter qu'il existe 4 pages, qui peuvent être consultées à l'aide des flèches sur le côté gauche de BHV. Comme la question demande des noms simplifiés, au lieu de « Edge Legacy », nous saisirons « Edge ». Il nous est également demandé de les fournir par ordre alphabétique. Nous allons donc nous assurer de les saisir correctement.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/32310ba5b570b3e527c09b89991bd4656e6530b926f48efb35fd052deb079c212dc25ed72e3e8a5763b2b423ad06.PNG)

---

**Question 2 - L'entreprise a adopté une politique interdisant aux employés de consulter les réseaux sociaux sur les appareils de l'entreprise. Quels sites l'employé a-t-il visités, classés par ordre alphabétique ?**

Pour répondre à cette question, nous devons nous concentrer sur la colonne « URL », où nous pouvons voir exactement quelles ressources Web ont été visitées par l'utilisateur. Il s'agit de les parcourir tous pour identifier les noms des sites Web de médias sociaux.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/d1232cea6f1bb786622e46f29a0152fedf2a8c176c9cc185436ad2a54be3a920904bc64cf51f97c8ae59a8ae4b92.PNG)

Si vous ne savez pas si une plateforme est considérée comme un réseau social ou non, une recherche rapide sur Google peut vous aider à comprendre. À titre d'exemple :

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/1aa5fe99295a8878f2deca07b964ccf6db7a40c4301404bdf052628ef60cca62433d965f2d62b506c162d3c2a8be.PNG)

Pour vous aider à répondre à cette question, il existe 5 sites que nous considérons comme des réseaux sociaux. Assurez-vous de les classer par ordre alphabétique ! Nous acceptons plusieurs variantes pour cette réponse.

---

**Question 3 - En regardant les images mises en cache le 19/06/2020 à 12:12:10 (UTC) avec le nom de fichier « everything-in-one-place-scenario-base [1] .png », quel est l'objet du troisième e-mail ?**

Pour cette question, une date nous est fournie afin de nous aider à identifier le dossier qui nous intéresse. Nous avons deux méthodes pour trouver cette date, qui est enregistrée dans la colonne « Dernière récupération » de l'onglet Images mises en cache de BHV.

- Option 1 : Cliquez sur l'en-tête de Last Fetched pour modifier les résultats afin qu'ils s'affichent par ordre croissant ou décroissant dans le temps. Si les horodatages sont en ordre, il nous sera plus facile de trouver l'horodatage correct.
- Option 2 - Utilisez la section « Filtrer par date » dans le panneau de droite. Pour ce laboratoire, tous les résultats concernent le même jour, mais dans un scénario réel, il est fort probable qu'il s'agisse de jours ou de semaines de données. Cette fonctionnalité serait donc utile pour examiner facilement des jours d'activité spécifiques.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/9e13c17213d4b1643f104849d4b84914cd35ceda3e8c9c8dde0a6cd39d12100cbe9f301fa2d873361951e1b523df.PNG)

À l'aide de la colonne Last Fetched, nous trouvons le bon moment et le bon fichier (en fonction de la colonne Nom de fichier).

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/d5b1693f47819cb23ccff09c4511acb74479295bc3efb4e2a9cc1276806201db6c95bbac9406e73b55c6d82110a5.PNG)

En regardant le panneau inférieur de BHV, si nous sélectionnons un fichier dans le tableau, l'image associée sera mise en évidence. Nous pouvons double-cliquer sur l'image pour l'afficher en taille réelle dans une nouvelle fenêtre. Ici, nous pouvons obtenir la réponse à cette question.

---

**Question 4 - Quelle est l'URL complète du clip vidéo que l'employé écoute sur Youtube ?**

Pour cette question, nous allons retourner à l'onglet Historique du site Web en haut à gauche. Au lieu de parcourir toutes les URL pour trouver celles de YouTube, nous pouvons utiliser le champ de recherche « Filtrer par mot clé » en haut à droite. Si nous saisissons YouTube, nous ne verrons que les URL ou les titres qui incluent la chaîne « youtube ».

Après avoir cherché cela, nous pouvons rapidement trouver la réponse à la question.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/d2b7999aa32870c459bb33f7c234151530801315bd8f5f1e5acb0965795b70a10d9c6fb64cbe83bf0c06b40d0ea3.PNG)

---

**Question 5 - Quel est le nom du fichier malveillant téléchargé par l'employé ?**

Pour aborder cette question, nous avons trois méthodes principales :

- Option 1 : passez en revue manuellement toutes les URL jusqu'à ce que des URL se terminant par un nom de fichier apparaissent, en mettant en évidence une URL de téléchargement (telle que securityblue.team/downloads/file.exe). Cette méthode peut prendre beaucoup de temps en fonction du volume d'enregistrements, mais vous pouvez également identifier d'autres activités intéressantes au cours de la recherche.
- Deuxième option - Nous pourrions utiliser le champ de recherche « Filtrer par mot clé » pour rechercher des extensions de fichiers, en recherchant des expressions telles que « .zip », « .exe », etc. Ces recherches réduiront le bruit généré par les enregistrements qui ne contiennent pas de nom de fichier, mais nous devrons parcourir chaque type de fichier jusqu'à ce que nous trouvions ce que nous cherchons. Si nous oublions de rechercher un type de fichier, il se peut que nous manquions l'activité correspondante.
- Option 3 - Tous les fichiers téléchargés dans BHV sont préfixés par « file :///». Nous pouvons l'utiliser pour voir le nom du fichier et l'endroit où il a été enregistré sur le système. C'est le moyen le plus rapide, et une fois que nous avons récupéré le nom du fichier, nous pouvons l'utiliser dans le champ de recherche pour trouver d'où il a été téléchargé !

En utilisant la troisième option et en filtrant d'abord par date de visite la plus récente, nous trouvons un fichier ZIP avec un nom inhabituel. Cela vaut vraiment la peine d'être étudié plus avant !

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/b1ea4ba61281d08b0e4e455cc575d2f7731dc73b35b7e74365927296923bbaacfda17448a99bf782b5d7ff1fb9d3.PNG)

---

**Question 6 - Sur la base de l'historique de navigation de l'employé au moment du téléchargement du fichier, quelle est la source probable de l'URL malveillante ?**

Maintenant que nous avons trouvé le fichier suspect, nous pouvons commencer à regarder de plus près. Bien que l'URL qui héberge le fichier nous intéresse, en regardant plus loin dans le temps, nous pouvons comprendre exactement comment ils y sont arrivés. En recherchant le nom de fichier, nous pouvons trouver l'URL d'hébergement.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/e8d60e60b558ee781435cd69abdc761b766e34241c56e2e62f4d674f02ebd9bb9575833fa5fa0f35069faf22b2f7.PNG)

Nous savons donc que l'utilisateur a visité cette URL et a téléchargé le fichier sur son bureau à 12:14:09. Effacons tous nos filtres en cliquant sur « Réinitialiser » sur le côté droit. Nous utiliserons ensuite la colonne Date de visite pour trouver l'horodatage 19/06/2022 12:14:09, ce qui nous permettra de voir les enregistrements survenus avant cet événement de téléchargement.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/97c0fa62eb6529af895244109fa1e9d5ae4eb0691799e6541f75a3fb67e57bbba98467989202fd2e6f43a22e3fd3.PNG)

Sur la base des informations ci-dessus, nous pouvons en déduire que le trajet suivant a été effectué par l'utilisateur :

- 1) L'utilisateur accède à la page de connexion d'Outlook.
- 2) L'utilisateur se connecte avec succès et accède à sa boîte de réception.
- 3) L'utilisateur télécharge le fichier zip, probablement à partir d'un e-mail dans sa boîte de réception. Le fichier est téléchargé sur leur bureau.

Il convient de mentionner que nous ne pouvons pas être sûrs à 100 % que cette activité représente une URL dans un e-mail, sans avoir réellement accès à leur boîte de réception pour confirmer cette découverte. Il est tout à fait possible que l'utilisateur se connecte à son compte de messagerie puis saisisse manuellement l'URL dans un navigateur pour le visiter. Toutefois, sur la base des informations dont nous disposons et des horodatages très rapprochés, l'explication la plus probable est un lien contenu dans un e-mail.

Par conséquent, la réponse à cette question sera le domaine indiqué dans la section 2 surlignée.

---

**Question 7 - Quel est le nom de domaine à partir duquel le logiciel malveillant a été téléchargé ?**

Nous avons déjà trouvé la réponse à cette question à la question 6 ci-dessus (illustrée dans la section 3 surlignée).

---

**Question 8 - Recherchez l'URL du logiciel malveillant sur https://urlhaus.abuse.ch (en dehors du laboratoire) pour savoir quel type de logiciel malveillant a été téléchargé**

En visitant URLHaus et en recherchant l'URL de téléchargement complète, nous pouvons constater, d'après les balises, qu'il s'agit du malware Quakbot !

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/5669244a693ee752f488dd8af2b7376c98057d34b499e0b7e73ee5e973664df5d48d5fce9a07740324462010f620.PNG)

Pour en savoir plus sur cette URL, vous pouvez cliquer sur l'URL en lien hypertexte dans les résultats de recherche (ne vous inquiétez pas, cela vous amène simplement à une page plus détaillée).

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/9a79491a156c9f9d4414739d2aab6ccc5bdae95494050a5c3111ee95d91547500b40f9239fc64406cbcc4a9fc1d7.PNG)

---

Utiliser RBCmd.exe pour analyser les fichier supprimés de la corbeille.

- ID d'événement 4624 (connexion réussie)
- ID 4672 (Ouverture de session spéciale)
- ID 4625 (échec de connexion)
- et ID 4634 (Logoff)
Les journaux d'événements Windows sont stockés à l'emplacement suivant : `C:\Windows\System32\winevt\Logs`

**Analyse des artefacts, 4624 Connexion réussie**

Tout d'abord, nous devons comprendre quelles informations nous sont fournies dans ces journaux. Commençons par 4624, qui indique les connexions réussies au système.

L'une des propriétés les plus importantes à noter est le type de connexion, où il existe 8 valeurs possibles :

2 — Interactif (connexion interactive, c'est-à-dire connexion physique à l'appareil)  
3 — Réseau (accès au système via le réseau)  
4 — Batch (démarré en tant que traitement par lots automatique)  
5 — Service (un service Windows démarré par le contrôleur de service)  
6 — Proxy (connexion par proxy ; non utilisé dans Windows NT ou Windows 2000)  
7 — Déverrouillage (déverrouillage du poste de travail - pensez à une connexion interactive, mais déverrouillage pour reprendre une session précédente)  
8 — NetworkClearText (réseau connexion (avec des informations d'identification en texte clair) 9 — NewCredentials (utilisé par RunAs lorsque  
(l'option /netonly est utilisée)

**Analyse des artefacts, 4672 Ouverture de session spéciale réussie**

Les événements d'ouverture de session spéciaux se produisent lorsqu'un utilisateur disposant de privilèges administratifs se connecte au système

**Analyse des artefacts, échec de connexion 4625**

Les événements d'échec de connexion sont très utiles pour nous, en particulier lorsqu'il s'agit de répondre à un incident. Cela est dû au fait que ces journaux contiennent des codes d'erreur qui nous aident à comprendre exactement pourquoi la tentative de connexion a échoué. Les différents codes d'erreur sont les suivants :

|CODE D'ERREUR DU JOURNAL NETLOGON|DESCRIPTION|
|---|---|
|0xC0000064|L'utilisateur spécifié n'existe pas|
|0xC000006A|La valeur fournie comme mot de passe actuel n'est pas correcte|
|0xC000006C|Politique de mot de passe non respectée|
|0xC000006D|La tentative de connexion n'est pas valide en raison d'un nom d'utilisateur incorrect|
|0xC000006E|La restriction du compte utilisateur a empêché la connexion|
|0xC000006F|Le compte utilisateur est soumis à des restrictions de temps et ne peut pas être connecté pour le moment|
|0xC0000070|L'utilisateur est soumis à des restrictions et ne peut pas se connecter à partir du poste de travail source|
|0xC0000071|Le mot de passe du compte utilisateur a expiré|
|0xC0000072|Le compte utilisateur est actuellement désactivé|
|0xC000009A|Ressources système insuffisantes|
|0xC0000193|Le compte de l'utilisateur a expiré|
|0xC0000225|L'utilisateur doit modifier son mot de passe avant de se connecter pour la première fois|
|0xC0000234|Le compte utilisateur a été automatiquement verrouillé|

Un volume élevé de tentatives de connexion à un compte désactivé (_0xc00000072_) ? Suspect.  
Un grand nombre de tentatives de connexion à un compte qui n'existe pas (nom d'utilisateur incorrect, _0xC0000006D) ?_ Suspect. Bien que la plupart des SoC utilisent ce journal et les codes d'erreur qu'il contient pour générer des alertes, il est certainement utile pour nous en tant qu'enquêteurs judiciaires.

Sur Windows 10, nous pouvons trouver le répertoire de la corbeille pour tous les utilisateurs situé à l'adresse `C:\$Recycle.Bin`
Nous devons utiliser `dir /a` car les dossiers sont masqués par défaut et l'indicateur /a les affichera.

Nous pouvons voir que certains sous-dossiers utilisent des identifiants de sécurité de compte comme nom (SID). Il est facile de savoir à quel nom d'utilisateur le SID se rapporte à l'aide de Windows Management Instrumentation Command (WMIC) : `wmic useraccount get name, SID`

cd C:\$Recycle.Bin
dir /a

**`C:\Users\BTLOTest\Desktop\Recycle -Bin-Analysis\Tools\RBCmd.exe -d. --csv C:\Users\BTLOTest\Desktop`**
(C'est tout sur la meme ligne)

C:\$Recycle.Bin>C:\Users\BTLOTest\Desktop\Recycle-Bin-Analysis\Tools\RBCmd.exe -d. --csv "C:\Users\BTLOTest\Desktop

Utiliser CSVQuickViewer pour mieux visualiser la réponse

C:\$Recycle.Bin \ _S-1-5-21-4001622725-2027095096-2530479061-1008_ \ $IK1SRL4
La partie en italique c'est le PID du user

Exemple :

**Question 1) Quelle est la valeur FileName du plus gros fichier supprimé détecté ?**

Tout d'abord, nous allons taper CMD dans le menu Windows et cliquer dessus avec le bouton droit de la souris pour l'exécuter en tant qu'administrateur. Nous allons ensuite placer le CD dans le répertoire de la corbeille.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/5c4d97bdb26665b60ad43698adbf9a16fbffd0832f60136bebc14195f3080ec40974e3efc73c167d37f8f3241639.png)

Ensuite, nous allons exécuter RbCmd à l'aide de la commande suivante :

`**C:\Users\BTLOTest\Desktop\Recycle -Bin-Analysis \ Tools \ RBCmd.exe -d. --csv C:\Users\BTLOTest\Desktop \**`

==NE PAS OUBLIER LE . (POINT) après le -d==

Cela exécutera RBCmd.exe dans le répertoire de la corbeille et générera un fichier CSV dans un dossier de sortie sur notre bureau appelé « Output ».

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/b884d36a88540b8d1cfac6d9dd859fad741b56f82d806594c3c1bb93a7f41ace74d8deaf70fb20824491483c1130.png)

Nous allons ensuite ouvrir l'application CSVQuickViewer à partir du dossier du bureau.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/d3571a279386e9477917196543fbc05d23dcae08051606d89bb0090fd9c128fd27be46b2fa908fb73b3bd6cdb4e0.png)

Si nous recevons l'application Search for dans le Store ? popup, nous pouvons simplement cliquer sur Oui pour lancer le programme de toute façon.

Cliquez sur Ouvrir le fichier dans le coin supérieur gauche et sélectionnez le fichier CSV dans le dossier de sortie. Nous pouvons maintenant commencer à trier les résultats !

En cliquant deux fois sur l'en-tête de la colonne FileSize, nous pouvons classer les résultats du plus haut au plus bas, en nous montrant le plus gros fichier supprimé.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/2cceddc2c3f46b4e45c5ad80bcea571950142d3b477c09945d5532dab194f83298bd32bee9da62a642782be62824.png)

---

**Question 2) Quel compte utilisateur contenait le plus grand nombre de fichiers supprimés dans la corbeille, et quel en était le nombre total ?**

Pour obtenir la réponse à cette question, nous devons compter le nombre de fois qu'un compte utilisateur est présent dans la colonne FileName (car cela est plus facile que de compter les occurrences du SID). Si vous êtes toujours en train de trier FileSize du plus haut au plus bas, cliquez sur l'en-tête FileName car cela filtrera cette colonne et regroupera les résultats en fonction de la chaîne du chemin du fichier, ce qui facilitera la lecture des utilisateurs en les regroupant.

Simon.Leeves a le plus de fichiers supprimés avec 8.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/1ac8466a5f49f158693fc425696304fe7965b2eb7ac7065beb3f0d3cb4a5d82173950aaaf66cb4cd53460f459897.png)

---

**Question 3) À quelle heure le fichier « 2023 Rebrand Design Brief.pdf » a-t-il été supprimé ?**

En recherchant ce nom de fichier dans la colonne FileName, nous pouvons ensuite identifier la valeur d'horodatage DeletedOn.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/6c988cdff4ec6be7a09c320d4dd7a07a17d75c9cd7c7dc71fb08921cf62183ccfe547367083d51c13782482b2438.png)

---

**Question 4) Quel compte utilisateur a supprimé un fichier d'une taille de 542812 octets ?**

Nous pouvons rechercher cette valeur dans la colonne FileSize, puis utiliser la colonne FileName pour identifier le compte utilisateur.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/ce463f3e87b2fc797e224c6522de82f031a8d36b1695ca63882c22eee2fa54c13f61c52968a80015dd98b52b5ca1.png)

---

**Question 5) Simon Leeves a été accusé d'avoir téléchargé des fichiers confidentiels, de les avoir supprimés de la base de données, puis d'avoir supprimé ses propres copies. Quels sont les noms des fichiers qui soutiennent cet argument ?**

Deux fichiers soutiennent cette théorie, en fonction de leur emplacement au moment de leur suppression (le dossier /Downloads/ pour ce compte utilisateur) et du contenu attendu des fichiers en fonction des noms de fichiers.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/1728658239d8bcf1fcce600cf61ae895ac6a9aec0c0182192fcad4d7581e807f181b02f367715e611a0d65597d48.png)

---

**Question 6) Combien de fichiers supprimés ont été identifiés au total ?**

En comptant toutes les lignes de résultats dans CSVQuickViewer, on obtient 24 résultats.

---

**Question 7) Quels sont les 4 derniers chiffres de la valeur SID de Rick Ranchez ? (Format : XXXX**)

Sur la base d'une ligne de résultats contenant Rick.Sanchez dans la colonne FileName, nous pouvons supposer que son SID se termine par 1013. N'oubliez pas que nous pouvons vérifier cela en utilisant wmic si nous le voulons !

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/4273063665106c353caaa32e2727b4c263e3134fbf81559eee0bce382b6e703a9d52c1a40e14da4aaf17bca33307.png)


**==FAIRE TOUT CA DANS UN TERMINAL EN MODE ADMINISTRATEUR==**

Cela exécutera RBCmd.exe dans le répertoire de la corbeille et générera un fichier CSV dans un dossier de sortie sur notre bureau appelé « Output ».

Cette commande exécute l'exécutable RbCmd, lui demandant de saisir le répertoire actuel (-d.) et d'exporter un CSV vers un dossier sur le bureau de notre utilisateur.

À l'aide de CSVQuickViewer depuis le bureau, nous pouvons ouvrir le fichier CSV généré et examiner son contenu. Grâce à ce format de fichier, nous pouvons facilement voir quels fichiers ont été supprimés par l'utilisateur et à quel moment !

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/2417026fd9e1d500b2ea072c3850c2e8bbe11b49ca81ce2cb57b0f6a2acc55979aa143384fa9486f66f686464ad6.png)

Si, pour une raison ou une autre, nous voulions analyser la corbeille de tous les comptes locaux d'un système, nous pourrions exécuter RbCmd à partir du répertoire C : $Recycle.Bin et l'argument use (-d.) pour pointer l'outil vers ce répertoire. Il parcourra ensuite de manière récursive chacun des sous-dossiers SID à la recherche de fichiers $I à analyser.

---

**/var/lib**
Sur les systèmes basés sur Debian, nous pouvons trouver un fichier très utile à l'emplacement suivant : /var/lib/dpkg/status. Ce fichier contient une liste de tous les packages logiciels installés en fonction du user

On peut filtrer la sortie :

`cat status | Package grep > packages.txt`

- cat status va lire le fichier.
- grep Package recherchera toutes les lignes contenant « Package »
- > packages.txt affichera les résultats dans un fichier texte appelé packages.txt

**/var/log

1. **/var/log/auth.log** : contient les informations d'authentification du système, y compris les connexions des utilisateurs.  
    ![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/d334a78e3f10942aa70f8c93855db0b9f8ae0bb97834cbec73c33a9b3d9bc74336f8057286fb4f8d49e50fc4b8c8.png)
2. **/var/log/dpkg.log** — Contient des informations enregistrées lorsqu'un package est installé ou supprimé à l'aide de la commande « dpkg ». Cette commande est similaire à la commande packages de la section var/lib ci-dessus.  
    ![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/278766abf71b4e40c0dd1881bcdf02afe7d4284c5b4576201c8709cbe67cff785429ddeb14d6ca120111aca067d5.png)
3. **/var/log/btmp** — Ce fichier contient des informations sur les tentatives de connexion infructueuses.
4. **/var/log/cron** — Chaque fois que le démon cron lance une tâche cron, il enregistre les informations relatives à cette tâche dans ce fichier. Cela est utile car les tâches cron peuvent être utilisées à mauvais escient à des fins de persistance sur un système.
5. **/var/log/secure** : contient des informations relatives aux privilèges d'authentification et d'autorisation. Par exemple, sshd (le démon utilisé pour le service SSH) enregistre tous les messages ici, y compris les tentatives de connexion infructueuses.
6. **/var/log/faillog** — Contient les tentatives de connexion infructueuses de l'utilisateur.

**var/log/apache2/access.log** qui nous fournit des informations sur les demandes adressées au serveur Web, y compris des valeurs telles que :

- Adresse IP du client à l'origine de la demande
- La ressource à laquelle ils essaient d'accéder
- La méthode HTTP, qui sera le plus souvent GET (pour obtenir une ressource, telle que des images dans une page Web)
- L'agent utilisateur utilisé par l'adresse IP du client (il doit généralement s'agir d'un agent utilisateur du navigateur, tel que Chrome, Firefox, etc.)
- et l'horodatage de la demande

Regardons un exemple.

`**52.50.100.106 - SBT Utilisateur [27/Jul/ 2020:15:30:00 -0600] « GET /logo.png HTTP/1.1" 200 379**`

1. 52.50.100.106 - L'adresse IP du client qui fait la demande au serveur Web
2. SBT Utilisateur : l'identifiant du compte à l'origine de la demande (s'il est connecté et si le site Web utilise des comptes)
3. [27/Jul/ 2020:15:30:00 -0600] - L'horodatage de la demande
4. « GET /logo.png HTTP/1.1 » - La ressource à laquelle vous accédez, dans ce cas, l'adresse IP récupère le fichier image du logo afin qu'il puisse être affiché sur une page
5. 200 - Le code de réponse HTTP. Dans ce cas, c'est 200 OK (accès réussi). Dans d'autres cas, il peut s'agir de 404 si la ressource n'est pas trouvée.
6. 379 - La taille du fichier envoyé au client (dans ce cas, la taille du fichier logo.png)

Historique des commandes sur linux : **.bash_history**

- **steghide** — invoque l'outil que nous voulons utiliser
- **embed** — sélectionne l'opération que nous voulons utiliser, dans ce cas intégrer un fichier dans un autre
- **-cf Dog.jpg** — le flag « fichier de couverture » est l'endroit où nous indiquons le fichier qui contiendra le fichier caché
- **-ef secretmessage** — l'indicateur « intégrer le fichier » est l'endroit où nous indiquons le fichier que nous voulons cacher dans le fichier de couverture

---

# Volatility

| Commande (exécutable)                                                | Objectif / description                                                         | Exemple (remplace `PROFILE` par le profil suggéré)                   | Remarques / sortie attendue                                                                                                  |
| -------------------------------------------------------------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `volatility -f memdump.mem imageinfo`                                | Détecte et suggère le profil mémoire (OS, version, architecture)               | `volatility -f memdump.mem imageinfo`                                | Affiche plusieurs profils suggérés et métadonnées (date/heure, pointeurs, etc.). Utilisé avant d’appliquer `--profile`.      |
| `volatility -f memdump.mem --profile=PROFILE pslist`                 | Liste les processus actifs vus via les structures internes (EPROCESS)          | `volatility -f memdump.mem --profile=PROFILE pslist`                 | Liste “linéaire” des processus ; bon point de départ pour l’analyse des processus.                                           |
| `volatility -f memdump.mem --profile=PROFILE pstree`                 | Affiche l’arbre des processus (parent/enfant)                                  | `volatility -f memdump.mem --profile=PROFILE pstree`                 | Utile pour visualiser la hiérarchie des processus et repérer processus orphelins/suspects.                                   |
| `volatility -f memdump.mem --profile=PROFILE psscan`                 | Recherche tous les processus en mémoire (y compris cachés ou non listés)       | `volatility -f memdump.mem --profile=PROFILE psscan`                 | Détecte processus supprimés ou masqués ; compare avec `pslist` pour anomalies.                                               |
| `volatility -f memdump.mem --profile=PROFILE psxview`                | Agrège plusieurs vues/process plugins pour révéler processus cachés            | `volatility -f memdump.mem --profile=PROFILE psxview`                | Combine résultats (`pslist`, `psscan`, autres) et montre indicateurs d’incongruence.                                         |
| `volatility -f memdump.mem --profile=PROFILE netscan`                | Identifie connexions réseau (sockets, connexions TCP/UDP) présentes en mémoire | `volatility -f memdump.mem --profile=PROFILE netscan`                | Affiche IP/ports, états (LISTEN, ESTABLISHED). Peut requérir profile adéquat (Windows modernes).                             |
| `volatility -f memdump.mem --profile=PROFILE timeliner`              | Génère une chronologie d’événements extraits de la mémoire                     | `volatility -f memdump.mem --profile=PROFILE timeliner`              | Produit une timeline brute (timestamps, évènements divers) pour analyse forensique temporelle.                               |
| `volatility -f memdump.mem --profile=PROFILE iehistory`              | Récupère l’historique de navigation Internet Explorer depuis la mémoire        | `volatility -f memdump.mem --profile=PROFILE iehistory`              | Valeur limitée aux versions/artefacts IE ; utile si l’IE a été utilisé sur la machine.                                       |
| `volatility -f memdump.mem --profile=PROFILE filescan`               | Scanne en mémoire les objets fichiers (FILE_OBJECT, etc.)                      | `volatility -f memdump.mem --profile=PROFILE filescan`               | Liste fichiers/objets trouvés en mémoire ; utile pour repérer fichiers récemment ouverts ou fichiers malveillants résidents. |
| `volatility -f memdump.mem --profile=PROFILE dumpfiles --dump-dir=.` | Extrait (dump) les fichiers trouvés en mémoire vers un dossier local           | `volatility -f memdump.mem --profile=PROFILE dumpfiles --dump-dir=.` | Récupère fichiers (par ID ou pattern). Vérifie l’emplacement de sortie (`--dump-dir`) et permissions.                        |
| `volatility -f memdump.mem --profile=PROFILE dumpfiles -D .`         | Variante courante pour écrire les fichiers extraits dans le répertoire courant | `volatility -f memdump.mem --profile=PROFILE dumpfiles -D .`         | `-D` est équivalent à `--dump-dir` selon les versions/plugins ; toujours vérifier la version de Volatility.                  |
Compter le nombre d'occurrence : **python vol.py -f Volatility memdump1.mem --profile=win7sp1x64 pslist | grep « svchost.exe » | wc -l**

**Question 7 - memdump1.mem - Liste des processus 4 - L'un des processus svchost est malveillant. Quel est le PID de l'étrange processus svchost.exe ?**

Pour nous fournir plus de contexte que la simple liste des processus, nous utiliserons le plugin « pstree » pour montrer les relations parent-enfant entre les processus. Nous pouvons voir que le premier processus svchost.exe crée un processus enfant cmd.exe, dans lequel la commande ping est utilisée, car nous pouvons voir que le processus ping.exe est utilisé. C'est vraiment une activité inhabituelle !

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/545be0170ad5167923528d8ed5c422f7bc8c1b88b6797d262fa225b4408e55dfa392e9ce795496b8426cdef15e03.png)

**Question 8 - memdump1.mem - Liste des processus 5 - Quelle est la ligne de commande du processus avec le PID 2352 ?**

En utilisant le plugin « cmdlist » et en pointant vers le pid spécifique Volatility à l'aide de l'indicateur « -p », nous pouvons extraire les arguments de ligne de commande que ce processus utilisait. `**python vol.py -f /home/ubuntu/desktop/ \ Exercise/MemDump1.mem --profile=Ligne de commande Win7SP1x64 -p Volatility 2352**`

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/725a36255f0a0515bcc1d0aa7c9bcfdfb2b1d41d9d23114b3e2318aa258f630550a40c70e16717b7d1e3c9693a8e.png)


**Question 10 - memdump2.mem - Sauvegarde du processus - Sauvegardez le processus avec le PID 2940 et calculez le hachage MD5. Soumettez les 5 premiers caractères**

En utilisant le plugin « procdump » et en fournissant le PID à l'aide de -p, nous pouvons extraire le fichier. Nous utiliserons ensuite « md5sum » pour obtenir la valeur de hachage MD5. `python vol.py -f memdump2.mem --profile=Win7SP1x64 procdump -p Volatility 2940`

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/eb4e8460c4b7155959d296b2bd195f71c82a726a3dfa1121e47f745a83fa474c76d90d752394511d807393480941.png)

**POUR VOLATILITY 3**

|Command Purpose|**Volatility 2 Command**|**Volatility 3 Command**|
|---|---|---|
|Get process tree|volatility --profile=PROFILE pstree -f file.dmp|python3 vol.py -f file.dmp windows.pstree|
|List services|volatility --profile=PROFILE svcscan -f file.dmp|python3 vol.py -f file.dmp windows.svcscan|
|List available registry hives|volatility --profile=Win7SP1x86_23418 -f file.dmp hivelist|python3 vol.py -f file.dmp windows.registry.hivelist|
|Print cmd commands|volatility --profile=PROFILE cmdline -f file.dmp|python3 vol.py -f file.dmp windows.cmdline|
https://blog.onfvp.com/post/volatility-cheatsheet/

**Question 1) When refreshing the process list - what plugin is volatility actually using? (Format: Command.command)**

In the main window of Workbench we can see that after clicking the Refresh Process List button, Workbench is just running the windows.pslist command:

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/2448bb384aaa533963c59608781dbb00b3919a1c6a199851389be1c11f72c75eccc637eb11bf8c7193dd11cee65f.png)

**Question 2) Select the windows.info.info plugin from the drop down list. What version of the Windows Operating system is being used on the system the memorydump is taken from? (Format: Windows Version)**

 Selecting the command provided in the question within the output we can see the following lines of interest:

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/9cea979f55b974eb4b4688941e48b882b38dc6f0fa967494af926de3f7cd03869e0405750103bd0a5424222368e1.png)

Combining the SystemRoot and MajorOperatingSystemVersion, we can identify that the machine the memory image was taken from is running Windows 10.

**Question 3) Run the windows.pstree.PsTree command and use the process ID drop down menu to help filter out the noise. What is the parent process of Powershell.exe? (Format: PID, ProcessName)**

We'll select the windows.pstree command and click the Process ID checkbox which gives us a dropdown to select the process we want to focus on. Based on the question, we'll find and click on PowerShell.exe that has a PID of 4708. Now we can run the command.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/c264779edeeb60a31154f54dc6774e0ba12ed28602af2fa943117c19031dd5ef60c605a16b76afa918dfa9e9d9d9.png)

In the above output we can see that the parent process of PowerShell.exe is CompatTelRunne which has a process ID of 5264.

**Question 4) Use the windows.privileges command. The process 2416 has the ability to 'Add Workstations to the Domain. What is the attribute associated with this privilege? (Format: AttributeName)**

The question specifically mentions process 2416, so we'll click the Process ID checkbox and select this process from the dropdown menu, which is listed as HxTsr.exe (2416).

Looking through the output we can find a reference to “Add workstations to the domain” which has a Privilege Attribute value of “SeMachineAccountPrivilege”.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/fa16aafc13b6dd69a402fabacb77156c9d417be9756b56c9972cd2f3c77ac37cc8b98e03f00a4023389ddc49b7c0.png)

**Question 5) Pick a plugin to analyse the command-line arguments executed by process 2416. What is the server name the executable is parsing in its command? (Format: ServerName)**

Looking through the command dropdown menu for a relevant plugin, we find windows.cmdline.CmdLine, which seems like it'll do what we need. We'll click the Process ID checkbox and select HxTsr.exe (2416) and run it.

In the output we can see the ServerName value is HX.IPC.Server:

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/3dc04604640d8331dfadfd1b0ced1fa25e5780990753f16452e2061920c56e9ffd326092767b1adf5c9238f7337d.png)

# Autopsy

Nous devons d'abord ouvrir Autopsy . Lorsque l'écran ci-dessous s'affiche, cliquez sur Nouveau dossier.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/180d723ef89b9fb27432cbaae8d9c44362391ddd7f0bd0030c4c3a8f51a087f829c207b73ff928618dbb52de9d91.png)

Ici, nous devons fournir un nom et un répertoire de base pour stocker tous nos fichiers. Nous avons sélectionné le nom «  BTL1   Autopsy  Procédure pas à pas » et l'avons enregistré dans un répertoire portant le même nom dans notre dossier de documents.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/1faa0dc77704213d2fdee325026ecbec06a597a770b1b97398882009ddbe685ff294827b53672541e18e35aaf574.png)

L'écran suivant nous demandera de saisir certaines informations facultatives concernant l'enquête. Nous n'avons pas besoin de l'utiliser, mais c'est ainsi que les équipes de sécurité et les forces de l'ordre ajouteront des métadonnées liées aux enquêtes. Autopsy

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/3cd1fd757e33ef5fbc2c65a525bf0951895dd31e27316202eef5b6d14fc52c4bc50acbf2559aa10a1af8ade02796.png)

Autopsy devrait alors nous demander d'ajouter notre source de données. Dans ce cas, il s'agit d'une image disque. Nous devons donc sélectionner « Image de disque ou fichier de machine virtuelle », puis cliquer sur Suivant.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/a063c6c89257631bf6f5825254b4630ef5e5da6420a7a669467b628d036169734192819394e056722e7a17c5af67.png)

Nous cliquerons sur Parcourir et sélectionnerons le fichier image disque .E01 que nous utilisons pour cette procédure pas à pas, puis nous cliquerons sur Suivant pour l'ajouter en tant que source de données pour notre enquête. Il nous sera ensuite demandé si nous voulons exécuter des modules d'ingestion. Il s'agit d'actions automatisées qui peuvent être effectuées sur une source de données afin de récupérer des informations utiles au médecin légiste et de lui faire gagner du temps. Pour cette procédure pas à pas, nous souhaitons sélectionner « Tous les fichiers, répertoires et espace non alloué » dans le menu déroulant, car cela permet de sélectionner les cibles sur lesquelles les modules d'ingestion seront exécutés. Ensuite, vous devez sélectionner les options suivantes :

- Activité récente
- Identification du type de fichier
- Extracteur de fichiers intégré
- Analyseur Exif
- Analyseur d'e-mails
- Détection du chiffrement

Notez que certains de ces modules d'ingestion peuvent changer de nom !

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/acbbd2a2822ab61a22d6f9074f07b02b4b750375feae59327a9c6d6ddc7ef77fdf3b0116c28b4789918025c60910.png)

Dans le coin inférieur droit, vous verrez une barre de progression qui vous indiquera quand chaque module d'ingestion est terminé. Autopsy Accordez quelques minutes pour terminer l'analyse de la source de données. Vous devez également remarquer que les valeurs affichées dans le volet de gauche augmentent lorsque les modules d'ingestion s'exécutent, car ils découvrent des informations importantes et les placent dans l'arborescence des artefacts afin de permettre à l'examinateur de les examiner plus en profondeur.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/f8cf0e75240def3a0fbe5e0db77dc82ac8a5ed4a9adcb5d3c2c7c818e004973bc85b2700ef0439186b8e275824be.png)

## **Analyse des résultats du module Ingest**

À présent, tous les modules d'ingestion devraient être terminés et vous ne verrez pas la barre de progression dans le coin inférieur droit de Autopsy . L'arborescence de navigation du volet de gauche doit également comporter des chiffres à côté des titres, indiquant que les informations ont été trouvées et triées en différentes catégories. Nous allons maintenant vous expliquer certaines des informations extraites de l'image du disque dur. Autopsy

La première chose que nous voulons examiner concerne les volumes du disque dur afin de collecter des informations telles que l'espace alloué et non alloué, la taille de ces partitions et le ou les formats utilisés. En haut de l'arborescence de navigation, cliquez sur l'icône + à côté de Data Sources, puis sur l'icône + à côté de Craig Tucker Desktop.E01. Trois volumes s'afficheront : vol1, vol2, vol3.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/4ad70e23ef7a24d39b2b658783e3812ff21263396f3b1f673a67d2bf7bd5cad46153f7ba25e2bfe535bb93b308e0.gif)

Si nous cliquons avec le bouton gauche de la souris sur Craig Tucker Desktop.E01 dans l'arborescence de navigation, le volet de droite affiche désormais des informations sur les volumes détectés. C'est ce que l'on appelle la table de partition.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/c84fff9b8d7b43b42e5b217ab7dfe8c50fd9c58fe6f884a881723aa1e952c77578922535ab9324a4fe29b1d0e27e.png)

Dans la capture d'écran ci-dessus, nous pouvons voir que le volume 2 est formaté avec NTFS /exFAT, qu'il commence au secteur 2048 et que sa longueur est de 125825024. Il s'agit de la section principale du disque dur et c'est là que se trouve la structure des fichiers. Tout, des utilisateurs aux documents et aux téléchargements, se trouvera dans ce volume. Si vous double-cliquez sur vol2, une structure de fichiers en lecture seule s'affiche, ce qui nous permet de parcourir les fichiers comme si nous étions assis devant un ordinateur portable !

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/086233e0c6af9557146fd8feab71949b171b991e7b5e5abad996ff58869dbc69143038f9bc44419ea63787641d06.png)

Passez une minute à parcourir les répertoires pour voir ce que vous pouvez trouver. Il est bon de se familiariser avec cette méthode de navigation dans les images médico-légales, car les personnes qui utilisent Windows au quotidien seront probablement habituées à naviguer dans la structure des fichiers.

Maintenant que vous avez jeté un coup d'œil, il est temps de voir les résultats des modules d'ingestion, qui se trouvent dans l'arborescence de navigation sous l'en-tête **Résultats**, illustré ci-dessous.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/2661942374aec7bd4667f073429f5518a05df3a16542ff9f214b03f86a38795e8da97cc257e86109c79e6f20fe5f.png)

Examinons quelques-uns de ces résultats. Pour commencer, cliquez sur l'historique Web en bas de la page. Cela nous montrera les sites qui ont été visités sur le système, y compris la date d'accès, le titre de la page s'il est disponible et le programme utilisé pour accéder à la ressource Web. Par exemple, la ligne surlignée indique qu'un utilisateur s'est rendu sur 4chan.org/rules via le navigateur Chrome le 18/12/2013 à 02h35 GMT.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/beba0fd2f910eff76cd59b87c658e39f9695ccaaf42bf4be363c9de0bb6f68337b8ff1e5cf8942d03c2db9e9a93b.png)

C'est un excellent moyen de consulter les habitudes de navigation et les sites consultés par un suspect. Les horodatages nous aident également à créer une chronologie des événements survenus et peuvent être utilisés pour prouver qu'un utilisateur a consulté des ressources un jour donné, ce qui peut faciliter une enquête.

Voyons maintenant quels fichiers l'utilisateur a supprimés en accédant à la corbeille dans l'arborescence de navigation. Dans le volet de droite, nous pouvons maintenant voir que l'utilisateur a supprimé trois fichiers et nous indiquent leurs chemins d'accès, l'utilisateur qui les a supprimés et l'heure à laquelle le fichier a été supprimé. Cela peut être une solution rapide si nous cherchons à identifier les fichiers qui ont été supprimés et à obtenir des informations à leur sujet.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/8d803dcd13a1bd0f3fff9257d39832d934d004ce2051bf4ba43fc4b5280a5dd4f8e9b18d4060031fa4cb3242c598.png)

Nous pouvons en fait exporter ces fichiers pour les consulter (cela ne se limite pas aux fichiers de la corbeille, nous pouvons le faire avec tous les fichiers identifiés dans l'image du disque !). Cliquez avec le bouton droit sur le chemin de « Underage_lolita_r@ygold_001.jpg » **(ne vous inquiétez pas, cette image n'est pas explicite, c'est juste un exemple de nom pour le scénario d'enquête)**.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/ebd36cf300ebf76754a97cb1933f3836577feec31ca78e8380454dd06b3aa9c2a19ce1b801d90f945beb44e6d94c.png)

Sélectionnez la destination vers laquelle vous souhaitez exporter le fichier, puis ouvrez-le. Vous trouverez ci-dessous l'image que nous venons d'extraire de l'image du disque.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/992a82be00788abe2524ea0c3a2bd2b2809db000bcb5b72eb0fadd608c94c090bcdf45e0b74037826ed9fd17df0e.png)

Cette fonctionnalité peut être utile si l'enquête portait sur l'exploitation d'enfants, car elle permet aux légistes d'identifier des images potentiellement explicites, de les exporter et de confirmer si le matériel peut être utilisé comme preuve dans le cadre de poursuites judiciaires contre le suspect.

Passons maintenant à la section Programmes installés pour identifier les logiciels installés sur ce système. Cliquez avec le bouton gauche sur le titre et dans le volet droit, vous pouvez maintenant voir une liste des programmes installés. À partir de là, nous pouvons déterminer quand les programmes ont été installés et leurs noms, à l'aide de certaines entrées, notamment WinRAR, GIMP, WinZip et Google Chrome.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/eaa4e728e4f657814ff349a5aa50ebcda5c5de3ea7b9fa093b45d72c3a9bd910105fc2801c75f4794434f93f8ff0.png)

Passons en revue ensemble une autre section, « Comptes > E-mail » en bas de l'arborescence de navigation. Vous pouvez voir ici la liste des fichiers de courrier électronique qui ont été téléchargés sur le système, généralement via un client de messagerie.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/05f5004f01650964dc06788fb0a73cb7ebfbf726af8999b41553cad0125dbd930a8d2e3b548f85e4e8748b0bd31d.png)

Maintenant que vous savez comment exporter un fichier en cliquant avec le bouton droit de la souris, exportons le fichier e-mail sélectionné et examinons-le (vous aurez besoin d'un client de messagerie si vous souhaitez le voir tel que l'expéditeur et le destinataire le verraient, comme Mozilla Thunderbird ou Microsoft Outlook App). Vous pouvez également lire le contenu en ouvrant l'e-mail avec un éditeur de texte).

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/d020278000d0df4dfe822feeaf8ce520915e60fed5aeff1a76e9f040aaa5669b5e37634929660915a4ff492b0453.png)

La lecture des e-mails d'un suspect peut aider à recueillir des preuves concernant l'affaire dans le cadre d'une enquête judiciaire, ou à des fins de réponse à un incident, nous pouvons chercher à identifier les e-mails malveillants présents sur le système au moment de la compromission. Nous pourrions ensuite les analyser pour collecter des indicateurs tels que :

- Expéditeur du message
- Destinataire de l'e-mail
- Date et heure
- Ligne d'objet
- IP du serveur d'envoi
- et bien plus encore !
---
# Autopsy Lab

Après l'ouverture Autopsy , dans le dossier «  Autopsy  Pour l'analyse des disques » sur le bureau, on nous demandera si nous voulons ouvrir un dossier ou en créer un nouveau. Cliquez sur Créer un nouveau dossier. Il vous sera demandé de fournir certaines informations, vous pouvez nommer le dossier comme vous le souhaitez.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/13f9edd4c729e15c595cd2199e6b0703a01ea836299bca63ea0a331650403e02f938a0fa6a2451565acf51858b21.PNG)

Nous devons sélectionner un répertoire de base pour notre enquête, qui doit être un dossier vide. Cliquez sur Parcourir, accédez au bureau, puis cliquez sur l'icône en haut à droite pour créer un nouveau dossier.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/5d34bf297cfe83965d5c7a803acd1395d0646ab8227c9d40ee611cc9760be7c11302f9d2c54a4e8f82df4c7416c1.PNG)

Après avoir cliqué sur Suivant, notre dossier sera créé dans Autopsy . Nous devons cliquer sur « Ajouter une source de données » dans le coin supérieur gauche. Lorsque vous êtes invité à sélectionner un hôte, laissez-le comme option par défaut (première option) et cliquez sur Suivant. Nous sommes maintenant invités à importer une image, à la laisser comme première option et à accéder au dossier Autopsy For Disk Analysis, puis à Laptop Image, puis à sélectionner le fichier ci-dessous.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/39492c9e84c80f0c0fe6176f75eb3e7d357244565e64db93668175ff7206677fb2027603b2b9b3d097236523e788.PNG)

À l'étape 4, on nous demande quels modules d'ingestion nous voulons exécuter sur l'image disque, afin de nous aider à récupérer rapidement des informations intéressantes. Cliquez sur Tout désélectionner, puis cochez les deux modules ci-dessous.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/fb2583fa8fe48aa217531565c9dae4f3ef077d811e0a8e573f5f72ea0a1b96387e1cd24152b913c9f6da00a6d9f6.PNG)

Autopsy va maintenant commencer à importer et à traiter l'image du disque et les modules d'ingestion. Laissez cela fonctionner pendant environ 10 minutes, puis vous serez prêt à commencer à répondre aux questions !

---

**Question 1 - Quel est le système d'exploitation (et la version du système d'exploitation) utilisé par l'ordinateur portable suspect ?**

Pour trouver le système d'exploitation de l'appareil, vous pouvez consulter la section « Artefacts de données > Informations sur le système d'exploitation ». En faisant défiler le tableau vers la droite dans le panneau de gauche, nous pouvons voir le système d'exploitation répertorié sous la forme « Nom du programme ».

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/1be2a1be291a99f3c17fcd219bb8ea939f28492bfa453aae6dbcdb9ff706c20aded629a6fe86f2e3d2f364d3133b.PNG)

---

**Question 2 - Quel est le nom d'hôte du système ?**

Dans la même section que ci-dessus, vers la gauche du tableau, nous pouvons voir le nom d'hôte répertorié sous la forme « Nom ».

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/86b49231cdca4045fb384a813423cfd8824b554d1a13992ec9ef4a292b44ac387bffafd8db54fe04a85f89e3f8ef.PNG)

---

**Question 3 - Examinez les téléchargements Web qui ont été extraits de l'image disque. Quel fichier a été téléchargé le 18/12/2013 20:05:57 GMT ?**

Toujours en regardant la rubrique « Artefacts de données » dans le panneau de gauche, on nous a demandé d'étudier les téléchargements Web. Dans le tableau de droite, nous pouvons voir « Date d'accès ». Nous devons donc trouver la ligne dont la date figure dans l'horodatage de la question !

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/98e263d93f3005b866b084c2d0ad0188c13ddb9bc854fdea5a3d6a321720039930ac5f82eb4a8489e13524c2b40f.PNG)

---

**Question 4 - Quelle est l'URL complète du fichier téléchargé le 18/12/2013 03:02:50 GMT ?**

En regardant au même endroit, nous devons trouver la ligne du tableau qui correspond à l'horodatage de la question. Après l'avoir trouvée, nous pouvons voir l'URL complète dans la colonne intitulée « URL ».

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/fbed000932dc3e33e95733c1e60cad9bfa0c81a1e299283bc0cbadbd3f45ce6cd6b3d28003751ee56e47746e5257.PNG)

---

**Question 5 - En consultant les documents récents, quel est le chemin complet du fichier Pier.jpg ?**

Vous vous souvenez des fichiers LNK, que nous avons abordés plus tôt dans ce domaine ? Fichiers utilisés comme raccourcis vers le fichier réel situé sur le disque. Nous pouvons utiliser LNK pour identifier quand les fichiers ont été consultés et où ils sont stockés. L'exemple s'applique ici ! En regardant l'élément de menu « Documents récents », nous pouvons trouver le fichier Pier.lnk, qui est utilisé pour représenter Pier.jpg. Nous pouvons obtenir le chemin du fichier dans la colonne « Chemin ».

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/cf87f0f201455b719ab993a4ce4e35372f076228bd4e338591ef614607688e65ca8902f24608bcd1f26ce575def7.PNG)

---

**Question 6 - Double-cliquez sur vol2 pour accéder au système de fichiers virtuel. Accédez à Program Files > GIMP 2. Quelle est la taille du fichier du répertoire nommé « lib » ?**

Regardons le système de fichiers virtuel, comme si nous étions sur l'ordinateur lui-même ! Double-cliquez sur vol2, la plus grande partition du système de fichiers.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/e35f317e223a0c36ca9a7dc152987cf8843c0724b58442b5ccf542f0dac10faeba99d2625e349cc671ff9bd86e5b.PNG)

En passant à Program Files, GIMP 2, nous pouvons voir le dossier qui nous intéresse. La taille du fichier est indiquée sous forme de colonne à la fin de la section surlignée !

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/83c0a4401f11a2cd594e7ec40d723250bbf3a598cccc90449430ce33d655fb78a99605e57df29b18c2f8a380aa74.PNG)

---

**Question 7 - Accédez à l'onglet Comptes du système d'exploitation. Quand le compte d'administrateur local a-t-il été consulté pour la dernière fois ? (Format : AAAA-MM-DD HH:MM:SS**)

Dans la section « Comptes du système d'exploitation », nous pouvons voir tous les utilisateurs locaux qui se trouvent sur cet ordinateur. En bas, nous pouvons voir le compte administrateur, nous indiquant l'heure à laquelle il a été consulté pour la dernière fois.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/7c416bfdae41f2a64e72ec29580c5c90997afc79988bc143825a91e0556d2e30a0c9a85c5ebbd5187af93dd7d628.PNG)