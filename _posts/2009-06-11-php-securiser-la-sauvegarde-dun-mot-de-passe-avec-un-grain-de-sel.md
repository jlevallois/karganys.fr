---
ID: 13
post_title: '[PHP] Sécuriser la sauvegarde d&#039;un mot de passe avec un grain de sel'
author: Jérémy Levallois
post_date: 2009-06-11 19:08:16
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/programmation/php/php-securiser-la-sauvegarde-dun-mot-de-passe-avec-un-grain-de-sel/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
---
Premier "vrai" article, celui-ci concerne la sécurité en PHP ( mais peut-être appliqué dans d'autres langages ) d'accès à un compte.
Imaginons que vous ayez un site communautaire, donc vous devez avoir des utilisateurs. Pour cela vous devez donner la possibilité de créer des comptes, pour chaque utilisateur, et donc stocker ces informations quelque part ( BDD par exemple ).
Et qui dit stockage d'informations, dit risque de subtilisation par quelqu'un non autorisé ( aucun système n'est parfait à 100% ), ce qui peut devenir gênant s'il s'agit d'un mot de passe et que l'utilisateur utilise le même sur plusieurs sites.

Pour contrer cela, nous devons rendre la tâche la plus difficile possible à ces voleurs. Au lieu de sauvegarder dans notre BDD les mots de passe des utilisateurs en clair, nous allons utiliser le <strong>hachage cryptographique</strong>.

Le hachage cryptographique calcule l'empreinte numérique d'une donnée. Par exemple, l'empreinte numérique du mot <strong>Karganys</strong> est <strong>2a29d47bc7a5094f18db6cbc0c56ce21</strong> en utilisant l'algorithme de hachage MD5.
Pour obtenir cette empreinte numérique, on effectue une série d'opérations à partir de la donnée d'entrée.
Pourquoi ne pas faire les opérations inverses alors, pour arriver à notre donnée de départ, comme le <strong>+</strong> et le <strong>-</strong>, le <strong>*</strong> et le <strong>/</strong> ? Et bien parce que ces algorithmes perdent des informations. Ainsi nous pouvons difficilement faire l'opération inverse sans ces informations ( Par exemple, si on arrondi 2/3 à deux chiffres après la virgule, on obtient 0.67. Mais 0.67*3 = 2.01, ce qui est différent de 2 ).

Cette empreinte numérique est censé être unique, c'est d'ailleurs une des remise en cause de la validité d'un hachage cryptographique : s'il y a collision, c'est à dire que de deux données résulte la même empreinte numérique, le hachage n'est plus considéré comme fiable ( d'ailleurs le hachage MD5 est assujetti à de nombreuses collisions, c'est pour cela qu'il faut l'éviter au maximum ). Le hachage doit donc utiliser des opérations injectives ( lorsque tout élément de l'ensemble d'arrivée a au plus un antécédent dans l'ensemble de départ ).

Le but d'un algorithme de hachage cryptographique n'est pas de ne jamais pouvoir être décrypté car c'est impossible, mais que la tâche pour créer l'empreinte soit la plus courte possible, et que le décryptage de cette empreinte soit la plus fastidieuse et longue possible. Si une empreinte peut être décrypter en 1 mois, et que l'on change cette empreinte tous les 15 jours, nous aurons toujours une longueur d'avance.
Mais ceci dépend de l'avancée de la cryptanalyse, et du matériel qui devient plus rapide que jamais.

Revenons à notre cas, nous voulons sauvegarder les mots de passe des membres dans notre BDD, ainsi si le mot de passe est <strong>Karganys</strong>, nous sauvegarderons dans la base son empreinte <strong>2a29d47bc7a5094f18db6cbc0c56ce21</strong> avec l'algorithme MD5. Ainsi à chaque connexion, nous devons calculer l'empreinte du mot de passe renseignée par l'utilisateur, et le comparer avec celui sauvegardé dans la base. S'il est le même, le mot de passe est correct ( vous comprenez désormais pourquoi un hachage avec collisions n'est plus fiable ? ).

On pourrait penser que nos informations sont bien sécurisés dans notre BDD si quelqu'un parvient à y entrer, mais en fait non ! Plusieurs applications comme <a href="http://www.authsecu.com/decrypter-dechiffrer-cracker-hash-md5/decrypter-dechiffrer-cracker-hash-md5.php" target="_blank">celle-ci</a> permettent d'effectuer une attaque dite de <strong>brute force</strong> sur notre empreinte, c'est à dire qu'ils génèrent une liste de mots ( où bien utilisent un dictionnaire, qui est un recueille de mots courants ), calculent leur empreinte et comparent avec notre empreinte. Autant vous dire qu'un mot de passe du style 'aaa' est beaucoup plus simple à trouver qu'un mot de passe du style 'cz'@]IhgLDJq`$@W"CG`'.
Ainsi, à partir de <strong>2a29d47bc7a5094f18db6cbc0c56ce21</strong> nous trouvons très rapidement <strong>Karganys</strong>, notre manœuvre de sécurisation a échouée.

Rajoutons donc une protection contre ce type d'attaque, grâce à un grain de sel.
Il s'agit en fait de la technique dite de "salage", qui consiste à rajouter à votre mot de passe de départ certaines informations que vous seul connaissez.

<pre lang="php">function md5_p($password)
{
     $val = 84675164;
     $val2 = 4794546;
     return md5(md5($val.$password.$val).md5($val2.$val));
}
</pre>

Ainsi, si quelqu'un subtilise l'empreinte numérique finale ( ici <strong>0ca6a75884d83652db776607fc77f2df</strong> ), il faut qu'il connaisse la suite d'opérations et de valeurs que nous avons usées, autant dire très difficile sans avoir le code source de la page. Cette solution n'est pas 100% sécurisé contre les attaques, mais améliore quand même de façon considérable celle de départ, et ce dans un temps tout à fait raisonnable !

J'ai utilisé dans cet article l'algorithme de hachage cryptographique MD5 pour vous montrer à quel point il est à proscrire au vu des applications qu'il existe pour décrypter son empreinte facilement et rapidement. D'autres sont disponibles en PHP, dont l'algorithme <a href="http://www.php.net/manual/fr/function.sha1.php" target="_blank">SHA1</a> disponible directement dans l'API PHP.

J'espère que ce premier article vous a plus, j'ai essayé d'être concis car les fonctions de hachage cryptographique feront l'objet d'un article dédié, tout en expliquant un peu comment ça fonctionne.
Je suis ouvert à toutes critiques que vous pouvez me laisser en commentaire ou par email