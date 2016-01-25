---
ID: 967
post_title: >
  Concaténer plusieurs PDF de
  différentes tailles en un seul, en
  ligne de commande
author: Jérémy Levallois
post_date: 2015-04-26 18:58:57
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/ubuntu/concatener-plusieurs-pdf-de-differentes-tailles-en-un-seul-en-ligne-de-commande/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
Toujours avec Ghostscript (voir «[Compresser un fichier PDF sans (trop de) perte de qualité en ligne de commande](http://www.karganys.fr/systemes-d-exploitation/ubuntu/compresser-un-fichier-pdf-sans-trop-de-perte-de-qualite-en-ligne-de-commande/)»), je voulais concaténer plusieurs fichiers PDF en un seul, avec une subtilité : tous mes fichiers PDF ne sont pas au même format de page. Certains sont en A4, d'autres non. Je les veux tous au même format de page.

https://gist.github.com/5152e32afdc8d825ec8e

Ghostscript va concaténer tous les fichiers PDF de votre dossier par ordre alphabétique de nom (vous pouvez aussi donner les fichiers à la main, changez `*.pdf` par `file1.pdf file2.pdf file3.pdf` etc.)

`-sPAPERSIZE=a4` renseigne la cible de format de page, vous pouvez en choisir un différent (la liste complète est disponible ici : [http://vis.lbl.gov/NERSC/Software/ghostview/docs/Use.htm#Known_paper_sizes](http://vis.lbl.gov/NERSC/Software/ghostview/docs/Use.htm#Known_paper_sizes))

`-dPDFFitPage` va mettre à l'échelle tous les documents ne respectant pas la contrainte de format de page précédente.

Pensez à vérifier le résultat (`output.pdf`) car la mise à l'échelle peut modifier la mise en page de vos documents.

**Testé avec :** Ghostscript 9.14 et Ubuntu 14.10
