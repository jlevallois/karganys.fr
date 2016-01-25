---
ID: 1121
post_title: 'Linux: Résoudre l&rsquo;erreur &laquo;&nbsp;[Errno 8] Exec format error&nbsp;&raquo; de Dropbox'
author: Jérémy Levallois
post_date: 2016-01-24 16:49:50
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/2016/01/24/linux-resoudre-lerreur-errno-8-exec-format-error-de-dropbox-2/
published: true
---
<p>Je viens de me rendre compte sur ma machine sous Linux Mint que <a href="https://www.dropbox.com/">Dropbox</a> n'était plus lancé. Lorsque j'ai essayé de le lancer à la main avec la ligne de commande suivante : <code>dropbox start -i</code>, j'ai eu le message d'erreur suivant :</p>

<p><code>Starting Dropbox...Traceback (most recent call last):
  File "/usr/bin/dropbox", line 1535, in &lt;module&gt;
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
OSError: [Errno 8] Exec format error</code></p>

<h2>Comment résoudre le problème</h2>

<ul>
<li>Supprimez le répertoire d'installation de Dropbox (ne vous inquiétez pas, vos documents synchronisés ne sont pas dans ce dossier) : <code>rm -rf ~/.dropbox*</code></li>
<li>Lancez Dropbox : <code>/usr/bin/dropbox start</code></li>
<li>Vous obtiendrez le message suivant : 
<code>Starting Dropbox...
The Dropbox daemon is not installed!
Run "dropbox start -i" to install the daemon</code></li>
<li>Lancez le deamon de Dropbox : <code>/usr/bin/dropbox start -i</code>, vous obtiendrez le message suivant : 
<code>Starting Dropbox...Done!</code></li>
</ul>

<p>Et voilà !</p>

<hr />

<p><strong>Source :</strong> <a href="http://geekswithblogs.net/jkhines/archive/2012/12/25/dropbox-fails-with-oserror-errno-8-exec-format-error.aspx">Geeks with Blogs</a></p>