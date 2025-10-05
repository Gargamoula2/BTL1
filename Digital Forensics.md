[[BTL1]]

1. **Identification** — La première étape consiste à identifier les sources potentielles de preuves ou d'informations pertinentes (dispositifs), ainsi que les principaux dépositaires et l'emplacement des données.
2. **Préservation** — Processus de conservation des informations pertinentes stockées électroniquement (ESI). Cela se fait en protégeant la scène du crime ou de l'incident, en capturant des images visuelles de la scène et en documentant toutes les informations pertinentes concernant les preuves et la manière dont elles ont été obtenues.
3. **Collecte** — Collecte d'informations numériques pouvant être pertinentes pour l'enquête. La collecte peut comprendre le retrait du ou des dispositifs électroniques de la scène du crime ou de l'incident, puis l'imagerie, la copie ou l'impression de leur contenu.
4. **Analyse** — Recherche systématique approfondie des preuves relatives à l'incident faisant l'objet de l'enquête. Les résultats de l'examen sont des objets de données trouvés dans les informations collectées. Ces sorties peuvent inclure des fichiers générés par le système et par l'utilisateur. L'analyse vise à tirer des conclusions sur la base des preuves trouvées.
5. **Rapports** — Les rapports sont basés sur des techniques et des méthodes éprouvées et d'autres légistes compétents devraient être en mesure de reproduire les mêmes résultats.

**Kroll Artifact Parser and Extractor – KAPE** est utilisé pour l’acquisition rapide de preuves numériques et de fichiers pouvant intéresser un examinateur forensic.  
L’opérateur peut définir les informations qu’il souhaite collecter en utilisant des modules, et KAPE se mettra au travail, récupérant les informations importantes en quelques minutes, alors qu’une copie forensic complète pourrait prendre des heures.

**Forensic Tool Kit Imager – FTK Imager** est un outil gratuit qui permet de prendre des images bit à bit de disques durs, de monter des images disque en mode lecture seule (bloqueur logiciel d’écriture) et offre des fonctionnalités d’analyse pour examiner les images disque.

**Browser History Capturer – BHC est** un outil gratuit qui permet à l’opérateur de collecter les fichiers principaux des navigateurs web courants, qui peuvent être examinés manuellement ou importés dans Browser History Viewer pour analyser l’historique web.

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
# FTK Imager

***Ce que peut faire FTK Imager :***
- **Videz la RAM** et stockez-la dans un fichier `**.mem**`, afin que nous puissions l'exporter vers d'autres outils, par exemple à des fins Volatility d'analyse.
- **Prendre des images de disque médico-légales** qui peuvent être analysées à l'aide d'outils tels que. Autopsy
- **Exportez des fichiers** directement à partir d'images de disque.
- **Générez des hachages MD5 et SHA1 pour les fichiers** de preuves.
- **Fournissez une vue en lecture seule** du contenu d'une image disque, exactement comme l'utilisateur l'aurait vue.
- **Et bien plus encore !**
- 
FTK Imager est un outil extrêmement puissant qui est utilisé dans le cadre d'enquêtes réelles par les enquêteurs et les équipes de sécurité. Passons rapidement en revue certaines des fonctionnalités :

- **Videz la RAM** et stockez-la dans un fichier `**.mem**`, afin que nous puissions l'exporter vers d'autres outils, par exemple à des fins Volatility d'analyse.
- **Prendre des images de disque médico-légales** qui peuvent être analysées à l'aide d'outils tels que. Autopsy
- **Exportez des fichiers** directement à partir d'images de disque.
- **Générez des hachages MD5 et SHA1 pour les fichiers** de preuves.
- **Fournissez une vue en lecture seule** du contenu d'une image disque, exactement comme l'utilisateur l'aurait vue.
- **Et bien plus encore !**


**Dump de mémoire**
  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/ba9219ef95d2f4558f265739e660ea05bffef5c5684b88bd82f5cbaf8b1be70b41567e3aa695dbbf2964e3dd7e50.png)

La première chose que nous voulons vous montrer est de prendre un instantané de la RAM du système FTK Imager sur lequel nous fonctionnons. Pour ce faire, nous allons dans **Fichier > Capturer la mémoire**.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/8d7d686cd8b967effdca6b989bc75a029820918c2a0846a3ac2777bdd3332ccd26443e3cab36c3ddf77cb7ec3c06.png)

