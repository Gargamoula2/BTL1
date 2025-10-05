[[BTL1]]

| Logiciels           | Utilité                                                                 | Liens                                                           |
| ------------------- | ----------------------------------------------------------------------- | --------------------------------------------------------------- |
| VIRUS Total         | Scan un fichier pour vérifier sa dangerosité                            | https://www.virustotal.com/gui/home/upload                      |
| URL2PNG             | Permet de visualiser le site sans cliquer dessus                        | https://www.url2png.com/                                        |
| Wanna Brower        | Récupère le code HTML d'une page web et condense des infos utiles       | https://www.wannabrowser.net/                                   |
| PhishTool           | Permet de fournir un rapport type LaTex. Traite intelligement un mail   |                                                                 |
| Who Is Domain Tools | Recherche DNS inversée                                                  | [https://whois.domaintools.com](https://whois.domaintools.com/) |
| Talos               | Réputation du fichier via le hash                                       | https://www.talosintelligence.com/talos_file_reputation         |
| CyberChef           | Outil pour appliquer différents algorithmes sur une chaine de caractère | https://gchq.github.io/CyberChef/                               |

**Artéfacts à récupérer :**

|                                                      |                                    |                                                                                                                                 |
| ---------------------------------------------------- | ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| X-Sender-IP (Si introuvable, penser à "*Received:*") | IP du serveur envoyeur du mail     |                                                                                                                                 |
| From                                                 | Adresse -mail qui a envoyé le mail | From: auto-confirm.info-amazon.co.uk < QPE77765@mun.ca ><br>La première partie n'a aucune valeur, la vraie adresse est entre <> |
| Date                                                 | Date d'envoie du mail              |                                                                                                                                 |
| Subject                                              | Objet du mail                      |                                                                                                                                 |
| To                                                   | Destinataires                      |                                                                                                                                 |
| filename                                             | Concerne les pièces jointes        |                                                                                                                                 |
| Return-Path/Reply-to/In-Reply-To                     | Serveurs d'envoi                   |                                                                                                                                 |
![[Pasted image 20250925132202.png]]
![[Pasted image 20250925133002.png]]
**Récupérer le HASH d'un fichier :**

Windows : Get-FileHash FICHIER -algorithm md5/sha256
Linux : sha256sum FICHIER


Les liens cliquables en HTML sont représentés par des balise <"a">
Vérifier SPF/DKIM/DMARC



 **1) Récupérez l'original de l'e-mail suspect :**

Une version originale de l'e-mail peut être obtenue de différentes manières, par exemple en utilisant la technologie de sécurité de la passerelle de messagerie ou de la passerelle elle-même, en extrayant le courrier directement depuis la solution de messagerie, comme les serveurs Microsoft Exchange, ou en demandant à un employé de transférer l'e-mail vers une boîte aux lettres sécurisée.

 **2) Rassemblez des artefacts à partir de l'e-mail d'origine :**

Nous avons déjà décrit les artefacts que nous devons collecter et pourquoi ils sont importants. Ils sont utilisés plus tard dans le processus d'enquête pour effectuer une analyse des artefacts et prendre des mesures défensives.

**3) Informez les destinataires des e-mails :**

Un élément crucial de la réponse immédiate à une attaque de phishing consiste à informer toutes les personnes qui ont reçu l'e-mail. Cela permet de réduire le risque qu'ils ouvrent l'e-mail et interagissent avec celui-ci.

Généralement, les organisations disposent d'un modèle d'e-mail qu'elles peuvent envoyer aux destinataires une fois qu'ils ont été identifiés. L'analyste chargé de l'enquête vérifierait sur la passerelle de messagerie les boîtes aux lettres auxquelles l'e-mail de phishing a été envoyé, puis ajouterait les destinataires dans le BCC du modèle d'e-mail, en incluant les informations suivantes :

- **La date et l'heure d'envoi de l'e-mail** (permet aux destinataires de trouver l'e-mail plus facilement en consultant l'heure des e-mails qu'ils ont reçus)
- **L'objet de l'e-mail malveillant** (permet aux destinataires de trouver l'e-mail plus facilement en consultant la ligne d'objet des e-mails qu'ils ont reçus)
- **Des instructions claires sur la marche à suivre avec l'e-mail** (cela dépendra de la manière dont l'organisation traite les e-mails de phishing). Il peut s'agir de demander aux destinataires de supprimer l'e-mail ou de le transférer vers une boîte aux lettres sécurisée.)
- **Coordonnées à utiliser si le destinataire ne sait pas quoi faire** (généralement, une boîte aux lettres sécurisée, permettant à l'utilisateur de bénéficier de l'assistance de l'équipe de sécurité)

**4) Analyse et investigation des artefacts :**

