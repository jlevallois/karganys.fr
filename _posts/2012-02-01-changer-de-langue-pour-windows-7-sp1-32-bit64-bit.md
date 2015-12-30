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
---
<div class="wp-caption alignnone" style="width: 510px;">

<a href="http://www.flickr.com/photos/hostilemakeover/6456922089/"><img src="http://farm8.staticflickr.com/7031/6456922089_543f66962b.jpg" title="Help? - Additional question updates." alt="Help? - Additional question updates." width="500" height="342" /></a>
<p class="wp-caption-text"><a href="http://www.flickr.com/photos/hostilemakeover/6456922089/">Help? - Additional question updates.</a> by <a href="http://www.flickr.com/photos/hostilemakeover/">HostileMakeover</a></p>

</div>


Ce qui était bien en étant étudiant, c'est que j'avais accès au programme MSDNAA (MicroSoft Developer Network Academic Alliance), et par la même occasion à une copie gratuite de Windows 7 32 et 64 bit.

Le problème, c'est que lors de l'installation de cette version, il est impossible de changer la langue de Windows 7 (en français de base).

Il existe une méthode pour installer le pack langue anglais (ou toute autre langue) grâce à <a href="http://www.froggie.sk/">Vistalizator</a> et au MUI correspondant à la langue à installer, seulement, si vous avez oublié de le faire avant d'avoir installé le Service Pack 1 de Windows 7, cette méthode est obsolète.

<strong>MAIS</strong> ! Il existe une autre méthode pour Windows 7 SP1 beaucoup moins "grand public" dans laquelle il faut utiliser des lignes de commandes.
Je vais vous expliquer comment faire.

<strong>Pensez à sauvegarder vos documents important, au cas où quelque chose ne se passe pas bien.
Le changement de langue est une opération "à risque", et il se peut que vous soyez amené à réinstaller Windows en cas d'erreur !</strong>

Tout d'abord, il faut que votre Windows 7 possède le SP1, que vous obtiendrez en mettant à jour via <a href="http://windowsupdate.microsoft.com">Windows Update</a>.

Il faut également que vous sachiez quelle version de Windows 7 vous utilisez (32 ou 64 bits) :
<a href="http://www.karganys.fr/wp-content/uploads/2012/02/32or64b.jpg"><img class="aligncenter size-medium wp-image-736" title="" src="http://www.karganys.fr/wp-content/uploads/2012/02/32or64b-300x249.jpg" alt="" width="300" height="249" /></a>

Puis téléchargez le MUI de la langue que vous souhaitez installer : <a href="http://www.pcdiy.com/146/windows-7-service-pack-1-language-packs-download">http://www.pcdiy.com/146/windows-7-service-pack-1-language-packs-download</a>

Et enfin téléchargez un petit outil qui va nous permettre de transformer le .exe du MUI en .cab : <a href="http://www.froggie.sk/download/exe2cab.exe">Exe2Cab</a>

Nous voilà enfin prêt pour démarrer le changement de langues.
<ul>
	<li>Ouvrez exe2cab en mode administrateur (clic droit dessus &gt; Lancer en mode administrateur), sélectionnez le MUI que vous venez de télécharger ( <strong>windows6.1-kb2483139-x64-en-us_9b9c8a867baff2920507fbf1e1b4a158572b9b87.exe</strong> pour la version anglaise ), et enregistrez le .cab (renommez le <strong>LP.cab</strong> pour que ce soit plus simple par la suite).</li>
	<li>Ouvrez l'invite de commande en mode administrateur : <strong>Windows</strong> &gt; <strong>Tous les programmes</strong> &gt; <strong>Accessoires</strong> &gt; Clic droit sur <strong>Invite de Commande</strong> &gt; <strong>Lancer en mode administrateur</strong>.</li>
	<li>Dans un premier temps nous allons installer la langue :
<pre lang="dos">DISM /Online /Add-Package /PackagePath:C:\LP.cab</pre>
(Changez <strong>C:\LP.cab</strong> par l'adresse où se situe le fichier <strong>LP.cab</strong> sur votre machine) et cliquez sur Entrer
Si vous obtenez l'erreur <strong>87</strong> ou <strong>0x80070057</strong>, c'est que probablement votre .exe est corrompu, ou bien sa transformation en .cab a échouée.</li>

	<li>Puis nous allons changer la langue par défaut de Windows 7 :</li>

<pre lang="dos">bcdedit /set {current} locale en_US</pre>
(Changez <strong>en_US</strong> par la langue de votre MUI. Vous pouvez obtenir le code dans le nom du .exe que vous avez téléchargé : windows6.1-kb2483139-x64-<strong>en-us</strong>_9b9c8a867baff2920507fbf1e1b4a158572b9b87.exe , respectez bien la notation <strong>xx_XX</strong>)

	<li>Et enfin nous la mettons par défaut au démarrage :

<pre lang="dos">bcdboot %WinDir% /l en_US</pre>
(Là encore, changez <strong>en_US</strong> par la langue de votre MUI)</li>

	<li>Dernière étape, nous allons supprimer l'ancienne langue, inutile désormais. Pour cela, il faut se rendre dans l'éditeur de registre (<strong>[Win]+[R]</strong> &gt; <strong>regedit</strong>), rendez-vous dans le dossier <strong>HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Control/MUI/UILanguages</strong> et supprimez le sous-dossier de votre ancienne langue (<strong>fr-FR</strong> pour moi).</li>

<li>Redémarrez votre machine, et le changement de langue s'est effectué !</li>
</ul>