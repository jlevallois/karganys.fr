---
ID: 723
post_title: Désactiver le chat de Facebook
author: Jérémy Levallois
post_date: 2011-08-15 21:10:27
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/web/desactiver-le-chat-de-facebook/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";s:3:"918";s:11:"_thumb_type";s:5:"thumb";}'
---
<div class="wp-caption alignnone" style="width: 510px;"><a href="http://www.flickr.com/photos/naudinsylvain/6042396273/"><img src="http://farm7.static.flickr.com/6194/6042396273_3f371afc22.jpg" title="Chat du g&Atilde;&reg;te" alt="Chat du g&Atilde;&reg;te" width="500" height="332" /></a><p class="wp-caption-text"><a href="http://www.flickr.com/photos/naudinsylvain/6042396273/">Chat du gÃ®te</a> by <a href="http://www.flickr.com/photos/naudinsylvain/">Sylvain Naudin</a></p></div>


Je n'utilise pas le chat Facebook. Déjà que je jongle avec tous les systèmes de messagerie instantanée d'un peu tout le monde (GTalk, Skype, WLM (MSN), ...), je ne vais pas <em>en plus</em> chatter sur Facebook.

Jusqu'à présent, je me mettais <strong>Hors Ligne</strong> et tout allait pour le mieux dans le meilleur des mondes possibles.
Bien ... Sauf depuis la nouvelle mise à jour de Facebook, avec la nouvelle barre latérale.

Depuis, quand vous ouvrez Facebook alors vous étiez <strong>Hors Ligne</strong> sur le site, vous serez <strong>Disponible </strong>un court moment avant de vous faire vraiment déconnecter du chat. Juste immonde !
J'ai vu pleins de manipulations sur Internet pour le désactiver totalement, mais aucune ne fonctionnait/était vraiment à jour.
Sauf celle utilisant AdBlock Plus, une extension très pratique pour <a href="https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/" title="Addons Mozilla Firefox">Firefox</a>/<a href="https://chrome.google.com/webstore/detail/cfhdojbkjhnklbpkdaibdccddilifddb" title="Addons Google Chrome">Google Chrome</a>.
Pour ceux qui ne connaissent pas cette extension, elle vous permet de ne plus afficher les publicités lors de vos navigations.
Mais vous pouvez aussi rajouter des filtres manuellement. Nous allons nous servir de ça.

Tout d'abord, allez sur Facebook, déconnectez vous du Chat et cachez la barre latérale.
Ensuite, rendez-vous dans les paramètres d'AdBlock Plus :
<strong>Option</strong> > <strong>Customize</strong> > Cliquez sur <strong>Edit</strong> à côté de <strong>Manually edit your filters</strong>
Le champ du dessous se dégrise, rajouter la ligne suivante :
<pre lang="css">facebook.com##div[id*="presence"]</pre>
Cliquez sur <strong>Save </strong>pour sauvegarder, rechargez la page de Facebook et le chat aura totalement disparu.

Quand vous réouvrirez Facebook, il ne chargera pas le module de chat, et donc ne vous connectera pas l'espace de quelques instant.

Si vous voulez réactiver le chat, supprimez la ligne précédente des filtres de AdBlock.

Source : <a href="http://www.twoslashes.com/miscellaneous/removing-the-chat-from-facebook-chat/">Two Slashes</a>