Nous avons déjà expliqué comment examiner les artefacts liés au courrier électronique, au Web et aux fichiers afin de collecter davantage d'informations et de déterminer leur degré de malveillance. Les outils à utiliser incluent le sandboxing de niveau entreprise, URL2PNG VirusTotal , IPVoid WannaBrowser , une machine virtuelle, etc.

 **5) Prenez des mesures défensives :**

Les mesures défensives sont les mesures prises par l'équipe de sécurité pour réduire le risque généré par l'attaque de phishing. Cela inclut potentiellement le blocage des e-mails, du Web et des artefacts basés sur des fichiers. Si un e-mail malveillant inclut une URL redirigeant l'utilisateur vers un outil de collecte d'informations d'identification, le blocage de cette URL sur un proxy Web empêcherait les employés de se connecter à la page Web, réduisant ainsi totalement le risque qu'ils saisissent leurs informations d'identification. Nous aborderons le blocage des e-mails, du Web et des artefacts basés sur des fichiers dans les trois prochaines leçons.

**6) Rapport d'enquête complet :**

Nous aborderons cela en détail dans une section ultérieure. Votre rapport d'enquête contiendra des notes sur toutes les étapes que vous avez effectuées au cours du processus de réponse immédiate. Cela fournit une piste d'audit pour montrer que le courrier électronique a été identifié, étudié et que des mesures défensives ont été prises pour protéger l'organisation contre cette attaque.

---
**Un rapport d'incident doit comprendre :**
- Détails de l'en-tête de l'e-mail, artefacts collectés et description du contenu du corps du message
- Utilisateurs concernés et mesures prises pour les informer
- Processus d'analyse, outils utilisés et résultats
- Mesures défensives prises
- Leçons apprises

**En détail :
- **Adresse e-mail expéditeur** (ex : J0hnSm1th@gmail.com)
- **Réponse à** (ex: J0hnSm1th@gmail.com ou rien)
- **Adresse de réponse** (ex : F4keacc0unt2421@gmail.com)
- **Date d'envoi** (ex : 20 octobre 2019, 9h34)
- **IP du serveur d'envoi** (Ex : 40.92.10.10)
- **DNS inversé de l'adresse IP du serveur d'envoi** (ex : mail-oln040092010100.outbound.protection.outlook.com)
- **Destinataire (s)** (Ex : jason.s@domain.com, kirsty.p@domain.com, brian.b@domain.com)
- **Objet du message** (ex : Mise à jour de la paie — URGENT !)
- **Toutes les URL pertinentes présentes dans le mail(<span style="background:#ff003366">LES MODIFIER POUR NE PAS QU'ELLES SOIENT CLIQUABLES</span>**) (Ex : hxxps : //Healthcare-United [.] com/wp/index/2020/PAYPAL/lure.php ?)
- **Pièces jointes** : nom du fichier + extension ainsi que les hashs
- **Description rapide du mail, de son contenu et de son objectif**



<span style="background:#8fc8e3">Quelle que soit la plateforme que vous utilisez pour stocker les notes d'enquête, nous joignons le fichier e-mail directement à notre dossier (dans les deux cas)`.` **eml** `ou. format **msg**`, fourni s'il le permet) afin que nous en ayons une copie aussi longtemps que nécessaire. Il est recommandé d'inclure une brève description de l'e-mail et une capture d'écran dans vos notes de cas, afin d'éviter aux autres analystes d'avoir à télécharger et à ouvrir eux-mêmes le fichier e-mail dans un client. Bien que l'apparence de l'e-mail ne soit pas très importante lorsqu'il s'agit de prendre des mesures défensives, elle est tout de même importante car elle peut être utilisée pour identifier des tendances ou des attaques ciblées, et générer des indicateurs sur le type d'e-mails malveillants reçus.
Vous devez vous efforcer d'écrire environ 1 à 2 phrases décrivant à quoi ressemble l'e-mail et ce qu'il essaie d'amener le destinataire à faire. Nous présentons ci-dessous deux exemples qui vous donneront des conseils sur la manière dont ces informations, ainsi que les artefacts, doivent être présentés de manière claire et concise.
</span>
---

