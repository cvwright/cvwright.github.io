---
title: Projects
layout: page
---

This page describes some projects that I'm working on, or that I've
worked on in the past.

## Kombucha Privacy (2019 -- present)

I started a company, Kombucha Digital Privacy Systems, to take a break
from research and to instead spend some time building real systems that
regular people can use right away.
Our first product is called **Circles**, and it will be launching on iOS
in late Spring 2021.

## Cryptographic Crumpling and Abrasion (2017 -- present)

Governments around the world are threatening to crack down on
encryption.  They may soon start requiring pervasive backdoors
or other mechanisms for "exceptional access" allowing law enforcement
agencies to access encrypted data.

I take these threats seriously, so I've been working on some ideas
for maximizing security and privacy in a world where exceptional
access is required.

In joint work with **Mayank Varia**, we proposed the twin notions of
cryptographic *crumpling* and *abrasion*.
The idea is to weaken cryptographic keys *just a little bit*, so
that a nation state government could just barely afford to recover
only the keys that it really needs to keep its people safe.

* **Abrasion** imposes a huge upfront cost (e.g. $2 billion) on anyone
who wants to start cracking keys.
It's intended to discourage profit-motivated actors like hackers
and megacorps from getting into the game.

* **Crumpling** imposes another marginal cost for every encrypted
message that is cracked.
It's there to prevent a legitimate government from abusing its
newfound power to decrypt messages that it doesn't really need.

My former MS student at PSU, **Scott Griffy**, wrote his thesis on
a very cool new construction for hash-based abrasion.
With any luck, we'll have it published in a conference paper
sometime in the near future.

## Encrypted Databases and Searchable Encryption (2013 -- 2020)

While I am not a cryptographer, I do sometimes work on the security
of systems where cryptography is an important building block.

In early 2013, I wanted to encrypt my email that was stored in the
cloud.
Of course, being able to search is a killer feature for any email
application, so I started asking questions about the efficiency
and backwards compatibility of constructions for **searchable
encryption**.
Fortunately my first office mate from grad school, **Seny Kamara**,
is one of the world's leading experts on this stuff.
I sent him an email asking, basically, "*Hey why has nobody ever
tried doing something less secure but more efficient?*"

Over the next few years, we found out in great detail why the
applied crypto community had been smart to avoid the kind of
construction that I initially wanted.

In 2015, we published a paper analyzing the most efficient
schemes for encrypting a relational database, including
deterministic encryption and order-revealing encryption.
It turns out that, if the adversary has a good idea of the
statistical distribution from which your data was drawn,
then he can make a very good guess about almost every 
encrypted record in your database.

In 2016, my student **David Pouliot** and I showed that a similar
attack, using graph matching algorithms, could be used to recover
many of the words in a free-form text corpus (like email) if it's
encrypted using the efficient-but-risky constructions that I
originally wanted.  Whoops!

In 2019, David, Scott, and I published a paper showing how
the worst weaknesses of determinstic encryption can be 
efficiently mitigated with **Weakly Randomized Encryption**.
It doesn't fix everything, but it's a lot better than what
we had before.

In 2020, **David** defended his dissertation on WRE and other
further advancements over deterministic encryption.

## Figleaf / Thumbnail Preserving Encryption (2014 -- 2019)

When my daughter was born in 2014, I wanted a more secure way to
share baby photos.
This began my long, wild journey through multimedia encryption,
a topic usually reserved for ["goofy DRM schemes"](https://blog.cryptographyengineering.com/2011/11/10/format-preserving-encryption-or-how-to/) and avoided by respectable cryptographers.

But, dammit, I wanted to share my baby pictures without posting
the poor kid all over Facebook and Google, so I dove right in.
I've never been a respectable cryptographer anyway.

The approach that we came up with was basically a form of
property preserving encryption for images: **Thumbnail
Preserving Encryption**.
It does just what the name says.
When you encrypt an image, its low-resolution "thumbnail" looks
just the same as it did before the encryption, but (ideally)
all finer-grained detail is completely obscured.

This is simultaneously one of my most favorite research problems
ever, and one of the most frustrating.
It's the greatest example of a [nerd sniping](https://xkcd.com/356/)
problem that I've ever encountered in real life.
It sounds deceptively simple.
Given a rectangle of pixel intensities and a secret key,
encrypt the pixels such that:

1. The encrypted pixels produce the same thumbnail intensity as the
  plaintext pixels.
2. The encrypted intensities don't go outside the allowable range
  for plaintext values, typically 0-255.
3. Given the key and the encrypted pixels, you can decrypt to
  recover the original plaintext pixels, or at least a close enough
  approximation that a human won't notice the difference.
4. Your runtime performance should be not too much slower than just
  AES-CTR encrypting the original JPEG as a blob.
5. The size of your encrypted file should be not too much larger
  than the JPEG compressed original.
6. Oh, and you also don't get to use any extra space for ciphertext
  expansion, e.g. for an IV or a MAC.
7. And if you really want to get crazy, try to come up with something
  that can survive being re-compressed with JPEG in encrypted form,
  and still decrypt to something that looks reasonably close to the
  original.

It sounds easy at first, but people much smarter than me have spent
sleepless nights on this problem and still came up empty.

Even still, it was a heck of a lot of fun.
I had a lot of great conversations with **Seth Terashima**,
**Wu-chi Feng**, **Mike Rosulek**, **Rakesh Bobba**, **Byron Marohn**,
**Colleen Toth**, **Kimia Tajik** and others about various things
that we could try.
And we tried a whole lot of them.

We eventually came up with two constructions:

* A quick and dirty "approximate" TPE scheme that preserves an
  approximation of the original thumbnail and works on JPEG
  compressed photos, first proposed by myself and then improved
  substantially by my MS student **Byron Marohn**.  It can give
  very reasonable file sizes, but nobody is really sure how much
  protection it provides in that configuration.
* A much slower but more secure "exact" TPE scheme that matches
  the original thumbnail exactly, from **Kimia Tajik** and others
  at Oregon State.  The design is based on substitution-permutation
  ciphers, and if you let it run for sufficiently many rounds,
  then it's definitely secure.  But unfortunately nobody knows
  for sure when it's safe to let it stop.

**Kimia** recently defended her PhD dissertation on this topic at OSU.

If you come up with a TPE scheme that meets all or most of the
requirements above, I'd love to hear about it.
I'm not actively working in this space right now, but it's still
one of my favorite problems.

## LO-PHI (2010 -- 2012)

My team at MIT-LL designed and built what I believe was the most
advanced, low-artifact cyber testbed instrumentation tool in the world.
After I left the Lab, my former intern **Chad Spensky** and others
did an awesome job continuing to develop the initial prototype
into a real system, described in their paper at NDSS 2016.

## Cyber Testbeds and Experimentation (2008 -- 2012)

## Voice Over IP Security (2006 -- 2009)
