---
ID: 1073
post_title: WordPress et Github
author:
  - Jérémy Levallois
post_date: 2015-12-30 17:31:03
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/web/wordpress-et-github/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
J'utilise quotidiennement GitHub depuis plusieurs années maintenant, tant dans le cadre professionnel ([DGtal][1], [DGtalTools][2], [ICTV][3], [PhD-Thesis][4], etc.) que personnel. **J'aime GitHub**.

D'autant plus qu'ils ont pris le parti de mettre en avant le langage **Markdown**, un langage à syntaxe simple et claire qui simplifie grandement la création de documents. Si vous voulez vous essayer au Markdown, une éditeur en ligne est disponible [ici][5].

Cela fait quelques temps que j'envisage de passer mon blog en statique, où j'écrirais mes posts en Markdown que je synchroniserais moi-même sur le blog. Principalement parce que c'est moins lourd qu'un blog Wordpress, et que c'est plus facile à maintenir. Par contre, ça demande pas mal de travail, et surtout je perdrais pas mal de fonctionnalités utiles.

C'est alors que je suis tombé *par hasard* sur un plugin permettant de synchroniser ses posts sur **GitHub**, en les écrivant en **Markdown**, et qui seront convertis en posts sur **Wordpress**. Euh ... bah c'est juste génial, non ?

Le plugin s'appelle [Wordpress GitHub Sync][6], et je suis actuellement en train de l'essayer.

## Installation

### Dans le panel administation de votre site Wordpress

*   Allez dans `Extensions &gt; Ajouter` et recherchez **Wordpress GitHub Sync**.
*   Cliquez sur **Installer maintenant** pour l'installer.

### Sur votre compte GitHub

*   Créez un **nouveau repository** : `Repository &gt; New`.
*   Nommez le comme bon vous semble (usuellement, on donne le nom du site. **karganys.fr** dans mon cas)
*   Vous pouvez le rendre **Public** ou **Private**, selon si vous souhaitez que vos articles soient disponibles publiquement ou pas.
*   Cliquez sur `Create repository`, le voici créé.
*   Rendez-vous à [cette adresse][7] afin de créer un nouveau **token** pour que votre site Wordpress puisse accéder en lecture et en écriture à votre repository GitHub.
*   Dans **Token description**, mettez `Plugin Wordpress` (vous pouvez mettre ce que vous voulez, c'est pour vous en rappeler).
*   Dans **Select scopes**, ne laissez de cocher que `public_repo` si votre repository est en **Public**, cochez aussi `repo` s'il est en **Private**. Vous pourrez changer ça par la suite.
*   Cliquez sur **Generate token**, et mettez le dans un coin, nous allons nous en servir par la suite.

### Dans le panel administation de votre site Wordpress

*   Allez dans `Réglages &gt; GitHub Sync`.
*   Dans le champ **Repository**, donnez le nom du repository que nous venons de créer (avec votre nom de compte GitHub) : `jlevallois/karganys.fr` dans mon cas.
*   Dans le champ **Oauth Token**, rentrez le **token** que nous venons de générer.
*   Dans le champ **Webhook Secret**, rentrez un mot de passe unique. Celui-ci va permettre à GitHub d'avertir votre site en cas de mise à jour de votre repository. Comme ça les articles se mettront automatiquement.
*   Copiez le lien à droite de **Webhook callback**, nous allons le donner à GitHub ainsi que votre **Webhook Secret**.
*   Cliquez sur **Enregistrer les modification**.

### Sur votre compte GitHub

*   Retournez sur votre **repository** nouvellement créé.
*   Allez dans les paramètres de repository : `Settings &gt; Webhooks &amp; services`
*   Cliquez sur **Add webhook**
*   Dans le champ **Payload URL**, collez le lien de votre **Webhook callback**
*   Dans le champ **Secret**, collez votre mot de passe unique **Webhook Secret**
*   Dans le champ **Content Type**, vérifiez bien que ce soit `application/json`
*   Cliquez sur **Add webhook**.

Et voilà. Si votre repository a été synchronisé, vous devriez voir un dossier **_posts** contenant tous vos articles. Ces articles sont formatés en Markdown, avec un peu de **YAML** en entête pour être compatibles avec Wordpress.

## Utilisation

Ok, et maintenant ? Comment on fait. Le problème, c'est surtout cette entête qu'on ne peut pas trop connaître à l'avance, notamment l'ID ou l'URL. C'est pour cela que j'ai créé un dossier **_drafts** sur le repository où j'écris le contenu des articles. Je l'enregistre au format Markdown (`.md`) dans ce dossier, avec un nom temporaire.

Une fois celui-ci fini, je créé un article sur wordpress où j'y définis toutes les méta data : titre, tag, catégories, etc.

Ensuite, je publie l'article vide. Cela va créé un nouveau fichier .md dans le dossier **_posts** de votre repository (`/_posts/date-nom-de-l-article.md`) contenant ces précieuses metadonnées que je dois copier.

Enfin, je colle ces métadonnées en entête de mon article. Il ne reste plus qu'à le déplacer dans le dossier **_posts** en ayant supprimé l'ancienne copie.

Et voila !

* * *

**Source :** [Alda Marteau-Hardi (Aldarone)][8]

 [1]: https://github.com/DGtal-team/DGtal
 [2]: https://github.com/DGtal-team/DGtalTools
 [3]: https://github.com/dcoeurjo/ICTV
 [4]: https://github.com/jlevallois/PhD-Thesis
 [5]: https://stackedit.io/editor
 [6]: https://wordpress.org/plugins/wp-github-sync/
 [7]: https://github.com/settings/tokens/new
 [8]: http://aldarone.fr/ecrire-avec-vim-pusher-sur-github-publier-sur-wordpress/