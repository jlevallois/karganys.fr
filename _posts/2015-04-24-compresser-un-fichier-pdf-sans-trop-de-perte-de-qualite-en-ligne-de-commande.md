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
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
Je cherchais comment compresser un article assez volumineux pour une soumission (d'ailleurs, dédicace au site de soumission de Elsevier qui ne mentionne pas de limite de poids pour <del datetime="2015-04-24T12:19:32+00:00">l'uploade</del> téléversement (lol) et se contente d'envoyer un mail marqué "Error.").

Nous allons utiliser Ghostscript (<code>sudo apt-get install ghostscript</code> sous Ubuntu).

https://gist.github.com/jlevallois/ad0d3a72ad9b45d1c170

Vous pouvez jouer avec le paramètre <code>-dPDFSETTINGS</code> pour le résultat final (de celui qui compresse le plus à celui qui compresse le moins) :
<ul>
	<li><code>-dPDFSETTINGS=/screen</code> – basse résolution. Beaucoup d'artefacts de compression apparaissent sur les images.</li>
	<li><code>-dPDFSETTINGS=/ebook</code> – moyenne résolution. Moyennement acceptable, quelques artefacts sont visibles.</li>
	<li><code>-dPDFSETTINGS=/printer</code> – haute résolution. Le résultat est vraiment pas mal.</li>
	<li><code>-dPDFSETTINGS=/prepress</code> – très haute résolution. Sur mes tests, je n'ai pas vu de différence visuelle par rapport à la version non compressée.</li>
	<li><code>-dPDFSETTINGS=/default</code> – il va essayer de trouver les meilleurs paramètres. Le résultat peut être volumineux.</li>
</ul>

Dans mon exemple, mon fichier PDF pesait 120Mo avant compression, et comportait beaucoup d'images HD assez volumineuses.

<table>
	<tr>
		<th><strong>Paramètre</strong></th>
		<th><strong>Poids</strong><br />(en Mo)</th>
		<th><strong>Taux de compression</strong><br />(plus c'est proche de 0, mieux c'est)</th>
	</tr>
	<tr>
		<td>Non compressé</td>
		<td>127.9</td>
		<td>1</td>
	</tr>
	<tr>
		<td>/screen</td>
		<td>0.469</td>
		<td>0.003666927</td>
	</tr>
	<tr>
		<td>/ebook</td>
		<td>1.3</td>
		<td>0.010164191</td>
	</tr>
	<tr>
		<td>/printer</td>
		<td>6.0</td>
		<td>0.04691165</td>
	</tr>
	<tr>
		<td>/prepress</td>
		<td>9.8</td>
		<td>0.076622361</td>
	</tr>
	<tr>
		<td>/default</td>
		<td>10.6</td>
		<td>0.082877248</td>
	</tr>
</table>

Sauf si vous avez vraiment besoin de fortement réduire la taille de votre fichier PDF, je vous conseille d'utiliser <code>/printer</code>, <code>/prepress</code> ou <code>/default</code> pour éviter de dénaturer vos images.


<strong>Source :</strong> <a href="http://www.tjansson.dk/2012/04/compressing-pdfs-using-ghostscript-under-linux/">tjansson.dk</a>
<strong>Testé avec :</strong> Ghostscript 9.14 et Ubuntu 14.10