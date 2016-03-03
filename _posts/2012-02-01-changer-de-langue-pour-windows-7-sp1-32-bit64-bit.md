---
ID: 734
post_title: >
  Changer de langue pour Windows 7 SP1
  32-bit/64-bit
author: Jérémy Levallois
post_date: 2012-02-01 23:12:07
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/windows-seven/changer-de-langue-pour-windows-7-sp1-32-bit64-bit/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";i:736;s:11:"_thumb_type";s:10:"attachment";}'
  - 'a:2:{s:9:"_thumb_id";i:736;s:11:"_thumb_type";s:10:"attachment";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
Ce qui était bien en étant étudiant, c'est que j'avais accès au programme MSDNAA (MicroSoft Developer Network Academic Alliance), et par la même occasion à une copie gratuite de Windows 7 32 et 64 bit.

Le problème, c'est que lors de l'installation de cette version, il est impossible de changer la langue de Windows 7 (en français de base).

Il existe une méthode pour installer le pack langue anglais (ou toute autre langue) grâce à [Vistalizator](http://www.froggie.sk/) et au MUI correspondant à la langue à installer, seulement, si vous avez oublié de le faire avant d'avoir installé le Service Pack 1 de Windows 7, cette méthode est obsolète.

**MAIS** ! Il existe une autre méthode pour Windows 7 SP1 beaucoup moins "grand public" dans laquelle il faut utiliser des lignes de commandes.
Je vais vous expliquer comment faire.

> **Pensez à sauvegarder vos documents important, au cas où quelque chose ne se passe pas bien.
Le changement de langue est une opération "à risque", et il se peut que vous soyez amené à réinstaller Windows en cas d'erreur !**

Tout d'abord, il faut que votre Windows 7 possède le SP1, que vous obtiendrez en mettant à jour via [Windows Update](http://windowsupdate.microsoft.com).

Il faut également que vous sachiez quelle version de Windows 7 vous utilisez (32 ou 64 bits) :
[![img](http://www.karganys.fr/wp-content/uploads/2012/02/32or64b-300x249.jpg)](http://www.karganys.fr/wp-content/uploads/2012/02/32or64b.jpg)

Puis téléchargez le MUI de la langue que vous souhaitez installer : [http://www.pcdiy.com/146/windows-7-service-pack-1-language-packs-download](http://www.pcdiy.com/146/windows-7-service-pack-1-language-packs-download)

Et enfin téléchargez un petit outil qui va nous permettre de transformer le .exe du MUI en .cab : [Exe2Cab](http://www.froggie.sk/download/exe2cab.exe)

Nous voilà enfin prêt pour démarrer le changement de langues.
- Ouvrez exe2cab en mode administrateur (clic droit dessus &gt; Lancer en mode administrateur), sélectionnez le MUI que vous venez de télécharger ( **windows6.1-kb2483139-x64-en-us_9b9c8a867baff2920507fbf1e1b4a158572b9b87.exe** pour la version anglaise ), et enregistrez le .cab (renommez le **LP.cab** pour que ce soit plus simple par la suite).
- Ouvrez l'invite de commande en mode administrateur : **Windows** &gt; **Tous les programmes** &gt; **Accessoires** &gt; Clic droit sur **Invite de Commande** &gt; **Lancer en mode administrateur**.
- Dans un premier temps nous allons installer la langue :
  ```dos
  DISM /Online /Add-Package /PackagePath:C:\LP.cab
  ```
  (Changez **C:\LP.cab** par l'adresse où se situe le fichier **LP.cab** sur votre machine) et cliquez sur Entrer.
  Si vous obtenez l'erreur **87** ou **0x80070057**, c'est que probablement votre .exe est corrompu, ou bien sa transformation en .cab a échouée.

- Puis nous allons changer la langue par défaut de Windows 7 :
  ```dos
  bcdedit /set {current} locale en_US
  ```
  (Changez **en_US** par la langue de votre MUI. Vous pouvez obtenir le code dans le nom du .exe que vous avez téléchargé : windows6.1-kb2483139-x64-**en-us**_9b9c8a867baff2920507fbf1e1b4a158572b9b87.exe , respectez bien la notation **xx_XX**).

- Et enfin nous la mettons par défaut au démarrage :
  ```dos
  bcdboot %WinDir% /l en_US
  ```
  (Là encore, changez **en_US** par la langue de votre MUI).

- Dernière étape, nous allons supprimer l'ancienne langue, inutile désormais. Pour cela, il faut se rendre dans l'éditeur de registre (**[Win]+[R]** &gt; **regedit**), rendez-vous dans le dossier **HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Control/MUI/UILanguages** et supprimez le sous-dossier de votre ancienne langue (**fr-FR** pour moi).

- Redémarrez votre machine, et le changement de langue s'est effectué !