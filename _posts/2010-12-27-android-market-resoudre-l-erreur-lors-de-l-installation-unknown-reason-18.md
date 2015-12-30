---
ID: 512
post_title: 'Android Market : Résoudre l&rsquo;erreur lors de l&rsquo;installation Unknown reason &#8211; 18'
author: Jérémy Levallois
post_date: 2010-12-27 12:14:30
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/android/android-market-resoudre-l-erreur-lors-de-l-installation-unknown-reason-18/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
---
<div class="wp-caption alignnone" style="width: 510px;"><a href="http://www.flickr.com/photos/tamaleaver/5275810388/"><img src="http://farm6.static.flickr.com/5085/5275810388_e15a218df5.jpg" title="Android + Phone" alt="Android + Phone" width="500" height="336" /></a><p class="wp-caption-text"><a href="http://www.flickr.com/photos/tamaleaver/5275810388/">Android + Phone</a> by <a href="http://www.flickr.com/photos/tamaleaver/">Tama Leaver</a></p></div>


J'ai eu il y a quelques temps la désagréable Erreur - 18 lorsque j'essayait de mettre à jour ou d'installer une application en provenance de l'Android Market.

<blockquote>Unknown reason - 18</blockquote>

J'ai lu de tout et de n'importe quoi pour résoudre ce problème, notamment certaines solutions nécessitant de rooter son téléphone, mais la solution est beaucoup plus basique que ça (et ne mettant pas en péril la garantie de votre téléphone).
<ul>
<li> Connectez votre téléphone à votre ordinateur grâce au cable USB (Sélectionnez <strong>Lecteur de Disque</strong> sur votre téléphone afin de pouvoir afficher le contenu de la carte mémoire de votre téléphone).</li>
<li> Déplacez-vous dans le dossier <strong>.android_secure</strong> (Il est vide si vous vous y rendez depuis votre téléphone. Faites cette manipulation de votre ordinateur).</li>
<li> Supprimez le fichier temporaire <strong>smdl2tmp1.asec</strong> .</li>
</ul>

Et voila, rien d'autre à faire, vous pouvez désormais installer vos applications en provenance de l'Android Market sans difficulté :)