---
ID: 217
post_title: Le corps humain en balises XML et PHP
author: Jérémy Levallois
post_date: 2010-08-08 17:58:44
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/programmation/php/le-corps-humain-en-balises-xml-et-php/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
---
<div class="wp-caption alignnone" style="width: 250px;"><a href="http://www.flickr.com/photos/marcogomes/3024603255/"><img src="http://farm4.static.flickr.com/3156/3024603255_0a54d2be39_m.jpg" title="Nath Valverde" alt="Nath Valverde" width="240" height="180" /></a><p class="wp-caption-text"><a href="http://www.flickr.com/photos/marcogomes/3024603255/">Nath Valverde</a> by <a href="http://www.flickr.com/photos/marcogomes/">Marco Gomes</a></p></div>


Que serait le code source du corps humain s'il était fait avec des balises XML et du PHP ?
Voici la réponse :

<pre lang="php"><human>
        <head>
                <hair />
                &lt;br />
                <ear align="left" />
                <sight>
                        <eye align="left" />
                        <eye align="right" />
                </sight>
                <ear align="right" />&lt;br />
                <nose />
                &lt;br />
                <form action="aliment.php">
                        <mouth />
                </form>
                &lt;br />
                <neck height="8cm" />
        </head>
        <body>
                <tshirt style="background-color: #000;">
                        <arm align="left">
                                <hand />
                        </arm>
                        <chestarea>
                                < ?php
                                if ($sex=='female')
                                {
                                        echo '<tit align="left" /><tit align="right" />';
                                }
                                else
                                {
                                        echo '<nipple align="left" /><nipple align="right" />';
                                }
                                ?>
                        </chestarea>
                        <arm align="right">
                                <hand />
                        </arm>
                        &lt;br />
                        <tummy>
                                <bellybutton />
                        </tummy>
                </tshirt>
                <pants size="short">
                        <underwear>
                                < ?php
                                include 'private.php';
                                ?>
                        </underwear>
                        <leg align="left" />
                        <leg align="right" style="tattoo-image: url(img/love_mom.gif);" />
                </pants>
                <sneaker align="left" class="nike">
                        <foot />
                </sneaker>
                <sneaker align="right" class="nike">
                        <foot />
                </sneaker>
        </body>
</human></pre>

Source : <a href="http://www.alvago.com.ar/2010/04/20/the-human-body-in-html-and-php/" target="blank">Alvago Go!</a>