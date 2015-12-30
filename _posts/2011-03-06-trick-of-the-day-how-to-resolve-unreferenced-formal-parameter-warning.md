---
ID: 569
post_title: 'Trick of the Day : How to resolve &laquo;&nbsp;Unreferenced formal parameter&nbsp;&raquo; warning ?'
author: Jérémy Levallois
post_date: 2011-03-06 12:09:03
post_excerpt: ""
layout: post
permalink: >
  http://www.karganys.fr/programmation/c-cpp/trick-of-the-day-how-to-resolve-unreferenced-formal-parameter-warning/
published: true
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
---
<div class="wp-caption alignnone" style="width: 250px;"><a href="http://www.flickr.com/photos/chiropractic/5500986886/"><img src="http://farm6.static.flickr.com/5059/5500986886_335fb8b046_m.jpg" title="Warning Restricted Area LAS" alt="Warning Restricted Area LAS" width="240" height="160" /></a><p class="wp-caption-text"><a href="http://www.flickr.com/photos/chiropractic/5500986886/">Warning Restricted Area LAS</a> by <a href="http://www.flickr.com/photos/chiropractic/">planetc1</a></p></div>

Hi !

If you compile your project in Warning Level 4 /W4 (Project > Properties > C/C++ > General > Warning Level : Level4 (/W4) in Visual Studio), you have probably seen this warning :

<blockquote><strong>Warning	2	warning C4100: 'var' : unreferenced formal parameter</strong></blockquote>

You think your code hasn't error (like unused stack variable for example), and you don't know why this warning is here ? It might be some <strong>unused function parameters</strong>.

Example :
<pre lang="c++">void callAWarning(int a)
{
	//some stuff without a variable
}
</pre>

And when you compile :
<code>Warning	2	warning C4100: 'a' : unreferenced formal parameter</code>

Now how to resolve this warning ?
Simply by using the macro <strong>UNREFERENCED_PARAMETER()</strong>.
 
<pre lang="c++">void callAWarning(int a)
{
	UNREFERENCED_PARAMETER ( a );
	//some stuff without a variable
}
</pre>


PS: If you have the error : "<strong>Error	2	error C3861: 'UNREFERENCED_PARAMETER': identifier not found</strong>", just add this #define into your project :
<pre lang="c++">#define UNREFERENCED_PARAMETER	( P ) 	   (void)(P)</pre>


PS2 : The default warning level in Visual Studio is Warning Level 3, but I recommend you to use Warning Level 4 for your projects, because it's the more strict compilation level and allow you to track any mistakes, as MSDN says :

<blockquote>For a new project, it may be best to use /W4 in all compilations. This will ensure the fewest possible hard-to-find code defects.</blockquote>

Source : <a href="http://msdn.microsoft.com/en-us/library/thxezb7y.aspx">MSDN</a> | <a href="http://linux.dell.com/libsmbios/main/gcc_8hpp.html">DELL</a>