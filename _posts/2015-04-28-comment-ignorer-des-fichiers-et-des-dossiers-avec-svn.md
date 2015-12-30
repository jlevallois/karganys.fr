---
ID: 974
post_title: >
  Comment ignorer des fichiers et des
  dossiers avec SVN
author: Jérémy Levallois
post_date: 2015-04-28 20:21:28
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/ubuntu/comment-ignorer-des-fichiers-et-des-dossiers-avec-svn/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
Vous pouvez facilement ignorer des fichiers et des dossiers avec Subversion localement à un dépôt, soit en utilisant un pattern (<code>*.txt</code> par exemple), soit en spécifiant le fichier à ignorer (<code>file1.txt</code>)

Vous devez vous déplacer dans le dossier dans lequel vous voulez ignorer des fichiers/dossiers.
La commande suivante va spécifier les fichiers et dossiers à ignorer localement au dossier courant (le dossier doit être versionné). Vous pouvez spécifier un sous-dossier en changeant le <code>.</code> par son nom.
https://gist.github.com/jlevallois/5cf4b824d61f0cc4eb3f
Une fenêtre nano va s'ouvrir dans laquelle vous pourrez spécifier les filtres des fichiers/dossiers à ignorer.
Si nous ajoutons ces filtres :
<code>*.txt</code>
<code>folder1</code>
<code>main.pdf</code>
<code>*.log</code>
tous les fichiers <code>txt</code>, le dossier <code>folder1</code>, le fichier <code>main.pdf</code> et tous les fichiers <code>.log</code> seront désormais ignorés par Subversion.

Sauvegardez (<code>CTRL+X</code> et répondez <code>Y</code> pour sauvegarder), et n'oubliez pas de commiter les changements.



<strong>Testé avec :</strong> Subversion 1.8.8 et Ubuntu 14.10