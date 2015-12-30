---
ID: 1000
post_title: >
  Ajouter le dictionnaire français à
  Sublime Text 3
author: Jérémy Levallois
post_date: 2015-05-28 21:50:56
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/ubuntu/ajouter-le-dictionnaire-francais-a-sublime-text-3/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";i:1018;s:11:"_thumb_type";s:10:"attachment";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
<a href="http://www.karganys.fr/wp-content/uploads/2015/05/multi-line-selection.gif"><img src="http://www.karganys.fr/wp-content/uploads/2015/05/multi-line-selection.gif" alt="Sublime Text" width="500" height="280" class="aligncenter size-full wp-image-1018" /></a>

Si vous utilisez l'éditeur de code <a href="http://www.sublimetext.com/">Sublime Text</a>, vous avez dû vous rendre compte que celui-ci n’inclut pas par défaut de dictionnaire français pour la correction orthographique. Voici comment le rajouter facilement sous Linux.

Il suffit de créer un package <strong>"Language - French"</strong> et d'y télécharger le dictionnaire français utilisé avec Hunspell. Les commandes suivantes vous permettront de le faire :

https://gist.github.com/jlevallois/cc37842952f823363ebf

Ensuite, il faut sélectionner le dictionnaire français dans Sublime Text (<strong>View > Dictionary > Language-French > French</strong>)

Pensez à activer la correction orthographique avec la touche <strong>F6</strong> ou <strong>View > Spell Check</strong>


<strong>Source </strong>: <a href="http://blog.smarchal.com/correcteur-orthographique-francais-sublime-text">Samuel Marchal</a> (pour Windows)
<strong>Testé sur</strong> : Linux Mint 17.1 et Sublime Text 3