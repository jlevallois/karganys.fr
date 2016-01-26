---
ID: 1096
post_title: >
  Écran noir après mise à jour de
  Raspbian
author:
  - 'a:1:{i:0;s:18:"Jérémy Levallois";}'
  - 'a:1:{i:0;s:18:"Jérémy Levallois";}'
post_date:
  - 2016-01-24 16:27:51
post_excerpt:
  - ""
layout: post
permalink:
  - /?p=1096
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";s:4:"1134";s:11:"_thumb_type";s:5:"thumb";}'
  - 'a:2:{s:9:"_thumb_id";s:4:"1134";s:11:"_thumb_type";s:5:"thumb";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
En ce moment je m'amuse avec mon [Raspberry Pi 2](https://www.raspberrypi.org/help/what-is-a-raspberry-pi/). J'ai installé [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) dessus, une version spéciale de Debian pour Raspberry.

## Problème

Après avoir mis à jour (`sudo apt-get update &amp;&amp; sudo apt-get upgrade`) et redémarré Raspbian, aucun message d'erreur ne s'affiche pendant le démarrage mais l'écran reste noir avec le [curseur blanc](https://fr.wikipedia.org/wiki/Curseur_(interface)) qui clignote.

 Impossible de démarrer Raspbian.

## Solution

La source du problème est toute simple. Raspbian, en s'installant, partitionne la carte SD contenant le système d'exploitation de façon à ne pas utiliser trop de place. Le problème, c'est dès lors qu'il y a beaucoup de mises à jour à faire, il ne reste plus assez de place libre pour les installer. Et cela engendre des paquets *sensibles* qui ne s'installent pas correctement.

Je ne sais pas s'il y a une solution pour refaire fonctionner votre Raspbian. Par contre, il y a un moyen d'éviter cela lors de votre prochaine installation de Raspbian :

- Installer Raspbian (comme avant).
- Lancer la commande `sudo raspi-config` et sélectionner **exprend_rootfs** : cela aura pour conséquence d'étendre la partition de Raspbian au maximum de la capacité de la carte SD.

* * *

**Testé sur** : Raspbian Jessie et Raspberry Pi 2