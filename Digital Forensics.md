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
