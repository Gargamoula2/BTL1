 [ID d'événement du journal de sécurité Windows 4625](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/event.aspx?eventID=4625#fields), se trouve un champ réservé aux « informations d'échec » qui contiendra l'un des codes suivants :

  
![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/e5e72a49050655d9f7a71a23b2fe6689caf91362ff4b9cf229a5109940943605b44c893d05f5fdc8d7a53971d6a5.png)

 Les échecs de connexion lorsque le nom d'utilisateur n'est pas reconnu (0xC0000064) ou que le compte est verrouillé en raison d'un trop grand nombre d'échecs de connexion (0xC00000234) peuvent être le signe qu'un attaquant tente d'accéder à des comptes internes en bruteforce, indiquant ainsi qu'un système interne a été compromis.

---

**Question 1 (Processus) Pour exporter la liste des processus en cours d'exécution à partir d'une invite de commandes vers un fichier texte, ouvrez une session cmd sur le bureau (ou accédez au bureau à l'aide de « cd Desktop ») et exécutez « tasklist > tasklist.txt ». Ouvrez-le dans Sublime Text et utilisez la fonction Rechercher dans le menu supérieur pour rechercher des instances de cmd.exe. Combien y en a-t-il au total ?**

Après avoir déplacé la session CMD vers notre bureau (cd Desktop) et exécuté la commande indiquée (tasklist > tasklist.txt), nous allons cliquer avec le bouton droit sur le fichier texte créé, ouvrir avec et sélectionner Sublime Text.

En utilisant CTRL+F et en recherchant « cmd.exe », vous obtenez 4 résultats (techniquement, l'un d'entre eux est le nôtre, que nous avons utilisé pour obtenir une liste des processus en cours d'exécution, donc 3 ou 4 est la bonne réponse).

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/6ac46a64bd96972f91c4f3d9d69939f53e7ba6eac095bf1b81a106820feb6895ef1f57f0774fc8f453625513c44f.PNG)

**Question 2 (Utilisateurs) Combien de comptes au total sont présents sur le système ?**

À l'aide de la commande `**net users**`, nous pouvons obtenir une liste de tous les utilisateurs locaux du système.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/aedf6563509ea465aeaca00b32d501b6954eac2424325cab2ab5ec51d0b5479760d313a3b356267a8d37c5027fd5.PNG)

**Question 3 (Utilisateurs) Combien de ces comptes se trouvent dans le groupe local des administrateurs ?**

À l'aide de la commande `**net localgroup**` administrator, nous pouvons répertorier tous les comptes locaux dotés de privilèges administratifs.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/0a3d8ac3a769926a8717f06e179aa1efc2bc09ea5500b82854ee92e935333f56b945c9f492777cf110c1755faf93.PNG)

**Question 4 (Utilisateurs) Quel est le nom du compte administrateur suspect ?**

En regardant la capture d'écran ci-dessus, nous pouvons voir qu'il existe un compte nommé « ServiceeAccount », qui semble essayer d'imiter un compte qui pourrait exister sur le système à des fins légitimes.

**Question 5 (Utilisateurs) Quels sont les noms des comptes locaux qui peuvent se connecter au système via le protocole RDP ? (Listez-les par ordre alphabétique)**

À l'aide de la commande net localgroup « Remote Desktop Users », nous pouvons constater qu'un seul compte est capable d'utiliser le protocole RDP, le compte suspect de la question précédente.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/161c5b92c2a84c60b6dc16cfc8f65f670509bd0011a82ca72b564f5bb34dc8569d30965e2459db484f697d495a84.PNG)

**Question 6 ( PowerShell Utilisateurs) Exécutez la commande pour obtenir des informations détaillées sur le compte suspect identifié précédemment. Quand s'est-il connecté pour la dernière fois ?**

À l'aide de la commande `**Get-LocalUser -Name ServiceeAccount | Select***`, nous pouvons récupérer toutes les propriétés relatives à ce compte local. Surligné, nous pouvons voir l'horodatage de la dernière connexion.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/86257b82d51145b40ef82499a6ffc6b88665dc3bcb6e832dda6dd2966d557c2b2f2373952e85664329dc570d0240.PNG)

**Question 7 ( PowerShell Services) Exécutez la commande pour répertorier les services du système. Quel est le nom d'affichage du service commençant par « Amazon » ?**

L'exécution de la commande Get-Service | Where Status -eq « Running » | Out-GridView ouvrira une nouvelle fenêtre. À partir de là, nous pouvons voir que le service que nous avons été invités à trouver se trouve en haut de la liste alphabétique.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/b03b663971c5dbc2eb64f3f4ada3302dd0c88260e679cc14c0d50280ff59849a0c096c6a0cf91bd9d55d4047f2be.PNG)

**Question 8 (Tâches PowerShell planifiées) Obtenez la liste de toutes les tâches planifiées. Quel est le nom de tâche de l'entrée commençant par « P » qui est en état Prêt ?**

À l'aide de la commande `**Get-ScheduledTask | Where State -eq « Ready »**`, nous ne pouvons voir que les tâches planifiées qui se trouvent dans l'état que nous recherchons. Le premier élément affiché correspond à la tâche que nous recherchons.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/39ea31b38b6bdfd59caf37dad59cd8b0f1f660433f8a0f781d71075a2cfaf1572abb5d7266ababc1a9d22fe51bd4.PNG)

