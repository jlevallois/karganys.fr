---
ID: 929
post_title: >
  Compresser un fichier PDF sans (trop de)
  perte de qualité en ligne de commande
author: Jérémy Levallois
post_date: 2015-04-24 17:25:14
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/ubuntu/compresser-un-fichier-pdf-sans-trop-de-perte-de-qualite-en-ligne-de-commande/
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
Je cherchais comment compresser un article assez volumineux pour une soumission (d'ailleurs, dédicace au site de soumission de Elsevier qui ne mentionne pas de limite de poids pour <del datetime="2015-04-24T12:19:32+00:00">l'uploade</del> téléversement (lol) et se contente d'envoyer un mail marqué "Error.").

Nous allons utiliser Ghostscript (`sudo apt-get install ghostscript` sous Ubuntu).

```sh
#!/bin/sh

gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.5 -dPDFSETTINGS=/default -dNOPAUSE -dQUIET -dBATCH -dUseCIEColor -sOutputFile=output.pdf input.pdf
```

Vous pouvez jouer avec le paramètre `-dPDFSETTINGS` pour le résultat final (de celui qui compresse le plus à celui qui compresse le moins) :

- `-dPDFSETTINGS=/screen` – basse résolution. Beaucoup d'artefacts de compression apparaissent sur les images.
- `-dPDFSETTINGS=/ebook` – moyenne résolution. Moyennement acceptable, quelques artefacts sont visibles.
- `-dPDFSETTINGS=/printer` – haute résolution. Le résultat est vraiment pas mal.
- `-dPDFSETTINGS=/prepress` – très haute résolution. Sur mes tests, je n'ai pas vu de différence visuelle par rapport à la version non compressée.
- `-dPDFSETTINGS=/default` – il va essayer de trouver les meilleurs paramètres. Le résultat peut être volumineux.

Dans mon exemple, mon fichier PDF pesait 120Mo avant compression, et comportait beaucoup d'images HD assez volumineuses.

| Paramètre  | Poids (en Mo)  | Taux de compression <br />(plus c'est proche de 0, mieux c'est) |
| :------------ |:-----:| -----------:|
| Non compressé | 127.9 | 1           |
| /screen       | 0.469 | 0.003666927 |
| /ebook        | 1.3   | 0.010164191 |
| /printer      | 6.0   | 0.04691165  |
| /prepress     | 9.8   | 0.076622361 |
| /default      | 10.6  | 0.082877248 |

Sauf si vous avez vraiment besoin de fortement réduire la taille de votre fichier PDF, je vous conseille d'utiliser `/printer`, `/prepress` ou `/default` pour éviter de dénaturer vos images.

---
**Source :** [tjansson.dk](http://www.tjansson.dk/2012/04/compressing-pdfs-using-ghostscript-under-linux/)

**Testé avec :** Ghostscript 9.14 et Ubuntu 14.10