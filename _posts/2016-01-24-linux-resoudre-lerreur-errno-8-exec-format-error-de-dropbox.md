---
ID: 1094
post_title: 'Linux: Résoudre l&rsquo;erreur &laquo;&nbsp;[Errno 8] Exec format error&nbsp;&raquo; de Dropbox'
author:
  - Jérémy Levallois
post_date: 2016-01-24 16:49:50
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/systemes-d-exploitation/ubuntu/linux-resoudre-lerreur-errno-8-exec-format-error-de-dropbox/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";s:4:"1099";s:11:"_thumb_type";s:5:"thumb";}'
layout_key:
  - ""
post_slider_check_key:
  - "0"
---
Je viens de me rendre compte sur ma machine sous Linux Mint que [Dropbox][1] n'était plus lancé. Lorsque j'ai essayé de le lancer à la main avec la ligne de commande suivante : `dropbox start -i`, j'ai eu le message d'erreur suivant :

`Starting Dropbox...Traceback (most recent call last):
  File "/usr/bin/dropbox", line 1535, in <module>
    ret = main(sys.argv)
  File "/usr/bin/dropbox", line 1524, in main
    result = commands[argv[i]](argv[i+1:])
  File "/usr/bin/dropbox", line 1395, in start
    if not start_dropbox():
  File "/usr/bin/dropbox", line 732, in start_dropbox
    stderr=sys.stderr, stdout=f, close_fds=True)
  File "/usr/lib/python2.7/subprocess.py", line 710, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1327, in _execute_child
    raise child_exception
OSError: [Errno 8] Exec format error`

## Comment résoudre le problème

*   Supprimez le répertoire d'installation de Dropbox (ne vous inquiétez pas, vos documents synchronisés ne sont pas dans ce dossier) : `rm -rf ~/.dropbox*`
*   Lancez Dropbox : `/usr/bin/dropbox start`
*   Vous obtiendrez le message suivant : `Starting Dropbox...
The Dropbox daemon is not installed!
Run "dropbox start -i" to install the daemon`
*   Lancez le deamon de Dropbox : `/usr/bin/dropbox start -i`, vous obtiendrez le message suivant : `Starting Dropbox...Done!`

Et voilà !

* * *

**Source :** [Geeks with Blogs][2]

 [1]: https://www.dropbox.com/
 [2]: http://geekswithblogs.net/jkhines/archive/2012/12/25/dropbox-fails-with-oserror-errno-8-exec-format-error.aspx