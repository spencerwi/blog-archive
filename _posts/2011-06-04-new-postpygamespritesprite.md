---
layout: post
title: ! 'new Post(pygame.sprite.Sprite):'
permalink: new-postpygamespritesprite
published: true
categories:
- programming
- technology
---

Recently I've been teaching myself game programming with python and
pygame.

Most things are greatly simplified by python and pygame, but not
everything. Some of the harder things I've had to learn are how to use
[Bresenham's Algorithm][1] for field of vision. In a nutshell, it
resolves the difference between a direct line between two points
(theoretically of zero width) and something made up of pixels of a fixed
width (or in my case, tiles of a fixed size.) I can give  Bresenham's
algorithm two points and get back a list of the squares in a grid that
will form the shortest line between those two points. From there, I can
work through that list, checking for something that obscures the line of
sight between those two points, and stop as soon as I find it (throwing
out anything that can't be seen due to the obstruction.)

Another difficulty still remains ahead and unsolved: creating art and
music and designing levels. See, for now I'm building little demos to
teach myself each new concept (incrementally introducing new things into
my existing "ecosystem" one at a time), but I'm working towards a
smallish game I already have in mind. 

At work the other day, my coworkers and I were discussing any video
games we've recently played, and one coworker mentioned that her husband
had picked up "Ninja Garden" -- she meant "[Ninja Gaiden][2]", of
course, but the idea of "Ninja Garden" was just too amusing to pass up.
So that's where I've started now.

My idea is this: you are a ninja, sneaking in and about a guarded
garden. You have to sneak past the guards to a certain level goal (you
see now why I needed to implement field of vision correctly). 

 

This requires me to have the artistic ability to come up with background
music (sound effects are not a problem, I've got an awesome little tool
called [sfxr][3] that simplifies that significantly) as well as all the
images in the game. Currently, my demos have all involved a random
cheesy series of images I found on the internet for the level
backgrounds, triangles for the enemies, and this friendly toaster I
threw together in about 20 minutes with a bizarre frame of mind.

This is the "fun" part -- I've made the game act right, now I have to
make the game look and sound right.

 

This won't be pretty.



[1]: http://en.wikipedia.org/wiki/Bresenham's_line_algorithm
[2]: http://en.wikipedia.org/wiki/Ninja_Gaiden
[3]: http://www.drpetter.se/project_sfxr.html
