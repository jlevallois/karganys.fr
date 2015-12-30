---
ID: 1030
post_title: 'Récupérer l&rsquo;adresse du serveur SVN sur Ubuntu'
author: Jérémy Levallois
post_date: 2015-07-16 09:29:40
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/ubuntu/recuperer-ladresse-du-serveur-svn-sur-ubuntu/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
Vous utilisez déjà un serveur SVN pour versionner vos fichiers, mais vous ne vous rappelez plus de son adresse ? Vous pouvez facilement le récupérer grâce à la commande <pre lang="shell">svn info</pre> (à faire dans votre dossier versionné) :

https://gist.github.com/jlevallois/07ce3a6a06dd7b45400c

<strong>Testé sur :</strong> Linux Mint 17.1 et Subversion 1.8.8