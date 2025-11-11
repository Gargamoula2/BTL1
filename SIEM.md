
# Windows Event Logs

Les « journaux d'événements Windows » ou « journaux d'événements » sont des fichiers au format binaire (avec l'extension .evtx) stockés localement dans le répertoire Windows d'un ordinateur doté du système d'exploitation correspondant :

- **Windows 2000 vers WinXP/Windows Server 2003** :  
    `%WinDir% \ system32 \ Config*.evt`
- **Windows Server 2008 à 2019 et Windows Vista à Win10 :  
    %WinDir%** `\ system32 \ WinEvt \ Logs*.evtx`

Ces journaux conservent un enregistrement détaillé de la grande majorité des événements survenus sur le système (événements matériels, connexions des utilisateurs, exécution et installation de programmes, etc.), ce qui permet aux administrateurs système de suivre tout ce qui se passe dans un système pendant son exécution et d'être en mesure de diagnostiquer et de prévoir les problèmes potentiels. Les catégories d'événements enregistrés incluent :

- **Application :** événements enregistrés par une application (exécution, erreur de déploiement, etc.)
- **Système :** événements enregistrés par le système d'exploitation (chargement de l'appareil, erreurs de démarrage, etc.)
- **Sécurité :** événements liés à la sécurité du système (connexions et déconnexions, suppression de fichiers, octroi d'autorisations d'administration, etc.)
- **Service d'annuaire :** il s'agit d'un enregistrement disponible uniquement pour les contrôleurs de domaine. Il stocke les événements Active Directory (AD).
- **Serveur DNS :** Il s'agit d'un enregistrement disponible uniquement pour les serveurs DNS ; les journaux du service DNS sont stockés.
- **Service de réplication de fichiers :** est un enregistrement disponible uniquement pour les contrôleurs de domaine ; il stocke les événements de réplication des contrôleurs de domaine.

Les journaux d'événements de sécurité sont des événements stockés par le système qui contiennent des informations relatives aux « politiques d'audit de sécurité de Windows » (éléments de surveillance systématique qui aident à évaluer la sécurité du système), qui sont utilisées pour permettre un contrôle précis de tout incident éventuel présent dans le système.  
Certains de ces éléments sont les suivants :

- Événements d'ouverture de session au compte (connexions et déconnexions valides et non valides)
- Gestion des comptes (création, modification, interaction et suppression de comptes utilisateurs)
- Utilisation des privilèges.
- Utilisation des ressources (création, modification, interaction et suppression de fichiers)

# Event Viewer

Sur Windows 10, nous pouvons afficher les événements Windows à l'aide du Event Viewer . Recherchez-le dans la barre de recherche de Windows et exécutez-le.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/dc11064b72bd13fb059c896891800c3a3788b36db13c616f49c6ea042b7d6a7fa9f706a3dc0eaf1736511115f120.png)

Nous pouvons utiliser ce programme pour consulter tous les types de journaux, et nous recommandons vivement aux étudiants de le consulter pour consulter les journaux sur leur propre système. Dans le cadre de cette procédure pas à pas, nous allons nous concentrer principalement sur les événements liés à la sécurité. Lors de l'ouverture, Event Viewer vous devriez voir un affichage similaire à la capture d'écran ci-dessous.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/33f99a1d9929baafcd679c589ba18f33714cd78db1685474df69de2567cfc00198212007e6956fd08eb32c6fff27.png)

Le résumé des événements administratifs au milieu de l'écran affiche un aperçu de haut niveau de tous les types d'événements survenus au cours des 7 derniers jours. Nous pouvons constater que nous n'avons eu aucun événement critique au cours des 7 derniers jours, 260 erreurs et 223 avertissements. Dans le volet de gauche, nous allons développer la section Windows Logs. Nous pouvons voir que cela est divisé en 5 sections différentes ;

- Demande
- Sécurité
- Configuration
- Système
- Événements transférés

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/3f50008a1bc507ba96e860e3143aa954bdf4e2959bcf7e31a10b78b204edf411d88378a704cd8c94f9cedd39e040.png)

