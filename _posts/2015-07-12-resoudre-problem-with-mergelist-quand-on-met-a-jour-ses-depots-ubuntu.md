---
ID: 1024
post_title: 'Résoudre &laquo;&nbsp;Problem with MergeList&nbsp;&raquo; quand on met à jour ses dépôts Ubuntu'
author: Jérémy Levallois
post_date: 2015-07-12 18:46:44
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/ubuntu/resoudre-problem-with-mergelist-quand-on-met-a-jour-ses-depots-ubuntu/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
layout_key:
  - ""
  - ""
post_slider_check_key:
  - "0"
  - "0"
---
J'ai eu la mauvaise surprise récemment en voulant installer un paquet sous Ubuntu d'obtenir une erreur bloquante "**Problem with MergeList**".

```sh
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_banshee-team_ppa_ubuntu_dists_trusty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
```

De ce que j'ai compris, MergeList s'occupe de générer une liste de toutes les sources de dépôts de votre machine en prenant les sources dans `/etc/apt/sources.list` et celles définies dans le dossier `/etc/apt/sources.list.d/`, et un conflit est apparu. 

Une solution simple consiste à supprimer les fichiers générés par MergeList (sans risque) et de les regénérer :
```sh
#!/bin/sh
 
# remove all mergelists (safe) and regenerate them
sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update
```

* * *

**Testé sur** : Linux Mint 17.1