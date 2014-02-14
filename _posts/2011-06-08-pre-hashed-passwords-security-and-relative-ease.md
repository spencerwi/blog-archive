---
layout: post
title: Pre-hashed passwords for security and (relative) ease
permalink: pre-hashed-passwords-security-and-relative-ease
published: true
categories:
- security
- technology
---

Let's be honest here: most of us have maybe two or three passwords of
varying degrees of "strength". The fact of the matter is that multiple
distinct strong passwords are hard to recall and remember (or to
remember which goes where). In fact, in some cases, having too many
distinct strong passwords can be a bad thing -- many higher-security
websites (like banking sites) will lock your account after several
failed login attempts to prevent hackers from [brute-forcing][1] their
way into your account.

One solution offered by some is to use a password storage program, like
[KeePass][2] or LastPass (I won't link there, since it seems there are a
few concerns I've yet to investigate, such as their recent [security
breach][3]). But this can have its own problems: local storage systems
like KeePass are vulnerable to hard drive failures; if your computer
crashes, you lose your passwords. Online solutions like LastPass pose an
interesting problem of their own: who do you trust to keep all your
passwords?

 

Instead, I recommend picking one or two good passwords and sticking to
them. Yes, I know, we're back at square one. So where's the solution?
Simple: pre-hashing your passwords.

Any service worth its salt will store passwords in a [hashed form][4] --
your password, obfuscated by one-way functions that ensure that the
password is implausible to determine just by looking at the hash. For
instance, the word "test", when passed into an [MD5 hash function][5],
results in "098f6bcd4621d373cade4e832627b4f6". As a result, employees of
the service (or hackers who gain system access, should that happen)
cannot easily determine your password directly from the hash.

I recommend that you **pre-**hash your passwords. This has the advantage
of creating long passwords (which are implausibly time-consuming to
brute-force) from simple, short words or phrases that are much easier to
remember than randomly-generated complex passwords and can be reproduced
when you need to login again without having to entrust anyone but the
service itself with your data.

But of course if you just hash your password, though you may wind up
with a longer password than the one with which you started out, you
still only have one password. This is why I recommend picking a few good
passwords, and then using the name or address of the service for which
you're logging in as a [salt][6] -- an extra bit of data that makes it
harder to use [rainbow tables][7] (pre-computed "dictionaries" of hashes
for common words or phrases) to guess your password.

This all sounds heady, so another example might be useful. Let's look at
our earlier case with the word "test". We've already seen that "test",
when MD5 hashed, becomes "098f6bcd4621d373cade4e832627b4f6". But let's
say you're signing up for an account at example.com. So you'd put
"testexample.com", "example.comtest", or some variation thereof into the
MD5 hasher. This results in "6fdea43ec85985ecae337542e870ca8f "
or "90e0c675dfe2cfe8d8d382978ea68353". Now you've taken things one step
away from the basic output of the word test *and* created a
unique password for example.com so that even if hackers breach the
service's security *and* manage to somehow figure out your
(already-hashed) password from the hash (that is, the doubly-hashed form
of your already-hashed password)  stored by the service (which is very
very improbable), they've only gained access to your account on that
specific site.

So how do you hash your password? Well, there are a few standard
algorithms used: [MD5][5] is probably best, since its output is rather
long while still remaining short enough to be used on most websites with
an upper limit on password length. If you want to be more secure, you
could look into [blowfish][8] or one of the variations of the [SHA
algorithm][9]. Of course, these links aren't the only places to find
these hashing functions -- several programs exist to do the same, and
these hashing algorithms have been implemented in almost every major
programming language (meaning that as long as you know which algorithm
you want to use, you'll be able to find a hasher for it.)

**It is important to remember which algorithm you used, as well as the
placement of the salt.**

Voila! Simple, secure, unique passwords that are easy to remember and
don't require some sort of vault or storage scheme to retrieve. All you
need is web access (which you probably already have if you're logging in
somewhere).



[1]: http://en.wikipedia.org/wiki/Brute-force_attack
[2]: http://keepass.info/
[3]: http://news.cnet.com/8301-1009_3-20060464-83.html
[4]: http://en.wikipedia.org/wiki/Cryptographic_hash_function
[5]: http://www.md5hasher.net/
[6]: http://en.wikipedia.org/wiki/Salt_(cryptography)
[7]: http://en.wikipedia.org/wiki/Rainbow_table
[8]: http://hash.online-convert.com/blowfish-generator
[9]: http://www.fileformat.info/tool/hash.htm