Si nous cliquons sur Sécurité, le volet central affiche désormais les événements de sécurité. Dans la capture d'écran ci-dessous, nous pouvons voir de nombreux événements avec l'[ID d'événement 5379](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/event.aspx?eventid=5379) et la catégorie de tâches Gestion des comptes utilisateurs. Si nous double-cliquons sur l'un de ces événements ID 5379, nous pouvons obtenir plus d'informations, que nous aborderons ci-dessous.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/f63962a9a441fb3ab4ff052d3f8e53d4ec694066057ce49c8bb3a7f9dab4eab463e48d0544397b3cf599dc7ac777.png)![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/b457e4afe81c3e4f893254bf5f31d09a0f69967c38682b7b0dafbda10e9090eee7dbbd6c0445cecdf3e37a782614.png)

  
L'événement 5379 concerne les utilisateurs qui se connectent à un système Windows. Expliquons les informations contenues dans ce journal des événements :

- Les informations **d'identification du gestionnaire d'informations d'identification ont été lues :** lorsqu'un utilisateur soumet des informations d'identification lors de la connexion à Windows, le système lit les informations d'identification stockées dans le gestionnaire d'informations d'identification pour s'assurer que les informations d'identification fournies par l'utilisateur existent et, si elles sont valides, pour permettre aux utilisateurs de se connecter correctement.
- **ID de sécurité :** valeur d'identification de sécurité du compte lors de la tentative de connexion.
- **Nom du compte :** nom du compte.
- **Domaine du compte** : domaine auquel le compte essaie de se connecter. Comme il s'agit simplement d'un PC personnel connecté à un réseau domestique, le domaine par défaut est WORKGROUP.
- **ID de connexion :** il s'agit d'un numéro semi-unique (unique entre les redémarrages) qui identifie la session de connexion.
- **Opération de lecture :** énumérer les informations d'identification est l'action entreprise par le système, comme indiqué dans le premier point.

Dans la partie inférieure de la fenêtre, vous pouvez également voir l'heure à laquelle l'événement a été enregistré (18/06/2020 14:05:10), l'ordinateur sur lequel l'événement a été généré (DESTKOP-V9GVD5Q) et la réussite de l'audit, en fonction de la valeur du mot clé.

Dans la première capture d'écran ci-dessus montrant une liste d'événements de sécurité, en haut, nous pouvons voir certains événements de connexion et des événements d'ouverture de session spéciaux. Examinons-les de plus près.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/7426bb966b2aae84a611177275a5e74c1e63fce0251bccb539956883c3be46728f74b4bdd992181cae6e271fc641.png)

Dans la capture d'écran ci-dessus, nous pouvons voir les événements portant les ID [4672 Special Logon et](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/event.aspx?eventid=4672) [4624](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/event.aspx?eventid=4624) Logon. Ce volet affiche les événements avec le plus récent en haut. La séquence actuelle est donc la suivante : Ouverture de session > Ouverture de session spéciale. Mais qu'est-ce que cela signifie réellement ? L'événement d'ouverture de session se produit chaque fois qu'un utilisateur se connecte au système, et l'ouverture de session spéciale se produit lorsqu'un administrateur se connecte. Nous pouvons voir qu'ils sont couplés, car lorsqu'un compte utilisateur disposant de privilèges d'administrateur se connecte à Windows, il nécessite l'événement Logon, puis l'événement Special Logon. Vous trouverez ci-dessous des captures d'écran de ces deux types d'événements développés dans Event Viewer .

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/323d06552345d0c98de0ee91a88c241faca29df07fd1ed0c4217364071ddf949b6c3ec0d9cdeec527c27aa3ac854.png)_Événement d'ouverture de session utilisateur standard_

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/07ffc46e673ddfd620032cda1fb0ad3526d94e65b2f76768f920463ff505a64f39f6da88ea83d1e8017cec97c53a.png)

