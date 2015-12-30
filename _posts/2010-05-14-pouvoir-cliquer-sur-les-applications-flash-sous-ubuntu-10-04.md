---
ID: 149
post_title: >
  Pouvoir cliquer sur les applications
  Flash sous Ubuntu 10.04
author: Jérémy Levallois
post_date: 2010-05-14 11:41:16
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/ubuntu/pouvoir-cliquer-sur-les-applications-flash-sous-ubuntu-10-04/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
---
<div class="wp-caption alignnone" style="width: 343px;"><a href="http://www.flickr.com/photos/64k/4551717056/"><img alt="Les aventures de la petite souris, Nathan, 1968" src="http://farm5.static.flickr.com/4033/4551717056_ec1d595df9.jpg" title="Les aventures de la petite souris, Nathan, 1968" width="333" height="500" /></a><p class="wp-caption-text"><a href="http://www.flickr.com/photos/64k/4551717056/">Les aventures de la petite souris, Nathan, 1968</a> by <a href="http://www.flickr.com/photos/64k/">64k.be</a></p></div>

Bonjour à tous.

J'ai réinstaller récemment Ubuntu dans sa dernière version (10.04) et à ma grande suprise, impossible d'installer le lecteur flash d'Adobe sous le navigateur internet Chromium.

La manipulation pour y arriver est en fait très simple :
Ouvrez le terminal, puis exécutez ces commandes :
<pre lang="sh">sudo apt-get install flashplugin-nonfree
sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/chromium-browser/plugins/</pre>
La première ligne installe le player flash sur votre système, et la seconde copie le plugin flash dans le répertoire plugins de Chromium.
Ensuite, pour lancer Chromium avec le lecteur flash, vous devez lancer la commande suivante :
<pre lang="sh">chromium-browser - -enable-plugins</pre>
(il n'y a pas d'espaces entre les deux - -, mais si je les colle Wordpress les interprète comme un -- ).
Je vous conseille de faire un raccourci sur votre lanceur d'application afin de ne pas avoir à refaire la commande à chaque fois.

Mais Oh rage, Oh désespoir, vous voyez les animations flash, mais impossible d'interagir avec !
Que diable, résolvons ceci de suite !

<pre lang="sh">sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer</pre>
Ce qui vous ouvre l'éditeur de texte Gedit
Ajoutez donc, <strong>avant</strong> la dernière ligne, la ligne suivante :
<pre lang="sh">export GDK_NATIVE_WINDOWS=1</pre>
Sauvegardez, puis relancer Chromium (ou tout autre navigateur car le problème apparait sur l'ensemble des navigateurs sous Ubuntu 10.04).

Voilà, vous pouvez à nouveau cliquer sur les animations flash !

Source : <a href="http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html" target="_blank">HelpForLinux</a>