Nous sommes ensuite invités à saisir l'emplacement dans lequel le fichier doit être enregistré. Nous avons donc créé un nouveau répertoire sur notre bureau nommé « Memory Dump ». Nous pouvons modifier le nom du fichier si nous le voulons, mais dans cet exemple, nous allons le laisser sous la forme « memdump.mem ». Comme indiqué précédemment dans ce domaine, pagefile peut contenir des preuves supplémentaires, mais nous ne les inclurons pas dans cette procédure pas à pas. En bas de la page, vous pouvez créer un fichier AD1, le type de fichier de signature de The Forensic Toolkit (TFK), un autre outil développé par AccessData. Nous laisserons ces deux options décochées et cliquerons sur « Capturer la mémoire ». FTK Imager va maintenant se mettre au travail en vidant tout ce qui se trouve dans la RAM et en le stockant dans un fichier .mem.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/4f6d3ad23b7fb17ba2a9024f5b0d4a57ecc3b27a1e69ca48710a182ff07be2b34d2657c7d9943f8aa2a159c6475f.png)

Une fois l'opération terminée, nous aurons désormais un fichier mémoire dans notre destination désignée. Nous pouvons utiliser des outils tels que Volatility l'analyse de ce vidage, mais nous aborderons ce point dans une prochaine leçon.

**Imagerie du disque dur**

Dans le monde réel, un disque dur prélevé sur une scène de crime sera connecté à un poste de travail médico-légal (un PC doté d'un matériel haut de gamme permettant d'accélérer les analyses et le transfert de données) auquel un disque dur propre sera connecté. Un bloqueur d'écriture sera utilisé entre le poste de travail et le disque dur suspect, afin d'empêcher le poste de travail de modifier accidentellement quoi que ce soit sur le disque dur, ce qui pourrait entraîner le rejet de preuves pour falsification. L'analyste judiciaire commencera ensuite à copier bit par bit le disque dur du suspect sur le disque vierge. Cela peut prendre beaucoup de temps, car il s'agit d'une copie exacte de chaque donnée, de sorte que rien n'est oublié.

Nous pouvons créer un fichier image système (`**.img**`) à l'aide FTK Imager duquel nous pouvons ensuite l'analyser pour rechercher des preuves numériques. Pour cet exemple, nous allons prendre une image disque d'une clé USB de 15 Go que nous avons. À des fins de démonstration, nous avons placé des fichiers aléatoires sur la clé USB.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/c92d5a33b41fda82f289c708b25bd3ff1b03b2a6b52eaea552f27252db646971f0933d57da6d5126fa27948d4822.png)

Dans FTK Imager ce document, nous voulons cliquer sur **Fichier**, puis aller sur **Créer une image de disque**.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/47c9705eeca789fd2b6c268703bb95e7e43745f7a93d27eb4278c1a4a2aa7e37e3ae2eef9226605d1544a77d02b3.png)

Ensuite FTK Imager , nous demanderons quelle sera la source des preuves. Lorsque nous prenons une copie des données d'une clé USB, nous devons sélectionner **Physical Drive**.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/572a30babec765d460b7dd138e95b72901f8bda320e0de5dc212f6559b9388a03de83b67232948b05cb19ab6f4c3.png)

Comme nous avons sélectionné Physical Drive, nous FTK Imager allons maintenant nous demander de sélectionner les lecteurs actuellement connectés au système exécutant l'outil. Dans la liste déroulante, vous pouvez voir le SSD de 500 Go et le port USB de 15 Go. Nous devons sélectionner la clé USB.

  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/96c5e38e23f3b15a261583cfc57f4492919b4dd30f36ae29dc1c8da46c77e90d7d204d55527c79f05e1e5924d13b.png)

Ensuite, nous serons invités à fournir des informations sur les éléments de preuve. C'est une bonne idée de suivre les principes de la chaîne de traçabilité et de l'ACPO. Toutefois, comme nous le faisons à titre d'exemple et qu'il ne s'agit pas d'une enquête d'application de la loi ou de réponse à un incident, nous pouvons laisser cette information vide et cliquer sur **Suivant**.

  

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

En consultant le KAPE dossier, vous trouverez deux fichiers exécutables, kape.exe et gkape.exe. Nous allons utiliser gkape.exe, qui est la version graphique de cet outil. Exécutons-le. Nous pouvons diviser l'interface en trois sections :