_Événement spécial d'ouverture de session utilisateur_

  
**Pourquoi pensez-vous que c'est une bonne idée que les équipes de sécurité surveillent les connexions des utilisateurs et les ouvertures de session spéciales ?** (Pensez-y vraiment pendant une minute avant de continuer à lire !).

- La plupart des employés travailleront de 9 h à 17 h dans les organisations basées sur des bureaux. Nous pourrions surveiller les activités de connexion à des heures inhabituelles, par exemple en générant une alerte pour un compte qui se connecte à 3 heures du matin, alors que l'utilisateur n'est censé travailler que de 9 heures à 17 heures. Cela peut être le signe d'une compromission du compte ou d'une menace interne.
- Les comptes dotés de privilèges administratifs peuvent effectuer bien plus de tâches que les utilisateurs standard. Nous devons surveiller de près ces comptes, car s'ils sont compromis, les attaquants vont passer un bon moment. Cette surveillance peut également alerter l'équipe de sécurité de la présence de menaces internes qui souhaitent abuser de leurs comptes d'administrateur pour causer des dommages ou effectuer d'autres actions malveillantes.

---

# Affichages personnalisés

Event Viewer nous permet de créer des profils de recherche personnalisés, appelés « Vues personnalisées ». Nous pouvons facilement les utiliser pour récupérer les identifiants d'événements souhaités dans un système, en supprimant ainsi tout le bruit supplémentaire qui ne nous intéresse pas. Ci-dessous, nous allons vous expliquer comment créer une vue personnalisée pour ne rechercher que les activités d'ouverture et de fermeture de session. Tout d'abord, ouvrez Event Viewer et cliquez sur Vues personnalisées sur le côté gauche.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/8c8be5b8581ce8674577184c8b1fe79bc965c9c5fed5430f81325465d0bafedbcfbb71a125d9110951977279877c.png)

Nous pouvons voir dans la capture d'écran ci-dessus qu'il existe déjà par défaut une vue personnalisée, nommée « Événements administratifs ». Sur le côté droit, nous pouvons cliquer sur « Créer une vue personnalisée » pour créer notre propre filtre. La fenêtre ci-dessous apparaîtra, nous permettant de créer la vue. Ci-dessous, nous allons couvrir toutes les propriétés que nous pouvons définir.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/86c9164eb9f0b9ebb53bc2eb3f43593ad94d251c5f25ad7db25a39209976c9cdc2c8457fd5126c5c6c7646b18296.png)

- **Enregistré :** nous permet de définir une plage de dates à partir de laquelle récupérer les journaux. Nous pouvons définir une plage personnalisée ou utiliser les préréglages tels que « À tout moment », « Dernière heure », « 12 dernières heures », « Dernières 24 heures » et « 7 derniers jours ». Cela peut être utile si un système n'est pas connecté à un SIEM, car cela nous permet de récupérer des journaux d'événements spécifiques après une infection par un logiciel malveillant ou un incident de sécurité.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/cbb953a59101485834518c721915353b4ceb6aa5123169124b26910fd2621f54d5169ea1c5aa9396f682425d3148.png)

- **Niveau d'événement :** nous permet de sélectionner les niveaux d'événements sur lesquels nous voulons filtrer, ce qui nous fournira différents événements en fonction des niveaux sélectionnés.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/e22d405154166390f45b0bfff95461bdd149c5590f2433e38a709e6a03fd8964b83ef1d4ef103441a69af6ba9ebe.png)

- **Par journal :** nous pouvons choisir les journaux que nous voulons filtrer. La capture d'écran ci-dessous montre une structure hiérarchique dans laquelle nous pouvons sélectionner des journaux à n'importe quel niveau. Dans l'exemple de capture d'écran ci-dessous, nous recherchons uniquement les journaux d'événements relatifs à la sécurité et aux systèmes provenant de Windows.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/59d8ec9d907ae18791e9512de0d01d00aaddf88802890ba4056f8acf73a9fa7c3f8e794db1f088e8305156923a2e.png)