**Question 9 (Tâches PowerShell planifiées) Exécutez la commande « Get-ScheduledTask -TaskName 'TaskNameFromLastQuestionHere' | Sélectionnez * ». Regardez la propriété Triggers, de quoi s'agit-il ?**

En exécutant la commande fournie, nous pouvons voir que la propriété Trigger est définie sur lorsqu'un utilisateur se connecte au système.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/4a9bb802f2b078938f66b54e0d4d8166970812008769d69c15f3a1fc73c943bb55df959259d2ea8d1e30be12dddf.PNG)

---

# The Hive

**Question 1) Combien de cas ont été enregistrés au sein de TheHive ?**

Sur la page Cas, nous pouvons voir que 6 cas sont présents sur la plateforme.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/9e4d2830f596e003190d2557b579962bd5c24cc95ce72965028f44301978b4a5e545b551b7a2a0dd1f9d310dd008.png)

---

**Question 2) Combien de dossiers sont ouverts et combien sont fermés ?**

Il existe plusieurs façons d'obtenir cette réponse. L'une d'elles consiste à cliquer sur Filtres rapides, qui nous donne le nombre d'ouvertures et de fermetures.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/cf531d557269ba0c908d8ea66721f8fc79f0ed84d6b88353a4b5d094f9f6298325dc583c8abdad6a8af4afe81715.png)

---

**Question 3) Enquêtez sur le cas #5. Quels tags ont été attribués à ce dossier ?**

Dans la liste de tous les cas, nous pouvons voir que la deuxième colonne a pour titre « #NUMBER ». Nous allons donc cliquer sur le titre du cas #5.

Dans l'onglet Général, nous pouvons voir que deux balises sont appliquées, « hameçonnage » et « e-mail ».

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/194185c4df5edc6e648b3f63adc8668b2b1602bd6ce2c7c5a6c286c4c27008592e2336f0aa5c24b99b539a603f02.png)

---

**Question 4) Examinez la tâche liée à la prise de mesures défensives. Combien de blocages ont été demandés/réalisés ?**

En accédant à l'onglet Tâches et en cliquant sur la tâche « Prendre des mesures défensives », nous pouvons constater que l'analyste a demandé/réalisé deux blocs, un bloc de courrier électronique et un bloc Web.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/55aea566d10d8015f77cdc51d5e018f2fee7c8d2cde9490a3103ca91be9aa3ea194a7e0be339862542173d734d7a.png)

---

**Question 5) Combien d'observables ont été créés pour ce cas ?**

À partir du nom de l'onglet Observables, nous pouvons déjà voir qu'il y a (8). Si nous cliquons sur l'onglet, nous pouvons également les compter nous-mêmes.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/15b92fb27692ae843dd548345bdc00d2260b1386071b0e816a36907bc95236bb00cdb91b9711641db9630979cde3.png)

---

**Question 6) Il existe un observable avec le type de données « ip » qui commence par 54. À quoi est liée cette adresse IP ?**

En cliquant sur le type de données IP observable pour 54.240.48.89, nous pouvons lire la description et voir qu'il s'agit d'une « adresse IP du serveur d'envoi ».

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/85f0c27217f56e8e8affcf7559d1b12868f49be7bb55f2fb4b5cb89080a320c5b2ebf53742040d1d6e2e9cc131f9.png)

---

**Question 7) Quelle est la taille de la pièce jointe à l'intérieur du boîtier ?**

En accédant à l'onglet Pièces jointes, nous pouvons voir que dans la colonne TAILLE, il y a une valeur de 24,66 Ko.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/c5793f03c710acc0e458e09bce480bfc4a2bccb248fa63dfb2dcfb17407f5c10f4d6fb0902c6451311acf56de338.png)

