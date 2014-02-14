---
layout: post
title: import antigravity
permalink: import-antigravity
published: true
categories:
- programming
- technology
---

Two days ago, with the semester finally over and things quieting down
(by and large) for a bit, I opted to finally endeavor to learn Django, a
Python web framework.

Today, I've replaced a rather large PHP application with a complete
rewrite in Django, and load times have improved roughly sixfold.

 

That PHP application is this blog! Django is simple enough (to anyone
with Python experience) that, while still in the process of learning it,
I was able to replicate a site that had taken me a few weeks to build in
PHP.  
  

Granted, the design process was done, so there was no time spent on
that.  
 And I was able to more or less just drop in a pre-made module for rich
text editing in the administration area, so that work was also done for
me.  
  

There are a lot of things Django does very right -- the templating
system is phenomenal (custom blocks make life significantly easier) and
the baked-in admin tools are *very* impressive. It manages your database
in a well-normalized fashion for you. Added an object/model? No problem
-- "python manage.py syncdb" and you're done. And it's *fast*. Did I
mention that it's fast?

And while I haven't mastered Django just yet, there are a couple of
things about it that take a good bit of getting used to. For instance,
it requires FastCGI and custom htaccess rewriting rules on most
webhosts. Any static media files (external stylesheets and javascript
files, images, etc) live in a different location on the webserver than
the Python that drives your site or application (though with some
symbolic links, this is less of an issue). And the brilliant "syncdb"
command of which I've already made mention is great -- except that it
doesn't ever generate an "Alter Table" statement, which means that any
alterations to existing models aren't detected.

 

Even with these small issues, it's still actually *an enjoyable
experience* to use Django. Programming is fun again! It's a whole
new world up here.

