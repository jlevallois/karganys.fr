---
ID: 1040
post_title: >
  Afficher les numéros des
  sous-sous-sections avec LaTeX
author: Jérémy Levallois
post_date: 2015-07-27 15:10:09
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/programmation/latex/afficher-les-numeros-des-sous-sous-sections-avec-latex/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
Par défaut avec LaTeX, seules les parties (<code>\part{}</code>), sections (<code>\section{}</code>) et sous-sections (<code>\subsection{}</code>) ont un numéro. Vous pouvez ajouter des numéros pour vos sous-sous-sections (<code>\subsubsection{}</code>) facilement en rajoutant (ou modifiant) cette commande dans votre document :
<pre lang="latex">\setcounter{secnumdepth}{3}</pre>

Ainsi, les sous-sous-sections seront numérotés comme les sections ou les sous-sections.
Notez que vous pouvez définir d'autres niveaux, "3" correspondant aux sous-sous-sections : 
<table>
	<tr>
		<th><strong>Commande</strong></th>
		<th><strong>Niveau</strong></th>
	</tr>
	<tr>
		<td><code>\part{}</code></td>
		<td>-1</td>
	</tr>
	<tr>
		<td><code>\chapter{}</code></td>
		<td>0</td>
	</tr>
	<tr>
		<td><code>\section{}</code></td>
		<td>1</td>
	</tr>
	<tr>
		<td><code>\subsection{}</code></td>
		<td>2</td>
	</tr>
	<tr>
		<td><code>\subsubsection{}</code></td>
		<td>3</td>
	</tr>
	<tr>
		<td><code>\paragraph{}</code></td>
		<td>4</td>
	</tr>
	<tr>
		<td><code>\subparagraph{}</code></td>
		<td>5</td>
	</tr>
</table>