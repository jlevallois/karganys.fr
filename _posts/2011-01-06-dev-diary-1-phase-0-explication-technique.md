---
ID: 551
post_title: 'Dev Diary #1 : Phase 0 &#8211; Explication technique'
author: Jérémy Levallois
post_date: 2011-01-06 18:41:04
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/dev-diary/dev-diary-1-phase-0-explication-technique/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
---
<strong>Phase 0 : Explication technique</strong>

Quelques mois avant la proposition du Game Concept aux encadrants de Gamagora, Adobe a officiellement annoncé qu'il serait désormais possible de développer des application entièrement avec AIR 2.5, qui pourront être lu sur un iPhone. Le Game Concept initial avait pour objectif de faire un jeu en Flash pour iPhone.
Comment ça marche ? En fait Adobe utilise une machine virtuelle (LLVM) qui interprétera le code Flash sur l'iPhone (iOS ne lit que le code Objective-C compilé normalement).
Dans un même temps, Adobe annonce également que le portage d'AIR se fera également sur Android, bénéficiant du Runtime AIR disponible gratuitement sur l'Android Market.
La différence entre les deux, c'est que sur Android, c'est plus permissif et plus optimisé que sur iOs (les sempiternelles disputes entre Apple et Adobe en sont la cause). Par exemple, chaque application AIR pour iOs possède sa propre VM, alors que les applications AIR pour Android se partagent la même.

Le projet était initialement proposé pour être porté sur iPhone, mais les tests que nous avons fait ont montré qu'il serait préférable de le porter sur Android, grâce à la LLVM bien intégrée à Android.

Les avantages d'utiliser AIR au lieu de faire une application Flash disponible à partir du web ?
- L'application s’exécute plus rapidement. En fait, elle a beaucoup plus d'espace disponible pour s’exécuter, ainsi que de ressource (CPU, etc ...).
- Accès aux fonctionnalités du téléphone (Accéléromètre, GPS, etc ...). Bien que certaines soient disponible pour du Flash "basique" (comprendre sans utiliser AIR), la majorité sont restreintes.
- Pouvoir l'utiliser hors-ligne, étant donné qu'elle est installée comme une application normale.
- Pouvoir la distribuer sur l'Android Market ou market alternatifs.

Prochaine étape : Les tests.

Source : <a href="http://www.adobe.com/products/air/">Adobe</a>