---

**Question 8) Cette affaire a été classée. Quel était le statut et y a-t-il eu un impact ?**

En regardant la colonne de gauche contenant les propriétés du dossier, nous pouvons voir que le statut est TruePositive et que l'impact est Non.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/0e44149d67f2c10ddcae0bbddb3aa933078f95f1799a387ee02f6208ccf83cf400be2d0153f61ba74a7368a1f811.png)

---

**Question 9) Il manque quelque chose d'important dans le cas #4. Dans quel onglet il manque ces informations importantes ?**

Après avoir parcouru les onglets que nous avons appris à utiliser (propriétés du dossier, colonne de gauche, Général, Tâches, Observables, Pièces jointes, Commentaires), nous pouvons voir que ce dossier fait référence à un fichier, mais qu'il n'y a pas de pièces jointes ! Il est important de s'assurer que les fichiers sont joints.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/eb60b1fd201deac5a63acce505cde03b0aa45f86190a03b14f0beaceae44f4c022ca1811cc23377a1cbe19c128c5.png)

---

**Question 10) Quel est le nom du membre de l'équipe de réponse aux incidents de sécurité qui a participé à cette affaire ?**

Pour comprendre le cas, nous voulons lire les tâches pour voir ce qui se passe. Nous pouvons en déduire que Jason Smith du SIRT a été invité à apporter son aide.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/60a4e563744af871cb84d3611dffb7f5ac0a34cf13d3deb408cdbd69027c4f63d04a2afd817046c2fab32f0ea7a0.png)

---

**Question 11) Combien de tâches ont été marquées comme terminées ?**

Il existe plusieurs façons d'obtenir cette valeur, mais nous allons cliquer sur Filtres rapides, puis sur Tâches terminées, où nous pouvons voir qu'il y a 14 résultats.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/5f1dcfdd7cbc78024a30cf02e1e2aeb5af648aa631c151d87d24ca34ae1c83155157f4d1660793df9fab9547b1fc.png)

---

**Question 12) Combien de tâches ont le statut En attente ?**

Nous allons effectuer les mêmes actions que pour Q11, mais nous allons plutôt sélectionner « En attente » dans les filtres rapides. Il y a 9 tâches en attente.

---

**Question 13) En examinant le tableau de bord des opérations, combien de cas présentent une gravité faible, moyenne ou critique ?**

Pour accéder à la page Tableaux de bord, nous cliquons sur Tableau de bord opérationnel. Dans le graphique en anneau de droite (Gravité des cas), nous pouvons voir qu'il y a 2, 3, 1 cas de gravité faible, moyenne et critique.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/be2339f78e35c3c7a18a781606258fd0b8a43db2fb44179323828a6a3b1ae5f47601e50075b6361f5c7751ad74c9.png)

---

**Question 14) Combien de modèles de cas peuvent être utilisés par l'équipe ?**

En regardant le graphique du tableau de bord central, nous pouvons voir qu'il existe actuellement 5 modèles de cas différents prêts à être utilisés par les analystes.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/06f374606933d729df52db2175420ffd4ecaa537e89173a55e02731ae755c059be999da7330fa63c2150279424a9.png)

---

**Question 15) Revenez à la section Dossiers et ouvrez #4. Regardez la colonne de gauche du dossier et remarquez l'icône rouge « 1 » en bas à gauche, intitulée « Affaires connexes ». Cliquez sur ce bouton. Quel est le titre du dossier concerné ?**

Accédez à la page Cas, puis sélectionnez le cas #4. En bas de la colonne de gauche, vous pouvez voir ce qui suit :

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/6cd63cd8bbbd8732794414402e9df7c95fbed8f7714098f20d6b8c3cdf2911d040b04a5cac130f68bc7ca4f2a6f8.png)

Cliquez sur cette icône pour modifier le panneau central afin d'afficher le cas associé et la façon dont il est lié.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/93e54b776704c74761031569e5c600be3f179d41079533547d5d67557eee54a5a37efd8be1e843df606e2cd7d0e4.png)

---

**Question 16) Quel est l'un des deux observables liés communs à ces deux cas ?**

Nous pouvons voir les deux observables liés dans la colonne de droite. Soumettez l'une ou l'autre de ces options.

![](https://d2y9h8w1ydnujs.cloudfront.net/uploads/content/images/93e54b776704c74761031569e5c600be3f179d41079533547d5d67557eee54a5a37efd8be1e843df606e2cd7d0e4.png)

---
