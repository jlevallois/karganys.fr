---
ID: 1169
post_title: '[GPG error] Résoudre l&rsquo;erreur &laquo;&nbsp;The following signatures couldn&rsquo;t be verified because the public key is not available&nbsp;&raquo;.'
author: Jérémy Levallois
post_date: 2016-02-09 14:59:27
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/ubuntu/gpg-error-resoudre-lerreur-the-following-signatures-couldnt-be-verified-because-the-public-key-is-not-available/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";s:4:"1171";s:11:"_thumb_type";s:5:"thumb";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
## Problème
En mettant à jour mon Linux (`sudo apt-get update`), j'obtiens cette erreur :

```
W: GPG error: http://repo.steampowered.com precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F24AEA9FB05498B7
```

Dans mon cas, le problème provient du repository de [Steam](http://store.steampowered.com/). La clef publique permettant d'identifier le repository contenant les paquets n'est plus valide, et nécessite d'être mis à jour pour continuer à utiliser le repository.


Si vous avez le même message d'erreur (les seules différences peuvent être le lien `http://repo.steampowered.com` et la clef `F24AEA9FB05498B7`, car dans mon exemple c'est lié à Steam, mais dans votre cas ça peut être d'un autre repository), voici comment résoudre le problème.

## Solution

### Identifier le repository

La première étape sera d'identifier le repository qui pose problème. Généralement, le lien (`http://repo.steampowered.com` dans mon cas) dans le message vous donne assez d'indication pour le déterminer.

### Trouver la nouvelle clef publique

Pour déterminer la nouvelle clef publique, il y a deux solutions : la plus simple et une plus compliquée.

#### La solution simple

La solution la plus simple consiste à se rendre sur la page du repository. Supposons que votre problème vienne du repository de [Zeal](https://zealdocs.org/), rendez-vous sur la page du repository [https://launchpad.net/~jerzy-kozera/+archive/ubuntu/zeal-ppa](https://launchpad.net/~jerzy-kozera/+archive/ubuntu/zeal-ppa).

La nouvelle clef devrait y être présent. Sur les pages Launchpad.net, il faut cliquer sur "Technical details about this PPA" et vous verrez "Signing key". La clef se situe après `1024R/`, en rouge sur la capture d'écran suivante :

![Clef publique repository](http://www.karganys.fr/wp-content/uploads/2016/02/Clef-publique-repository.png)

#### La solution compliquée

Si jamais le fournisseur du repository ne diffuse pas clairement la clef publique du repository, vous pouvez toujours la chercher vous mettre sur le serveur de clefs d'Ubuntu : [http://keyserver.ubuntu.com/](http://keyserver.ubuntu.com/).

Dans **Search String**, rentrez le nom du repository (**steampowered** dans mon cas). Si aucun résultat n'apparait, essayez d'autres mots-clefs (c'est pour ça que c'est compliqué, il faut trouver les bons mots-clefs).

- Si vous obtenez un seul résultat : vous avez de la chance. La clef est visible après `pub 2048R/` (ou `pub 1024R/`)

  ![Steam public key](http://www.karganys.fr/wp-content/uploads/2016/02/Steam-public-key.png)

- Si vous obtenez plusieurs résultats : il va falloir trouver quelle est le bon repository. Ça dépend du repository qui pose problème chez vous.

  ![Steam public key 2](http://www.karganys.fr/wp-content/uploads/2016/02/Steam-public-key-2.png)

  - En lisant les **uid** des résultats, vous pourrez éliminer plusieurs choix. Dans notre exemple, nous pouvons éliminer **Valve Steam OS**, **Valve builder archive**.

  - Éliminez aussi, si possible, les clefs signées par des utilisateurs. Dans notre exemple, nous pouvons éliminer **Kevin Faltisco (www.steampowered.com)** et la clef de **Ramon Rosin**.

  - Avec ce jeu de déduction, il ne reste plus qu'une clef : **B05498B7**.

Vous l'aurez deviné, cette solution est beaucoup plus compliquée, et nécessite un peu de recherche.

### Utiliser la nouvelle clef

Une fois la clef récupérée, la suite est assez simple. Rentrez la commande suivante pour ajouter la nouvelle clef à votre liste de clefs (en changeant **VOTRENOUVELLECLEF** par la clef) :

```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys VOTRENOUVELLECLEF
```

puis mettez à jour les repository :
```bash
sudo apt-get update
```

Vous ne devriez plus avoir l'erreur.

* * *

**Testé sur :** Linux Mint 17.3