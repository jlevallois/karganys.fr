---
ID: 45
post_title: Introduction à la Motion Capture
author: Jérémy Levallois
post_date: 2009-12-21 17:12:16
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/mocap/introduction-a-la-motion-capture/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";i:49;s:11:"_thumb_type";s:10:"attachment";}'
---
On voit de plus en plus d'application à la Motion Capture ( Capture de Mouvements ) de nos jours. La MoCap, technique permettant de capturer les mouvements d'un acteur du monde réel au monde virtuel, pour faire simple, est utilisée dans les films d'animation, les jeux-vidéo, la robotique, etc ... Elle permet d'animer des avatars facilement tout en respectant le plus fidèlement les mouvements de l'acteur, mais également peut servir pour améliorer l'immersion de l'utilisateur. Pour ne citer qu'un exemple, le projet <a href="http://www.xbox.com/en-US/live/projectnatal/" target="_blank">Natal</a> de Microsoft résume bien cette tendance qui se démocratise.

Voyons plus en détail le fonctionnement de la MoCap.

Tout d'abord, deux types de MoCap se distinguent. La première utilise des marqueurs sur l'acteur ( on parle d'acteur pour la personne qui effectue les mouvements qui seront retranscris informatiquement ), et la seconde n'en utilise pas.

<strong>La Capture de Mouvements avec marqueurs :</strong>
L'acteur doit enfiler une combinaison d'une couleur uni, noir par exemple. On place ensuite les marqueurs sur sa combinaison.
[caption id="attachment_46" align="alignnone" width="300" caption="Acteur en combinaison portant des marqueurs"]<a href="http://www.karganys.fr/wp-content/uploads/2009/12/mocap.jpg"><img src="http://www.karganys.fr/wp-content/uploads/2009/12/mocap-300x269.jpg" alt="Acteur en combinaison" title="mocap" width="300" height="269" class="size-medium wp-image-46" /></a>[/caption]  Ces marqueurs doivent être visibles, le plus souvent il s'agit de balles de ping-pong blanches réfléchissantes (blanc sur noir, c'est facilement repérable).
L'acteur est alors entouré de caméras qui le filment toutes en même temps, dans différents points de vue. 
[caption id="attachment_48" align="alignnone" width="300" caption="Exemple de disposition de Capture de Mouvements"]<a href="http://www.karganys.fr/wp-content/uploads/2009/12/arena_mocap_setup.gif"><img src="http://www.karganys.fr/wp-content/uploads/2009/12/arena_mocap_setup-300x190.gif" alt="Disposition Motion Capture" title="mocap_setup" width="300" height="190" class="size-medium wp-image-48" /></a>[/caption]
Ainsi, à l'aide de tous les enregistrements, on pourrait recomposer une vue en 3D de l'acteur. Pour se faire, on va identifier sur chaque vidéo les marqueurs, et les faire correspondre avec ceux des autres flux vidéo ( c'est pour celà qu'il faudra bien calibrer les caméras avant, pour ne pas avoir d'erreur lors du matching de marqueurs ) et donc récupérer les coordonnées x, y et z de chaque marqueurs. Le nombre de marqueurs varie en fonction de ce que l'on souhaite retranscrire. On pourrait utiliser plusieurs marqueurs pour le visage si l'on souhaite capturer une émotion, ou n'en mettre qu'un seul si l'on souhaite juste avoir le déplacement de l'acteur.
[caption id="attachment_49" align="alignnone" width="300" caption="De l\'acteur à l\'avatar"]<a href="http://www.karganys.fr/wp-content/uploads/2009/12/Activemarker2.png"><img src="http://www.karganys.fr/wp-content/uploads/2009/12/Activemarker2-300x213.png" alt="" title="Activemarker2" width="300" height="213" class="size-medium wp-image-49" /></a>[/caption]

<object width="560" height="340"><param name="movie" value="http://www.youtube.com/v/IxJrhnynlN8&hl=fr_FR&fs=1&"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/IxJrhnynlN8&hl=fr_FR&fs=1&" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="560" height="340"></embed></object>
Utilisation de la MoCap avec marqueurs Pour Assassin's Creed 2

Cette technique est aujourd'hui la plus utilisée, mais possède quelques défauts.
Les marqueurs doivent toujours être visibles par les caméras et placés aux endroits stratégiques. On veut capturer les attaques d'un boxer, mais ce n'est vraiment pas pratique de placer des marqueurs sur les gants de boxe. La présence des marqueurs limite le champ d'action.
Le constat s'effectue également pour les animaux, difficile de mettre des marqueurs à un cheval ( mais ça a déjà été fait ), à un python royal ou ) une tarentule :)

La liste est exhaustive, mais c'est pour palier à celà qu'est née la <strong>Capture de Mouvements sans marqueur</strong>
Au revoir les balles de ping-pong, l'acteur n'a plus besoin d'équipement spécifique. Le seul besoin matériel est la disposition des caméras tout autour de l'acteur comme pour la MoCap avec marqueurs. Ensuite tout le travail s'effectue par le(s) ordinateur(s). 
Il existe plusieurs techniques pour y arriver, car, même si la technique est bien avancée, elle reste encore jeune.
L'idéal serait d'avoir un "fond vert" ( en fait la couleur dépend de la tenue de l'acteur, elle doit être facilement distinguable ), pour facilement extraire l'acteur du reste. Sinon il existe des algorithmes qui enregistre une première fois la scène sans l'acteur, puis avec l'acteur pour faire une simple soustraction de fond. D'autres encore ne prennent en compte que les pixels qui varient.
Pour retranscrire les mouvements de l'acteur, certains algorithmes essaient de faire correspondre le "tas de pixels" qu'il représente une fois séparé du background avec une silhouette humaine, en s'aidant de la chrominance si nécessaire ( pour distinguer la peau par exemple ). Ainsi, on peut voir les mouvements de l'acteur dans l'espace, ce qui permet de les reconstituer.

Voici un exemple simple de Motion Capture MarkerLess :
<object width="425" height="344"><param name="movie" value="http://www.youtube.com/v/vqYursDTOCQ&hl=fr_FR&fs=1&"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/vqYursDTOCQ&hl=fr_FR&fs=1&" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="425" height="344"></embed></object>
Un autre exemple serait Project Natal :
<object width="560" height="340"><param name="movie" value="http://www.youtube.com/v/I9tmr8VDqN8&hl=fr_FR&fs=1&"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/I9tmr8VDqN8&hl=fr_FR&fs=1&" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="560" height="340"></embed></object>
( Enfin, là je demande à voir quand même :) )

Il s'agit d'une introduction à la Motion Capture, j'ai encore pas mal de choses à dire sur ce sujet, notamment au niveau de la MoCap MarkerLess, mais se sera dans un prochain article :)

Sources images : <a href="http://www.animationarchive.org">Lien</a> | <a href="http://technabob.com">Lien</a> | <a href="http://www.wikipedia.com">Lien</a>