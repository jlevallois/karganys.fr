---
ID: 1155
post_title: 'scholar.js &#8211; un parser de Google Scholar pour afficher le nombre de citations sur votre site'
author: Jérémy Levallois
post_date: 2016-02-03 00:05:03
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/recherche/scholar-js-un-parser-de-google-scholar-pour-afficher-le-nombre-de-citations-sur-votre-site/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
---
Cela fait quelques temps que je m'intéresse aux bibliothèques JavaScript, assez
incontournable en ce moment si vous vous intéressez au web. J'ai donc voulu
mettre les mains dedans sachant que je partais d'une connaissance quasi nulle
dans le domaine. Et j'ai fait ma première bibliothèque JavaScript.

# scholar.js

Je ne trouvais pas de moyen d'afficher le nombre de citations pour mes
publications sur le [site web de ma
thèse](http://liris.cnrs.fr/jeremy.levallois/publications.html), Google Scholar
ne disposant pas d'API.

Alors je l'ai créé, non sans mal (*merci jQuery de ne pas autoriser de récuperer des fichiers s'il n'est pas hébergé dans le domaine courant*).

## TL;DR

**scholar.js** vous permet d'afficher une compteur de citations sur votre site web, grâce à Google Scholar.

## Utilisation
&gt; *Le tutoriel est pour la version 0.1.0, merci d'adapter le numéro de version en fonction des releases de scholar.js*

- Télécharger scholar.js (la version minimifiée **scholar-0.1.0.min.js**) : [https://github.com/jlevallois/scholar.js/releases](https://github.com/jlevallois/scholar.js/releases)

- Importer **jQuery** et **scholar.js** :

  ```html
  
  
  ```

  ou les charger directement depuis mon serveur kha.li :

  ```html
  
  
  ```

- Ajouter des span (ou autre chose) lorsque vous voulez obtenir un compteur de citations :

  ```html
  <span class="scholar"></span>
  ```
  Attributs:
  - `class="scholar"`: active le parser.
  - `name="XXXXX"`: nom de la publication (Attention : le nom doit être **exactement** le même que celui de votre publication sur Google Scholar).
  - `with-link="true|false"`: (optionnel) ajouter un lien vers la page Google Schole de votre publication.

- Puis, charger les données avec votre identifiant Google Scholar en bas de page :

  ```js
  Scholar.debug = true; // (optionnel) Active les messages de debug dans la console.
  Scholar.load("YOUR-GOOGLE-SCHOLAR-ID"); // Trouvez le sur votre profil Google Scholar.
  ```
  Par exemple, lorsque je vais sur **My Citations** sur Google Scholar, l'URL est [https://scholar.google.com/citations?user=-BL0_2EAAAAJ&amp;hl=en](https://scholar.google.com/citations?user=-BL0_2EAAAAJ&amp;hl=en), mon identifiant Google Scholar est donc **-BL0_2EAAAAJ**.

## Exemple

```html

  
    
    
  
  
    <p>Integral based Curvature Estimators in Digital Geometry -
      <span class="scholar">
        <!-- ajouter une image de chargement ici -->
      </span>
    </p>
    
      Scholar.load("-BL0_2EAAAAJ");
    
  

```

### Résultat

&gt; Integral based Curvature Estimators in Digital Geometry - [12](https://scholar.google.fr/citations?view_op=view_citation&amp;hl=fr&amp;user=-BL0_2EAAAAJ&amp;citation_for_view=-BL0_2EAAAAJ:u5HHmVD_uO8C)

## Exemples en ligne

- [http://liris.cnrs.fr/jeremy.levallois/publications.html](http://liris.cnrs.fr/jeremy.levallois/publications.html)
- [http://liris.cnrs.fr/david.coeurjolly/publications.html](http://liris.cnrs.fr/david.coeurjolly/publications.html)

## Oh, au fait, scholar.js est open-source

Tout le code est disponible sur [Github](https://github.com/jlevallois/scholar.js) :octocat:, et est sous licence [Creative Commons CC BY-NC-SA 4.0](http://creativecommons.org/licenses/by-nc-sa/4.0/). Si vous souhaitez contribuer, j'ai mis un guide à disposition [https://github.com/jlevallois/scholar.js/blob/master/CONTRIBUTING.md](https://github.com/jlevallois/scholar.js/blob/master/CONTRIBUTING.md).

## Ça marche pas !

Ça peut arriver. Si tel est le cas, merci de me le signaler en [ouvrant un ticket](https://github.com/jlevallois/scholar.js/issues) détaillant le problème.