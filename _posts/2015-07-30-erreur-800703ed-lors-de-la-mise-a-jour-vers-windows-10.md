---
ID: 1053
post_title: >
  Erreur 800703ED lors de la mise à jour
  vers Windows 10
author: Jérémy Levallois
post_date: 2015-07-30 10:51:24
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/windows-10/erreur-800703ed-lors-de-la-mise-a-jour-vers-windows-10/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";s:4:"1057";s:11:"_thumb_type";s:5:"thumb";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
<strong>La mise à jour vers Windows 10</strong> est disponible depuis hier dans le monde, et beaucoup en ont profité pour mettre à jour leur vieux Windows 7/8/8.1 vers la dernière version du système d'exploitation de Microsoft. Outre les "Something happened" que certains ont reçu (super les messages d'erreurs, d'ailleurs), la majorité des transferts se sont passés sans grande difficulté.

Sauf pour moi. Lorsque j'ai voulu mettre à jour mon Windows 7 à partir de Windows Update, j'ai reçu <code>Error Code 800703ED</code>. Impossible de trouver des informations dans la documentation de Microsoft, et personne ne semble avoir la même erreur que moi.

Après plusieurs heures de recherches, j'ai enfin trouvé d'autres personnes ayant cette erreur. Il semblerait que <strong>ce soit dû au dual-boot</strong>.

Ma machine a un dual-boot Linux Mint / Windows, et chaque OS est sur un disque dur séparé. Il semblerait que la cause provienne de la table de partition, dans laquelle la partition Windows n'est pas marquée comme partition active. Un moyen simple <strong>pour résoudre ce soucis </strong>et pouvoir mettre à jour votre Windows vers Windows 10 est de <strong>débrancher votre disque dur Linux</strong> pendant toutes les étapes de la mise à jour.

Vous noterez l'emploi du conditionnel, puisque je n'ai pas eu de soucis sur mon PC portable qui possède un dual-boot également (mais sur le même disque dur).

<h3>Edit (05/08/2015) :</h3>
Comme le précise <a href="https://lf-net.org/~littlefox/"><strong>LittleFox</strong></a> dans les commentaires (puis <strong>SpiKe</strong>), l'erreur peut apparaître également lorsque nous avons un <strong>dual-boot sur un seul disque</strong>, et la piste de la partition Windows pas marquée comme active semble se confirmer. 
Dans son cas, il faut alors <strong>marquer la partition Windows comme active</strong> dans le <strong>gestionnaire de disques Windows</strong> pour bénéficier de la mise à jour. 

<strong>Attention</strong> cependant, cela interfère avec le boot loader (l'amorce en français, mais c'est pas super sexy je trouve :/) de Linux, et vous devrez le rétablir ensuite. Donc je vous déconseille de faire cette manipulation si vous ne savez pas comment faire (<a href="https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows">c'est simple à remettre</a>, mais il faut savoir s'y prendre).

<strong>Source :</strong> <a href="https://www.reddit.com/r/windows/comments/3ezwsm/error_800703ed_on_windows_10_update_is_caused_by/">Jotokun sur Reddit</a>