- Par source : si nous ne voulons pas sélectionner de groupes de journaux, nous pouvons choisir des sources. Il s'agit de domaines spécifiques du système d'exploitation et des applications. Consultez la capture d'écran ci-dessous pour quelques exemples de sources parmi lesquelles nous pouvons choisir.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/3ae54e7fbdf856bdcd8014105698852c7d09ed7f8c3511bbc26290fd2116cd7b58a2f5dde4126eae2b7877983a70.png)  

- **Inclut ou exclut les identifiants d'événements :** cette section nous permet de définir exactement les identifiants d'événements que nous voulons capturer. `**Nous pouvons saisir tous les ID d'événement que nous voulons récupérer en les listant, en utilisant une virgule comme séparateur, par exemple : 56 991 411 3314**`

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/13f6571442501090d0d05bbd6cf0b3987ce023f224d737b3c758036870f69cc249222c40cf57c9a3ce10d27a9cde.png)

- **Mots clés :** nous pouvons rechercher des mots clés spécifiques dans les événements. Consultez la capture d'écran ci-dessous pour découvrir les options que nous pouvons choisir.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/5ac11b7de15676c7a5e43808eff6d4cb748781e61e2f71d6b5d6bb8bbc20a8c1adf8c3130d0617b277b8f6adcaf4.png)

- Utilisateurs et ordinateurs : cette section nous permet de nous concentrer sur des utilisateurs ou des systèmes spécifiques, si d'autres systèmes Windows transmettent leurs journaux d'événements au système Event Viewer sur lequel nous les consultons. S'il y avait un utilisateur nommé « KellyP » et que nous voulions uniquement enquêter sur les événements qui lui sont liés, nous utiliserions son nom de compte utilisateur dans le champ Utilisateur.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/02427364b3d37bc4f8877ee057210d423ebbeb7ee62ad6257c553c0f87c7d1d63f9141b2a334c25e44b5b0b5a5c7.png)

## **Exemple de vues personnalisées : surveillance des connexions**

Pour que vous compreniez parfaitement comment les vues personnalisées peuvent être utilisées, prenons un exemple dans lequel nous souhaitons surveiller les heures de connexion et de fermeture de session des employés. Les événements suivants doivent être pris en compte pour notre point de vue :

- Ouverture de **session utilisateur réussie — 4624**
- Ouverture de **session spéciale — 4672**
- **Déconnexion initiée par l'utilisateur — 4647**
- **Déconnexion utilisateur — 4634**

Dans la capture d'écran ci-dessous, vous pouvez voir les paramètres que nous avons définis. Nous voulons voir tous les événements associés aux connexions et aux déconnexions des utilisateurs au cours des dernières 24 heures.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/73c25d8717f1645071b7e1cf7a48e2361031b41d8e716b3c9be1dba69c2993825bf178ef827effbd3cf2c498dc31.png)

Nous serons ensuite invités à fournir un nom, une description et l'endroit où nous voulons enregistrer la vue.

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/4fffaa5be1d6d8e6dbf8127e26e99a5b42d9d144caa604d165328dd1a938941bcbdd3770286734bd0ed9881e72f5.png)

À présent, le filtre affiche uniquement les identifiants d'événements que nous avons définis. Ça a marché ! Nous pouvons désormais voir les événements liés à la connexion et à la déconnexion des comptes utilisateurs !

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/bde7b3cdbec0d4e79ac9e1db069b07123ace74a4290f6d425948006da13cef3bdd9e994ac80f0f57514ab4a4f492.png)

**Travaux pratiques pour Event Viewer**

**Question 1 - À quelle heure a lieu le premier événement d'ouverture de session spéciale ?**

L'une des approches pour répondre à cette question consiste à filtrer les journaux en fonction de la date et de l'heure auxquelles ils se sont produits. Par défaut, les événements les plus récents s' Event Viewer affichent en haut. Ainsi, si nous cliquons une fois avec le bouton gauche de la souris sur la colonne Date et heure, les journaux les plus anciens apparaîtront en premier. De là, nous pouvons voir que le premier journal enregistré est un identifiant spécial 4672. Nous pouvons prendre la date du journal et nous assurer qu'elle correspond au format attendu.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/1b9aa3ce831327c778093eb51df3d41a2d88883b8e2940199cd8d86f3db44707595989aa7f346fbd67e76c1dceeb.png)

