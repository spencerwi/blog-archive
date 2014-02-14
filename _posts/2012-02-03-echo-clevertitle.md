---
layout: post
title: echo "$clevertitle"
permalink: echo-clevertitle
published: true
categories:
- linux
- technology
---

It is no secret that I am a nerd. In fact, I'm one of the worst kinds of
nerds: a *linux user*. 

People think of linux and think of hackers and people in basements on
command-lines moving zeroes and ones around. But it's not all that bad!
You can have an [easy-to-use, aesthetic setup][1] on linux (disclaimer:
that's my laptop).

 

And, best of all, you can get things done -- often much more
quickly/efficiently than on Windows.

In using linux, I've made a few observations on how to get the most out
of it.

 

First,

1. Learn to script things

At work, I occasionally get a bit of grief (in good fun, of course) from
my coworkers my somewhat addictive tendency to "script" and automate
tasks. My philosophy is that I am willing to step through process of a
task two times by hand, but the third time I'll automate it.

This means gaining some familiarity with a scripting language, like
python, ruby, or even just bash (the default command-line program for
most linux versions). My weapon of choice is python, because it "glues"
things together nicely, but your preference may vary. In any case, you
want to be comfortable enough with it that you can put quickly together
a script that you write once and can reuse over and over again.

The time and mental bandwidth you will save in the future will be well
worth it when you realize that instead of having to focus in on once
again doing the same repetitive task, you can put the majority of the
burden on the computer to do it for you.

 

Which, of course, leads me to point #2:

2. Learn how to use the terminal (well)

Yes, I know I said it's not all command-lines. But, well, sometimes the
command-line is just *better*. 

For example, let's say I keep a bunch of files organized by year and
then month (by number, so January is 1, February is 2, etc), but I want
to move all of the files for 2011 into one folder.

Now, I could open up a file browser (think "My Computer" for those more
familiar with Windows) go into the 2011 folder, open up another file
browser to the place I want to put all the files, and for each month, go
into the folder, select all the files, click and drag them into the new
folder, go back out, go into the next month......and so on.

Or I could do this:

    for x in {1..12}
    do
        mv $x/* /path/to/new/folder/
    done
{: .prettyprint .linenums:1}

and then turn my attention to some other task.

When you use the command-line, you're using a programming language that
can itself use all of your programs! This gives you tremendous
versatility -- why not make use of it?

 

3. Stay organized

This one can fall through the cracks sometimes, but it goes a long way
to make life easier.

Decide on a consistent layout for your home folder (and whatever other
directories you use frequently) and stick to it. That way you don't have
to remember whether you put that pdf homework assignment you downloaded
into "tmp", "downloads", "documents", or "homework" -- instead you can
go to one place and find it.

 

And speaking of finding things....

4. Don't *just* grep, do something!

No, I haven't suddenly lapsed into Portuguese, nor is "*grep*" a
character from Star Wars.  Grep is a tool that searches through files
for words or patterns of text. For example, if I'm looking through all
of my class notes for anything about the class project, I might do this:

    grep -i "Project" /home/spencer/class_notes/*
{: .prettyprint .linenums:1}

What this says is "look for the word Project in all of the files in my
class\_notes folder" (the -i means case-insensitive, so the word "
Project" can be uppercase *or* lowercase).

Now, this is not all that big a deal, you might say, but here's where I
come to my point: sure, now, I have all the notes I jotted down with the
words "Class Project" in that folder. But I want to *do something with
them*. What's happened here is sort of like asking someone "hey, have
you seen my keys?" and having them just respond "yep." 

This is where point #2 comes in. In linux, you can chain together
commands using *pipes.* Pipes feed the output of one command into
the input of another. So using a pipe, I might send my notes into a text
editor:

    grep -i "Project" ~/spencer/class_notes/* | editor "project_notes.txt"
{: .prettyprint .linenums:1}

Or, I could skip a pipe altogether and just send the notes straight into
a file, using the "&gt;" or "&gt;&gt;" operators:

    grep -i "Project" ~/spencer/class_notes/* >> "project_notes.txt"
{: .prettyprint .linenums:1}

Now my project notes are ready to email around to the rest of my project
teammates.

An important note about "&gt;" and "&gt;&gt;"\: if you just use "&gt;",
you'll erase the contents of an existing file. So if project\_notes.txt
had something in it before, we erase it before putting our notes into
it. If you *don't* want to erase the contents, use "&gt;&gt;",
which will add the notes (or whatever else) to the end of the existing
file contents.

Remember: don't *just* grep, do something!



[1]: http://ninjatricks.net/upload/img/desktops/black_orange_busy.png