- **En haut à gauche —** Les cibles nous permettent de choisir exactement les informations que nous voulons récupérer du système cible, afin de pouvoir les obtenir le plus rapidement possible. Cela peut aller de la mémoire système aux données du navigateur Web.
- **En haut à droite :** les modules fournissent des fonctionnalités supplémentaires et permettent d'effectuer des opérations avec les données récupérées, telles que l'analyse des informations collectées à partir du système cible. Elles s'appuient sur les options Target et nous permettent d'affiner les informations que nous voulons collecter.
- **En bas :** la section Ligne de commande génère la requête qui est transmise KAPE pour exécution.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/8c3e09e8343034128158ebed1654453d17c06e49232cd7d98423acd6e5332fd9e2972bbd45b06ecc051b96c181e6.png)

Lorsque nous cochons la case pour activer les cibles en haut à gauche, nous devons d'abord fournir la source cible. Il s'agit généralement d'une image disque, mais pour cette procédure pas à pas, nous allons utiliser le lecteur C de notre système hôte.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/becab6a7e2586f4d056ec4a5027ea0341d2c99bd84d27ae9affb201287835584703e75e94a3f519c6a636a37fc4d.png)

Ensuite, nous devons définir un emplacement où les fichiers collectés KAPE seront enregistrés. Nous l'avons configuré dans un nouveau dossier dans nos Documents appelé KAPE Output.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/6df632c3be344227ebc38a11f14baea985d52bf8859dae448e388cb7e2fcc9b5e4c1ea291973e3c735426266df53.png)

Ensuite, nous pouvons sélectionner nos cibles. Pour le premier exemple, collectons des informations à partir des navigateurs Web les plus populaires : Chrome, Edge et Firefox. Nous pouvons faire défiler la zone Cibles vers le bas et les trouver.  

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/86fd20b0d23a3dce3f3740db925b46db879000e3e155198bf010166e2f791f873c58af3a3065856c0f800e79b90b.png)

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/853dee97f608ff6fd08c5ef69c95cb9a55b0f3b5df521b088e2190f4479347b0d57076e01c6af9be4610704c7442.png)

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/e152803c6ea10414967d0428713ab6dd7508dbe354b283a92f57f87f4fe3c9a6a1f2a6c915223b31a2d36ead21ca.png)

Une fois que nous avons sélectionné toutes nos cibles, nous pouvons cliquer sur le bouton Exécuter en bas à droite pour commencer KAPE .

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/ee74ebd5dc5ca5e5de11798fd64681e89ebff663892d77caaf994818fab10c5b1bbf694bb21112a146175f90ee8b.png)

KAPE va ouvrir un terminal et commencer à récupérer les copies des fichiers que nous avons demandés.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/7a4128714ec8bfe04c12aaab9fbc8be34c5f94c353514cb2626cbf7c0e67e85d9e3df9fc4e930b25700e30eccf7f.gif)

Voyons ce que nous KAPE avons trouvé en accédant au répertoire que nous avons défini comme destination cible plus tôt. Nous pouvons voir qu'il existe un certain nombre de journaux qui nous indiquent exactement ce qui KAPE s'est passé lors de l'acquisition. Nous avons également un dossier nommé « C » d'après le lecteur C de notre système hôte.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/7cbce1a9606ed0dfd1064e9043c31cbf45b6ab00db65b3608041f9361a02fb764b0bd82ca51142d9ef20bc510258.png)

Sur le chemin de fichier suivant, nous pouvons voir que vous avez KAPE trouvé des fichiers intéressants concernant l'activité menée à l'aide du navigateur Firefox sur ce système, y compris les cookies (qui peuvent nous indiquer les sites visités par l'utilisateur) et l'historique des formulaires qui peut inclure des informations personnelles telles que les adresses, les noms, la date de naissance, etc.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/e65860cf1997552f9ef6def5015e8808e7aa49dc5fa3b28e59b59308ab8e1f8ec08c6d532fae2f35234b73aa5f64.png)

Dans la capture d'écran ci-dessous, nous pouvons voir qu' KAPE elle a également récupéré des informations très utiles concernant Google Chrome.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/ba971f8b0c24834667dbeebef6a028b99c11f75f63cd418d1353bd0e1e1e5dc1e7a790639062701eba014ad81b10.png)

Enfin, nous avons certains fichiers provenant d'Internet Explorer/Edge tels que des caches Web.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/f984921f4546fedebab2395b78cdecdd80954bb7a563130f5a3061c30d22517db512ed960d9a2923f350f9f085ec.png)

---

