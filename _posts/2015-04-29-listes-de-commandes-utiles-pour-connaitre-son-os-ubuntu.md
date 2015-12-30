---
ID: 982
post_title: >
  Listes de commandes utiles pour
  connaître son OS Ubuntu
author: Jérémy Levallois
post_date: 2015-04-29 21:04:07
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/ubuntu/listes-de-commandes-utiles-pour-connaitre-son-os-ubuntu/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";i:991;s:11:"_thumb_type";s:10:"attachment";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
Voici un ensemble de commandes utiles pour connaître un peu mieux votre installation Ubuntu :

<table>
	<tr>
		<th><strong>Commande</strong></th>
		<th><strong>Description</strong></th>
		<th><strong>Résultat</strong></th>
	</tr>
	<tr>
		<td><code>gnome-shell --version</code></td>
		<td>Version de Gnome</td>
		<td>GNOME Shell 3.14.4</td>
	</tr>
	<tr>
		<td><code>uname -r</code></td>
		<td>Version des headers Linux</td>
		<td>3.16.0-33-generic</td>
	</tr>
	<tr>
		<td><code>lsb_release -d</code></td>
		<td>Version de Ubuntu</td>
		<td>Description:  Ubuntu 15.04</td>
	</tr>
	<tr>
		<td><code>lsb_release -c</code></td>
		<td>Nom de code de votre version de Ubuntu</td>
		<td>Codename:  vivid</td>
	</tr>
	<tr>
		<td><code>df -h</code></td>
		<td>L'espace disque utilisé sur toutes les partitions</td>
		<td>Filesystem      Size  Used Avail Use% Mounted on<br />
		/dev/sda1        37G   13G   22G  37% /</td>
	</tr>
	<tr>
		<td><code>ifconfig | grep HWaddr</code></td>
		<td>Adresse MAC</td>
		<td>eth0    Link encap:Ethernet HWaddr AA:BB:CC:DD:EE:FF</td>
	</tr>
	<tr>
		<td><code>uptime</code></td>
		<td>Temps écoulé depuis le dernier démarrage</td>
		<td>21:53:22 up</td>
	</tr>
	<tr>
		<td><code>who -b</code></td>
		<td>Date du dernier démarrage de l'ordinateur</td>
		<td>System boot 2015-04-29 09:28</td>
	</tr>
	<tr>
		<td><code>who -q</code></td>
		<td>Utilisateurs connectés sur l'ordinateur</td>
		<td>userA userB<br />
		# users=2</td>
	</tr>
	<tr>
		<td><code> lspci -v -s `lspci | awk '/VGA/{print $1}'`</code></td>
		<td>Informations sur votre carte graphique</td>
		<td>...</td>
	</tr>
</table>

<strong>Testé sur :</strong> Ubuntu 15.04 et Gnome 3.14.4