Par ailleurs, lorsque nous envisageons une exportation beaucoup plus importante des journaux d'événements (étant donné que cette capture ne contient que 11 journaux), nous pouvons utiliser un filtre pour examiner uniquement les identifiants d'événements spécifiques, qui dans ce cas seraient 4672. Pour ce faire, cliquez sur « Filtrer le journal actuel... » dans le panneau de droite de. Event Viewer Nous avons ajouté 4672 dans la zone de saisie à mi-chemin de la fenêtre contextuelle, et après avoir cliqué sur « OK », nous verrons nos résultats.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/869946d746fc864a33dd76c7cdb7d78797ffb72709e82892e0b4d3328bfb01df9889ceabb1217e389639bc1600b4.png)

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/f190a847ee8084deb853c23f5f46356d94cd1786b434a6ab1d871ac17a8b22b9f70269b7f522241a9d50e1ee32d7.png)

---

**Question 2 - À quelle heure Jeff crée-t-il un autre compte utilisateur ?**

En suivant la chaîne chronologique des événements, nous pouvons voir un événement de « gestion des comptes utilisateurs » (4720). Dans les détails du journal, nous pouvons voir la personne qui a effectué l'action (Jeff, le sujet) et le nouveau compte créé, StevEE. Nous pouvons prendre la date du journal et nous assurer qu'elle correspond au format attendu.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/0019ef65603ddc2dd23ee0a34549685fe9d6abc805ccfc72a71f38e093124466a2a9770460c1415c0af3691391e4.png)

Nous pourrions également créer un nouveau filtre pour rechercher 4720 identifiants d'événements.

---

**Question 3 - Quel est le nom du nouveau compte ?**

Nous avons déjà récupéré le nom du nouvel utilisateur dans la question précédente !

---

**Question 4 - Quel est l'identifiant d'événement Windows utilisé pour la création du nouveau compte utilisateur ?**

Sur la base des deux questions précédentes, l'ID d'événement 4720 est utilisé pour la création de nouveaux utilisateurs.

---

**Question 5 - Quels sont les noms des trois groupes d'utilisateurs auxquels appartient le nouveau compte, classés par ordre alphabétique ?**

Lorsque des utilisateurs sont ajoutés à des groupes de sécurité Windows, 4732 ID d'événement sont générés (Gestion des groupes de sécurité). En parcourant les détails du journal, nous pouvons voir le groupe auquel le compte cible a été ajouté. Dans le premier cas, le compte est ajouté au groupe par défaut « Utilisateurs ».
**A noter que pour savoir qui fait quoi a qui, il faut regarder les ID, l'un a 1003 et l'autre 1004, pas forcement se fier au Account Name qui peut ne pas être présent.**

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/a82f7614208ab66bf55c00ac7b716e4be46993a19e589d7fcf7997618ec2e90099c7d24ac625b52cf80607af667f.png)

Dans le second cas, le compte est ajouté au groupe ServiceAccount.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/a40a03e975f937d019be485d252800d4ece7e360b61a97bdd89eb37b263e885757c71dca28a0bf2a2063a7e7c5bb.png)

Et dans le troisième cas, le compte est ajouté au groupe des administrateurs.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/4a44256a0616224de807e43fc75ea29ecccbca6cb01abb4703122f5324ad2d99bfe6dbe57710a983f5ff130b30b6.png)

---

**Question 6 - À quelle heure le nouveau compte utilisateur se connecte-t-il ?**

