---
ID: 146
post_title: >
  Réparer le démarrage de Windows
  Vista/7 après suppression de Linux
author: Jérémy Levallois
post_date: 2010-05-06 21:43:54
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/windows-seven/reparer-le-demarrage-de-windows-vista7-apres-suppression-de-linux/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
---
<div class="wp-caption alignnone" style="width: 510px;"><a href="http://www.flickr.com/photos/tirandofotos/4571984705/"><img alt="Error 99" src="http://farm5.static.flickr.com/4034/4571984705_d295409ede.jpg" title="Error 99" width="500" height="375" /></a><p class="wp-caption-text"><a href="http://www.flickr.com/photos/tirandofotos/4571984705/">Error 99</a> by <a href="http://www.flickr.com/photos/tirandofotos/">tirandofotos</a></p></div>

Post assez rapide, mais qui me permettra de garder une trace au lieu de rechercher la manipulation quand ça me tombe dessus avec le navigateur de la PS3 ou de iPhone, et ça peut vous servir aussi :)

Vous êtes en dual-boot (ou tri-boot) avec Windows Vista ou Windows 7 et une distribution de Linux (Ubuntu dans mon cas), et pour une raison qui vous est propre, vous voulez supprimer la partition Linux. Vous reformatez donc le disque dur l'accueillant, et à votre prochain démarrage, vous avez ce joli message d'erreur qui s'affiche :

<blockquote>GRUB loading stage1.5.
GRUB loading, please wait
Error 17</blockquote>

Non, fermez tout de suite la fenêtre par laquelle vous projetiez de défenestrer votre ordinateur, il y a une solution toute simple pour tout réparer !

Bon déjà pourquoi ça ne marche plus. En fait votre ordinateur, après l'apparition du BIOS, a besoin de connaître quels disques durs et quelles partitions contiennent des secteurs "bootables" (contenant un système d'exploitation). Windows possède le sien, mais son inconvénient est qu'il ne supporte pas d'autres systèmes d'exploitations que Windows, limité donc. Ainsi, pour faire du multiboot, il faut installer en dernier Linux pour installer le <a href="http://fr.wikipedia.org/wiki/GRand_Unified_Bootloader" target="_blank">GRUB</a> de Linux, qui lui supporte tous les systèmes d'exploitations. En supprimant la partition Linux, vous supprimez également les secteurs d'amorçages nécessaires au bon fonctionnement du GRUB.

Voilà pour le principe, maintenant comment on le répare (en fait, on va remettre celui de Windows) ?

Il vous faut le <strong>DVD d'installation</strong> de Windows Vista ou Seven ( la démarche est sensiblement la même ).
Lancez le, puis choississez lorsque la possibilité se présentera, l'option <strong>Réparer</strong>.
Choississez d'utiliser <strong>L'invite de commande Windows</strong>.
Rentrez les commandes suivantes :
<pre lang="sh">bootrec  /FixMbr
bootrec  /FixBoot</pre>
Vous aurez normalement un message de confirmation pour chacune des commandes.
<strong>Redémarrez</strong> donc, et vous constaterez que la méchante Error 17 est partie !

Cette technique ne marche que pour l'Error 17, et pour Windows 7 ou Windows Vista, pour Windows XP, la commande à utiliser est apparement (je ne l'ai pas testé) :
<pre lang="sh">fixmbr</pre>