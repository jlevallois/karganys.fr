---
ID: 424
post_title: >
  Nombre de connexions à Facebook en 1
  minute
author: Jérémy Levallois
post_date: 2010-09-23 22:06:41
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/news/nombre-de-connexions-a-facebook-en-1-minute/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
---
<div class="wp-caption alignnone" style="width: 250px;"><a href="http://www.flickr.com/photos/fireatwillrva/5018150585/"><img src="http://farm5.static.flickr.com/4085/5018150585_aa918b6744_m.jpg" title="9/23/2010 (18/365)" alt="9/23/2010 (18/365)" width="240" height="93" /></a><p class="wp-caption-text"><a href="http://www.flickr.com/photos/fireatwillrva/5018150585/">9/23/2010 (18/365)</a> by <a href="http://www.flickr.com/photos/fireatwillrva/">Fire At Will [Photography]</a></p></div>


Ce soir, Facebook connait quelques soucis. L'impossibilité de se connecter touche apparemment le monde entier, d'après <a href="http://twitter.com/#search?q=facebook">Twitter</a> et <a href="http://downforeveryoneorjustme.com/facebook.com">Down for Everyone or Just Me</a>

À travers sa page d'erreur, nous pouvons tirer une petite information sur le nombre de personnes qui accèdent à Facebook.com au même moment.
La page d'erreur affiche un numéro de ticket :

<blockquote>Service Unavailable - DNS failure

The server is temporarily unable to service your request. Please try again later.
Reference #11.1a3f293e.1285275310.15b74c6c</blockquote>

Ce numéro de référence s'incrémente à chaque nouvelle connexion sur le site, et à chaque raffraichissement.
Ainsi, j'ai noté ces numéros avec une minute d'intervalle, à 22h55 et 22h56, et ai pu en tirer un nombre approximatif de connexion à Facebook.com :

<blockquote>À 22h55 : Reference #11.1a3f293e.1285275310.<strong>15b74c6c</strong>
À 22h56 : Reference #11.1a3f293e.1285275375.<strong>15b852a9</strong></blockquote>

Les chiffres après le dernier point (d'après mes observations sont déterminant du nombre de tickets) sont en base 16, c'est à dire qu'après 9, il y a A, puis B, C, D, E et F
base16(15b74c6c) = base10(364334188)
base16(15b852a9) = base10(364401321)

On fait la différence :
364401321 - 364334188 = <strong>67 133 connexions à <a href="http://www.facebook.com">Facebook.com</a> en 1 minute</strong>.

Ok, ça parait vraiment immense, mais il faut relativiser tout ça.

Premièrement, le site est down pour le monde entier, c'est à dire que une grosse partie des utilisateurs spamment leur touche F5 pour voir si le site réapparait, à chaque F5, une incrémentation du numéro (donc ce n'est pas un traffic "normal").

Ajoutez à celà tous les sites qui incluent un bout de page Facebook, pour converser avec d'autres utilisateurs, tous les smartphones qui rafraîchissent les données de Facebook, et que c'est l'après-midi aux États-Unis.