Pour trouver la réponse à cette question, nous pouvons créer un nouveau filtre pour les ID d'événement 4624 (logo normal) et 4672 (ouverture de session spéciale). En parcourant ces événements, nous pouvons trouver une connexion spéciale impliquant le nouveau compte, StevEE. N'oubliez pas qu'il s'agit d'une connexion spéciale et non d'une connexion standard, car ce compte appartient au groupe local des administrateurs.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/05624d909432098bedec743601f6f9bd0d51e9ef9d19658300922df7c816dd115106aea38786255f93e66f238dbb.png)

# Sigma

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/d97132c3bbe6159245a025b0212ac1cc8ffcce7bc16330d3c0fa40dfff2d59fd4c0ac724f92642752d2ff54fcda7.png)

1. `title` est une valeur descriptive personnalisée qui est utilisée pour fournir une très brève explication de ce que la règle recherche.
2. `id` est utilisé comme identifiant unique pour cette règle.
3. `status` est une valeur descriptive personnalisée utilisée pour expliquer l'état de la règle. Certains exemples peuvent inclure « incomplet », « expérimental » ou « production ».
4. `la description` est une valeur descriptive personnalisée utilisée pour fournir une explication plus détaillée de ce que la règle essaie de détecter et de quelle manière.
5. Voir ci-dessus.
6. `author` est une valeur personnalisée utilisée pour contenir le ou les auteurs de cette règle SIGMA.
7. `date` est une valeur personnalisée utilisée pour contenir la date à laquelle la règle a été créée pour la première fois.
8. `modified` est une valeur personnalisée utilisée pour contenir la date à laquelle la règle a été modifiée pour la dernière fois par un auteur.
9. `les références` sont une liste personnalisée qui contient des URL qui aident à expliquer ce que la règle essaie de détecter
10. voir ci-dessus (9)
11. voir ci-dessus (9)
12. `logsource` est utilisé pour expliquer quels journaux sont requis dans le SIEM pour que la règle fonctionne
13. la `catégorie logsource` est dns, ce qui montre que l'équipe de sécurité devra extraire les journaux DNS dans son SIEM pour que la règle fonctionne
14. La `détection` explique la logique qui sous-tend la règle, y compris les conditions qui, lorsqu'elles sont remplies, peuvent générer une alerte.
15. `La sélection` indique que quelque chose doit être sélectionné dans les journaux DNS. Dans ce cas, il s'agit du domaine parent (ou du domaine racine, tel que Google.com).
16. `parent_domain` indique le champ de journal qui doit être sélectionné. Le symbole astérisque * représente un « caractère générique », ce qui signifie que n'importe quelle valeur peut être utilisée. Cela signifie que N'IMPORTE QUEL domaine doit être sélectionné.
17. la `condition` indique la logique de détection réelle. Pour cette règle, il récupérera toutes les valeurs parent_domain et comptera le nombre de requêtes adressées à ce domaine. Si le nombre est supérieur à 1 000 (> 1 000 signifie supérieur à 1 000), il émettra une alerte.
18. les `faux positifs` sont une liste personnalisée qui indique comment les faux positifs peuvent se produire.
19. `faux positifs 2` — L'auteur explique qu'un logiciel légitime qui utilise le DNS pour transférer des données générerait une alerte, même s'il ne s'agit pas d'une activité malveillante.
20. `level` est une valeur descriptive personnalisée qui, dans cette règle, semble indiquer le degré d'urgence de cette alerte.
21. les `tags` sont une liste personnalisée qui inclut différentes techniques MITRE ATT&CK qui peuvent être détectées à l'aide de cette règle.

Nous savons donc que cette règle est utilisée pour détecter un éventuel [tunneling DNS](https://attack.mitre.org/techniques/T1071/004/) à des fins de communication de commande et de contrôle en recherchant un grand nombre de requêtes adressées à des domaines, et qu'elle émet une alerte lorsque 1001 demandes ou plus ont été observées en consultant les journaux DNS.

C'est maintenant à vous d'apporter des modifications qui nous permettront de détecter certaines activités spécifiques. Lisez le briefing de renseignement ci-dessous et essayez d'apporter des modifications à ce fichier de règles existant afin de refléter les informations fournies.