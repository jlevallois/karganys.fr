---
ID: 520
post_title: 'Android &#8211; Trop de schémas de déblocage et pas de compte Google'
author: Jérémy Levallois
post_date: 2010-12-27 15:53:22
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/android/android-trop-de-schemas-de-deblocage-et-pas-de-compte-google/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";s:3:"521";s:11:"_thumb_type";s:5:"thumb";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.10.6/moment-with-locales.min.js"></script>

<p style="color:#FF0000"><h2>Avertissement :</h2>
Cet article a été écrit <span id="time_since_article"></span>, ses informations peuvent être obsolètes.</p><p>

<script>
                var writingTime = moment("2010122716","YYYYMMDDHH", 'fr'); // +1 for Paris timezone
                document.getElementById("time_since_article").innerHTML = writingTime.fromNow();
</script>

<br />

<strong>Edit du 29/12/2010 :</strong>
Je viens de tester les deux méthodes sur mon HTC Desire sous Android 2.2, la faille a été corrigée. Aucune des deux méthodes présentées juste au dessus ne fonctionne sous cette version. Par contre cela devrait encore fonctionner sous Android < 2.2.

Un ami s'est retrouvé dans une fâcheuse posture avec son téléphone sous Android.

Il n'avait pas synchronisé de compte Google avec son téléphone, et avait mis en place la sécurité des schémas (Pattern) pour prévenir toute utilisation frauduleuse de son téléphone pendant son absence.

<img src="http://www.karganys.fr/wp-content/uploads/2010/12/android-pattern-lock-266x400-199x300.jpg" alt="Android pattern Lock" title="Android pattern Lock" width="199" height="300" class="size-medium wp-image-521" />

Lorsque l'on tente trop de fois un mauvais schéma, le téléphone se bloque pour quelques secondes. Au bout de trop d'essais infructueux, il se bloque totalement et demande le compte Google (et son mot de passe) associé au téléphone pour redéfinir un nouveau schéma.

Oui, mais comment faire si aucun compte Google n'avait été associé auparavant ?

Faille ou pas, il existe une solution permettant de ne pas envoyer son téléphone au service après-vente de son opérateur (de débourser quelques euros et de se retrouver sans téléphone quelques temps).
<ul>
	<li>Avec un autre téléphone, téléphonez au numéro du téléphone bloqué.</li>
	<li>Répondez, puis appuyez sur la touche Retour (Ne raccrochez pas!).</li>
	<li>Vous avez accès au menu, mais le téléphone n'est toujours pas déverrouillé. Lorsque vous raccrocherez, vous serez à nouveau bloqué.</li>
	<li>Rendez-vous dans les <strong>Paramètres</strong>.</li>
	<li>Allez dans <strong>SD et mémoire</strong>.</li>
	<li>Puis cliquez sur <strong>Reset Usine</strong> (<em><strong>Attention, vous perdrez tout ce que vous avez sauvegardé dessus, c'est un reset usine du téléphone !</strong></em>). Votre téléphone s'éteindra puis se rallumera, déverrouillé cette fois-ci.</li>
</ul>

Il existe d'autres solutions, mais elles n’avaient pas fonctionné (enfin du moins apparemment, j'avais fait de la maintenance par téléphone). J'en cite une tout de même en provenance du <a href="http://forum.frandroid.com/topic/5674-trop-de-schema-de-deblocage-pas-de-compte-google-mail-sur-le-mobile/">forum de frandroid.com</a> :
<ul>
	<li>Créez un <a href="https://www.google.com/accounts/NewAccount?service=mail&continue=http://mail.google.com/mail/e-11-118d2a4c20b21058603a08004a5eb582-83318b211c4dae62e33d317b7a04dc8e04169cb7&type=2">compte Google</a> depuis votre PC.</li>
	<li>Depuis votre téléphone, rentrez votre identifiant Google (si votre adresse GMail est machin@gmail.com, votre identifiant Google sera <strong>machin</strong>).</li>
	<li>Mettez comme mot de passe : <strong>null</strong> .</li>
	<li>Votre téléphone vous proposera donc de redéfinir un schéma et se déverrouillera.</li>
</ul></p>