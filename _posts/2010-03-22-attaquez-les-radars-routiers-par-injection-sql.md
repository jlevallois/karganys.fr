---
ID: 102
post_title: >
  Attaquez les radars routiers par
  injection SQL
author: Jérémy Levallois
post_date: 2010-03-22 19:29:22
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/programmation/php/attaquez-les-radars-routiers-par-injection-sql/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";s:3:"103";s:11:"_thumb_type";s:5:"thumb";}'
---
Une news qui m'a fait beaucoup rire, donc je vous la partage.
Sur <a href="http://www.gizmodo.com" target="_blank">Gizmodo</a>, on nous propose, comme pour les sites internet, d'attaquer les radars à l'aide d'une injection SQL.

[caption id="attachment_103" align="alignnone" width="1024" caption="Injection SQL pour radar routier"]<a href="http://www.karganys.fr/wp-content/uploads/2010/03/for_traffic_cameras.jpg"><img src="http://www.karganys.fr/wp-content/uploads/2010/03/for_traffic_cameras-1024x768.jpg" alt="Injection SQL pour radar routier" title="Injection SQL pour radar routier" width="600" height="400" class="size-large wp-image-103" /></a>[/caption]

L'injection SQL est une technique utilisée par les "pirates informatiques" pour avoir accès à certaines informations confidentielles d'une base de données en exploitant l'absence de méfiance du développeur.
Un exemple simple est un formulaire d'inscription, avec un champ pseudo. Si le développeur ne fait pas de traitement de ce champ et l'envoie directement dans sa requête qui modifie sa base de données, il pourrait se retrouver avec quelques désagréments.

La requête SQL aura donc une forme ressemblant à ceci :
<pre lang="php">INSERT INTO users VALUES ('$pseudo');</pre>

Un utilisateur met normalement aura dans la variable $pseudo son pseudo, mais si quelqu'un met à la place un bout de code SQL, nous parlons d'injection SQL.
<pre lang="php">$pseudo = "a'); DROP DATABASE users; -- ";
INSERT INTO users VALUES ('$pseudo');</pre>

sera l'équivalent de :
<pre lang="php">INSERT INTO users VALUES ('a'); DROP DATABASE users;--');</pre>
Qui aura pour conséquence de supprimer toute la table users contenant tous les utilisateurs du site (Et -- pour mettre en commentaire la fin de la ligne, afin de ne pas générer d'erreurs).

Ainsi, avec un peu de carton, vous pouvez faire une injection SQL sur un radar routier comme le montre la photo précédente ! Ensuite un algorithme de reconnaissance lit les chiffres et les lettres sur les plaques d'immatriculation, et les rajoute dans la base de données. Dans les faits, il y a peu de chances que ça fonctionne car je pense qu'ils ont prévu le coup (voire ne stocke pas dans une base de données SQL, ou encore ne reconnait pas certains caractères spéciaux comme la virgule), mais l'idée reste assez géniale.

<a href="http://gizmodo.com/5498412/sql-injection-license-plate-hopes-to-foil-euro-traffic-cameras" target="_blank">Source</a> - Merci mAn pour le lien