**La deuxième partie d'un rapport concerne les mesures défensives prises :**

- **Blocage des artefacts des e-mails** (objet du mail, adresse d'envoi, adresse IP du serveur d'envoi)
- **Blocage des artefacts Web** (URL, domaine, IP)
- **Blocage des artefacts** de fichiers (nom du fichier, hachage du fichier)
En fonction des procédures de l'entreprise :
- **Des analystes capables de prendre eux-mêmes directement des mesures défensives**.
- **Les analystes qui doivent demander que des mesures défensives soient prises par des analystes seniors ou d'autres départements, et doivent fournir une justification suffisante**.
---
# <span style="background:#F1C5D8">Premier exemple complet :</span>

Dans cet exemple, l'analyste chargé de l'enquête a découvert un récupérateur d'identifiants DHL, qui a été reçu par 23 employés. Après avoir examiné l'e-mail, l'analyste récupère les artefacts suivants :

- **Expéditeur :** contact@dhl.com
- **IP du serveur d'envoi** : 209.85.167.42
- **DNS inversé** : mail-lf1-f42.google.com
- **Objet** : « Échec de livraison DHL RESPOND NOW — URGENT ! ! »
- **URL : hxxps :** _//dhl-faileddelivery.shanepppalkkbc.com (exemple de valeur)_

## **Exemple de section de rapport :**

« L'adresse d'envoi a réussi à usurper contact@dhl.com, mais l'adresse IP d'envoi a révélé qu'il s'agissait en fait d'une adresse Gmail, et donc pas de DHL. Nous ne sommes pas en mesure de bloquer l'adresse IP du serveur d'envoi, car elle appartient à Gmail, ce qui aurait un impact négatif sur l'entreprise car les e-mails légitimes seraient bloqués. Le blocage de l'expéditeur « contact@dhl.com » n'est pas non plus approprié, car les e-mails légitimes provenant de cette adresse seront bloqués. J'ai bloqué la ligne d'objet sur la passerelle de messagerie, car il est très peu probable que des e-mails DHL légitimes l'utilisent. Cela n'aurait aucun impact négatif sur l'entreprise, et cette action empêcherait que d'autres e-mails faisant l'objet de cette attaque ne soient envoyés aux boîtes aux lettres des employés.

Objet du mail : « Échec de livraison DHL RESPOND NOW — URGENT ! ! » le 22 décembre à 12:03 par Jane Smith.

L'URL utilisée dans l'outil de collecte d'informations d'identification est un domaine malveillant « shanepppalkkbc [.] com » qui utilise le sous-domaine « dhl-faileddelivery » pour être plus efficace lorsque vous consultez le lien. Après avoir étudié le domaine, il a été créé uniquement à des fins malveillantes, et rien ne justifie que les employés le consultent. Nous pouvons bloquer l'ensemble du domaine pour empêcher les utilisateurs de consulter le lien malveillant existant ou tout autre lien hébergé sur le site.

Bloc de domaine (proxy Web) « shanepppalkkbc [.] com » le 22 décembre à 12h07 par Jane Smith »

## **Exemple 1 : Récapitulatif :**

**L'analyste chargé de l'enquête :**

1. Résume que l'expéditeur de l'e-mail a été usurpé et que le message provient en fait de Gmail.
2. Comprend et déclare que le blocage d'une adresse IP d'envoi de Google aurait très probablement des conséquences négatives.
3. Explique que la valeur de l'adresse d'envoi falsifiée ne peut pas être bloquée, car elle est utilisée de manière légitime par DHL.
4. Indique les mesures qu'ils prennent et justifie cette décision.
5. Comprend et déclare que le blocage de la ligne d'objet inhabituelle n'aurait aucun impact négatif sur l'entreprise.
6. Répertorie le type de blocage effectué, la valeur bloquée, l'heure et la date de l'action, ainsi que l'auteur de l'action (indique la responsabilité).
7. Résume que l'URL est malveillante et n'appartient pas à DHL. Couvre rapidement les tactiques utilisées.
8. Indique les mesures qu'ils prennent et justifie cette décision.
9. Dressez la liste du type de blocage effectué, de la valeur bloquée, de l'heure et de la date de l'action, ainsi que de l'auteur de l'action (indique la responsabilité).

