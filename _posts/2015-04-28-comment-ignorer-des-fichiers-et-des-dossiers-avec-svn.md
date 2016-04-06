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
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
layout_key:
  - ""
  - ""
post_slider_check_key:
  - "0"
  - "0"
---
Vous pouvez facilement ignorer des fichiers et des dossiers avec Subversion localement à un dépôt, soit en utilisant un pattern (<code>*.txt</code> par exemple), soit en spécifiant le fichier à ignorer (`file1.txt`)

Vous devez vous déplacer dans le dossier dans lequel vous voulez ignorer des fichiers/dossiers.
La commande suivante va spécifier les fichiers et dossiers à ignorer localement au dossier courant (le dossier doit être versionné). Vous pouvez spécifier un sous-dossier en changeant le `.` par son nom.

```bash
#!/bin/sh

# edit SVN ignore list for current folder
svn propedit svn:ignore .
```

Une fenêtre nano va s'ouvrir dans laquelle vous pourrez spécifier les filtres des fichiers/dossiers à ignorer.
Si nous ajoutons ces filtres :
```
*.txt
folder1
main.pdf
*.log
```
tous les fichiers `txt, le dossier `folder1`, le fichier `main.pdf et tous les fichiers `.log` seront désormais ignorés par Subversion.

Sauvegardez (`CTRL+X` et répondez `Y` pour sauvegarder), et n'oubliez pas de commiter les changements.


* * * 

**Testé avec :** Subversion 1.8.8 et Ubuntu 14.10