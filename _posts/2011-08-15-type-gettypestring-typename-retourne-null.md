---
ID: 713
post_title: >
  Type.GetType(string typeName) retourne
  null
author: Jérémy Levallois
post_date: 2011-08-15 20:49:42
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/programmation/c-sharp-xna/type-gettypestring-typename-retourne-null/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
---
J'ai eu un soucis dans un de mes projets en C# sur les <strong>Type</strong>.
C# vous offre la possibilité de passer d'une chaîne de caractères à un Type, avec la fonction <a href="http://msdn.microsoft.com/en-US/library/system.type.gettype.aspx" title="MSDN">Type.GetType(string typeName)</a>
<pre lang="C#">Type.GetType("System.Int32"); // Retourne le type d'un int</pre>

Jusqu'à là, pas de soucis. Sauf que, quand on essaie avec des classes customs et plusieurs sous-projets, et bien ...
<pre lang="C#">namespace MonNamespace
{
	// ...
	Type.GetType("MonAutreNamespace.MaClasse"); // Retourne null
	// ...
}</pre>

En fait, la chaîne de caractères doit contenir le nom de l'assembly où est inscrit la classe à chercher. Par défaut, si rien n'est spécifié, il va chercher dans l'assembly de l'appelant, puis dans l'assembly System (mscorlib.dll).
S'il s'agit d'une classe du framework .NET, vous pouvez le <a href="http://blogs.msdn.com/b/haibo_luo/archive/2005/08/21/454213.aspx" title="Haibo Luo's blog">récupérer "facilement"</a>.

Dans mon cas, il s'agissait de classe perso, beaucoup plus dur à récupérer l'assembly (et surtout je ne voulais pas de valeur écrit en dur dans mon code). Du coup, un bête
<pre lang="C#">typeof(MonAutreNamespace.MaClasse); // retourne le Type de MonAutreNamespace.MaClasse</pre>
fait très bien l'affaire.

PS : D'ailleurs, un truc qui m'aurait fait gagné quelques minutes de debugging aurait été d'utiliser la surcharge <a href="http://msdn.microsoft.com/en-us/library/c5cf8k43.aspx" title="MSDN">Type.GetType(string typeName, true)</a> qui déclenche une erreur dès que le Type n'a pas été trouvé.