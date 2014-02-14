---
layout: post
title: On cheese shops and ex-parrots
permalink: cheese-shops-and-ex-parrots
published: true
categories:
- programming
- python
- technology
---

The astute observer or reader will notice that I've only had two
previous entries filed under "programming" -- both of which have dealt
with Python. 

I feel it's worth expounding upon why I'm more stuck on Python than a
snake charmer (haw haw). 

1.) Simplicity of syntax

I've remarked before that writing Java is like filling out forms in
triplicate. You have to have all your boilerplate correct before you can
get to "the good stuff", and even the good stuff is often unnecessarily
verbose (though not in a good way).

For instance, the following Java code is necessary to swap the values of
two variables:

    String foo1 = "one";
    String foo2 = "two";
    String tmp = foo1;
    foo1 = foo2;
    foo2 = tmp;
{: .prettyprint .linenums:1}

Just to swap two variables, you've got to create a temporary variable,
which means you've got to know the types of the variables beforehand
(unless you want to get clever with generics) so that you can swap them.

Meanwhile, this works in Python:

    foo1 = "one"
    foo2 = "two"
    (foo1, foo2) = (foo2, foo1)
{: .prettyprint .linenums:1}

Done. In fact, we can even shorten that a bit by declaring the variables
with `(foo1, foo2) = ("one", "two") `{: .prettyprint}

Little things like variable unpacking save time and (arguably) memory
usage and Generic-typing headaches.

2.) from internet import \*

Okay, so maybe this is actually two (or three) points. But I'll hit them
both.

First, Python is like Perl in that if it exists, there is a very high
chance that there's a Python module for it. This is because python
modules are very easy to write. You just create a single file, toss in
some functions or classes, and import it using the filename. More
complex modules can be handled using a folder with an empty file called
\_\_init\_\_.py (allowing statements like `import foo.bar`{:
.prettyprint})

The next point (or two) is aliasing of imports. Using the `from foo
import bar`{: .prettyprint} syntax brings bar into the global namespace,
so that rather than having to deal with "foo.bar()" everywhere, you can
just use "bar()". Further, you can `import foo.bar.baz.who.what.why as
foowhy`{: .prettyprint} and everywhere afterwards refer to it as
"foowhy" without having to worry about the fully-qualified name (while
still keeping it out of the global namespace to avoid any namespace
collisions)

 
3.) An object-oriented interpreter

Python is an interpreted language. You can stop cringing -- it's not
that slow. (To be totally honest, it does some automatic compilation on
each successful first run after an alteration to the original source.)
But Python is also a powerful object-oriented language. What this means
is that you can test the individual aspects of a class just by importing
the source from the interpreter. You can even test changes within the
interpreter without altering the source (granted, if the change works,
you'll need to alter the source). It's a little arduous to
monkeypatch-rewrite a longer function, but for quick fixes or additions,
it's a useful attribute of the language.

 

4.) It's pretty.

This one is a bit more subjective, because beauty, as they say, is in
the eye of the beholder. Some people really like writing very terse,
implicit ruby that forces you to read between the lines.

I like the idea of "pythonic" code. See, every language brings with it
its own mindset and ethic.  Perl carries the idea that "there's more
than one way to do it". Java emphasizes absolute standardization and
portability. Ruby has the "Ruby Way" (about which there seems to be a
great deal of disagreement amongst the various authors I read).

"Pythonic" code emphasizes using the language's to be as clear as
possible; "explicit is better than implicit." Yes, you can complain that
whitespace is significant. But would you really ever leave your Java
code unindented? Humans naturally understand that a block quote -- an
indented paragraph -- is intended to be separated from the surrounding
text. So 

    for object in list_of_objects:
        object.do_something()
    do_something_after_loop()
{: .prettyprint .linenums:1}

should not be too great a stretch for our understanding. Even the
iterator is simple -- rather than relying on obscure syntax like
Java's `for (Thing thing : things) { //do something }`{: .prettyprint}
you can use syntax that matches the way you speak. 

This combination of explicit yet concise syntax extends to other areas,
like keyword arguments. For instance, consider the following code
snippet:

    def foo(one="bar", two="baz", three="bonk"):
        return one + " " + two + " " + three
{: .prettyprint .linenums:1}

After declaring this method, any of the following function calls are
valid:

    foo("who", "what", "when")
    # returns "who what when"
    foo("who")
    # returns "who baz bonk"
    foo("who", three="when")
    # returns "who baz when"
    foo(two="what")
    # returns "foo what bonk"
{: .prettyprint .linenums:1}

In this way, you can be even more explicit than in other languages --
you can specify which values match with which parameters, regardless of
position. This makes Python projects actually *more* forward-compatible in the event of future changes to argument
position (which really you ought not to be doing, but there it is.)

 

And now for something completely different.

Of course, as you may have figured out from the title, Python is named
for the famous sketch comedy group Monty Python, and much of that sense
of humor has carried over into the Python community. I don't think it's
too great a leap to say that the very same sense of humor and satire of
programming itself is the source from which most ideas of "pythonic
code" flow. Where Perl has cpan, Python has the "cheese shop"
(admittedly better known by the less humorous name "PyPI" or "Python
Package Index"). Tutorials often deviate from "hello world" to revolve
around parrots who may or may not be pining for the fjords (and other
such miscellany).  All these things combine to form a community that
doesn't take itself quite as seriously as others, making for a more
pleasant atmosphere for newbies overall.

 

So give it a shot -- if you like it, great. If you don't, no worries --
it's not like I'm going to hunt you down and attack you with a banana.
[Still, it might not hurt to be prepared.][1]



[1]: http://www.youtube.com/watch?v=piWCBOsJr-w