# <span style="background:#F1C5D8">Deuxième exemple complet :</span>

Dans cet exemple, un e-mail malveillant a été signalé à l'équipe de sécurité par le service de paie. L'e-mail prétend provenir du gouvernement britannique et demande au destinataire de consulter l'annonce fiscale ci-jointe. Après analyse de la pièce jointe, il s'est avéré qu'il s'agissait du logiciel malveillant Emotet(https://www.malwarebytes.com/emotet/), qui avait infecté deux machines avant d'être maîtrisé par l'équipe de réponse aux incidents. Le corps du contenu comportait également une URL qui permet de se connecter à un domaine et de télécharger exactement le même fichier que celui joint à l'e-mail. L'analyste chargé de l'enquête a extrait les IOC suivants :

- **Expéditeur :** HMRC-0fficial@govpayments.net
- **IP du serveur d'envoi** _: 129.33.19.188
- **DNS inversé** _: mail-govpayments.net
- **Objet** : "Annonce fiscale 2020 du HMRC IMPORTANTE"
- **URL : hxxp :** _//hmrc.announcementsgov.com/1jfa/download.php
- **Nom de la pièce jointe :** HMRC-Tax-Announcement-ReadMe.pdf.exe
- _Hachage **MD5 du fichier : 0a52730597fb4ffa01fc117d9e71e3a9**

## **Exemple de section de rapport :**

L'adresse d'envoi provient du domaine d'envoi @govpayments .net, qui n'est pas un site Web légitime utilisé par le gouvernement britannique et le HMRC. Bien que nous soyons en mesure de bloquer le domaine d'envoi car celui-ci tente de se faire passer pour un domaine légitime appartenant au gouvernement, nous n'avons reçu que des e-mails provenant d'une seule boîte aux lettres d'envoi, et le blocage du domaine à ce stade peut s'avérer excessif. Le blocage de l'expéditeur « HMRC-0fficial@govpayments.net » empêcherait l'envoi d'autres e-mails malveillants par cet expéditeur. Le blocage de cette adresse d'envoi malveillante n'aurait aucun impact négatif sur l'entreprise.

Envoi du bloc d'adresses (passerelle de messagerie) « HMRC-0fficial@govpayments.net » le 1er mars à 15h37 par Chris C.

L'URL utilisée dans l'e-mail est utilisée pour télécharger la même charge utile Emotet que la pièce jointe. Après avoir étudié le domaine, il a été créé uniquement à des fins malveillantes, et rien ne justifie que les employés le consultent. Nous pouvons bloquer l'ensemble du domaine pour empêcher les utilisateurs de consulter le lien malveillant existant ou tout autre lien hébergé sur le site.
****
Bloc de domaine (proxy Web) « hmrc.announcementsgov.com » le 1er mars à 15h41 par Chris C »

## **Exemple 2 : Récapitulatif :**

**L'analyste chargé de l'enquête :**

1. Résume que le domaine d'envoi du courrier électronique n'est pas un domaine légitime utilisé par le gouvernement et qu'il tente de se faire passer pour quelque peu légitime.
2. Explique que le blocage du domaine d'envoi, bien que malveillant, est excessif car, à l'heure actuelle, une seule boîte aux lettres d'envoi a été observée en train d'envoyer des e-mails malveillants.
3. Explique que le blocage de l'adresse d'envoi empêcherait la livraison d'un plus grand nombre d'e-mails.
4. Comprend et déclare que le blocage de l'adresse d'envoi n'aurait aucun impact négatif sur l'entreprise.
5. Répertorie le type de blocage effectué, la valeur bloquée, l'heure et la date de l'action, ainsi que l'auteur de l'action (indique la responsabilité).
6. Résume que l'URL est malveillante et qu'elle est utilisée pour télécharger le même fichier que celui inclus en tant que pièce jointe à un e-mail, et qu'il s'agit du logiciel malveillant Emotet.
7. Indique que le domaine est malveillant et fonctionne avec une intention purement malveillante, et que les employés n'ont aucune raison légitime de visiter le domaine.
8. Dressez la liste du type de blocage effectué, de la valeur bloquée, de l'heure et de la date de l'action, ainsi que de l'auteur de l'action (indique la responsabilité).

**==Lorsque vous rédigez vos rapports, il est essentiel de nettoyer toutes les URL ou adresses IP==**
- Entourez le «**.** » dans les URL et les adresses IP avec un « **[]** » devant devenir « **[.**] ».
- Remplacez le « **tt** » par « **xx** » dans le **http** des URL pour qu'il devienne « **hxxp** ».
- **8.8.8.8** _devient_ 8 [.] 8 [.] 8 [.] 8 **https://hello.example.com _devient_ hxxp [://] hello [.] example [.] com
- L'outil https://gchq.github.io/CyberChef/ peut le faire avec l'option "Defang IP Addresses"



# <span style="background:#F1A5D8">Autre exemple complet :</span>

## **Description de l'e-mail et artefacts collectés**

**Adresse d'envoi :** emailsecalert1@gmail.com

**Objet :** Votre e-mail sera verrouillé ! Agissez dès maintenant !

**Destinataires :**  
john.smith@dicksonunited.co.uk  
alice.cooper@dicksonunited.co.uk  
jacon.long@dicksonunited.co.uk  
fred.johnson@dicksonunited.co.uk  
pickle.rick@dicksonunited.co.uk

**IP du serveur d'envoi :** 209.85.222.173

**DNS inversé** : mail-qk1-f173.google.com (Gmail)

**Répondre à : emailsecalert1@gmail.com**

**Date et heure** : 15 h 21, lundi 1er juin 2020

**URL complète (désinfectée) : hxxps :** //outlook-security.emailsecalerts [.] net/index/2020/OWA.php ?

**Domaine racine :** hxxps : //emailsecalerts [.] net

Si vous examinez l'e-mail signalé dans le client de messagerie Outlook, ce message se fait passer pour une alerte de sécurité Outlook en utilisant une marque telle que des logos Outlook. L'e-mail informe les destinataires que leur boîte aux lettres sera fermée à moins qu'ils ne confirment leur identité, ce qui leur demande de cliquer sur un bouton, ce qui entraîne probablement une collecte d'informations d'identification en fonction du contexte de l'e-mail.

## **Analyse des artefacts**

La vérification de la passerelle de messagerie indique qu'aucun e-mail n'a été envoyé à l'adresse d'envoi. Par conséquent, aucun destinataire n'a répondu à l'expéditeur.

Une recherche DNS inversée sur l'adresse IP du serveur d'envoi montre que cet e-mail provient certainement de Gmail et non de Microsoft.

URL2PNG l'analyse montre que l'URL complète est un outil de collecte d'informations d'identification Outlook, demandant aux utilisateurs de saisir leur adresse e-mail et leur mot de passe.

Une VirusTotal recherche sur le domaine montre qu'il a été signalé comme étant malveillant et qu'il est donc connu pour son caractère malveillant au sein de la communauté des spécialistes de la sécurité.

En vérifiant le SIEM et l'EDR, aucun employé n'a établi de connexion réseau avec le domaine malveillant. Aucun destinataire n'a donc cliqué sur le lien contenu dans l'e-mail pour le moment.

Le domaine tente également de faire une faute de frappe ou d'apparaître comme un domaine légitime lié aux alertes de sécurité par e-mail, dans le but de rendre l'attaque plus crédible aux yeux des cibles.

## **Mesures défensives suggérées**

Comme l'expéditeur utilise une adresse Gmail, l'action la plus appropriée serait de bloquer cette boîte aux lettres spécifique afin d'empêcher tout nouvel envoi d'e-mails malveillants en provenance de cet expéditeur.

**Demande d'un bloc de passerelle de messagerie pour l'adresse d'envoi «** **emailsecalert1@gmail.com ».**

Le domaine a été reconnu comme malveillant et rien ne justifie que des employés aient besoin d'accéder à ce site. Comme il a une réputation malveillante et que des analyses VirusTotal ont montré qu'il héberge un outil de collecte d'informations d'identification, l'ensemble du domaine peut être bloqué sur le proxy Web, empêchant ainsi les employés de se connecter au site. Cela rendra également inefficaces les futures attaques de phishing utilisant ce même domaine.

**Demande d'un bloc de proxy Web pour le domaine «** **hxxps : //emailsecalerts [.] net ».**