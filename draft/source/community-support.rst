.. -*- coding: utf-8 -*-

Earning community support
=========================

User community support is essential
-----------------------------------

An excellent proposal for an open source software product without the
user community support will not be approved or chosen by the development
team. User community support is essential and critical to get your
proposal or changes accepted into the repository.

Things you can do for gaining community support
-----------------------------------------------

It took almost six years to deprecate and remove ``random`` module and
let the Erlang/OTP users convert into ``rand`` module, from 2011
to 2017. During the process, I have attempted a few kinds of promoting
the need to change for a new pseudo random number generator (PRNG).

In the following sections, I will explain the activities I've done to
promote the problem, issues, and the solution regarding the ``random``
module.

Release all you've got
----------------------

I've released all PRNG algorithm code which are the candidates for
``rand`` module. The repositories for the Erlang implementations are:

* `sfmt-erlang <https://github.com/jj1bdx/sfmt-erlang>`_, an
  implementation of `SIMD-oriented Fast Mersenne Twister (SFMT)
  <http://www.math.sci.hiroshima-u.ac.jp/~m-mat/MT/SFMT/>`_;
* `tinymt-erlang <https://github.com/jj1bdx/tinymt-erlang>`_, an
  implementation of `Tiny Mersenne Twister (TinyMT);
  <http://www.math.sci.hiroshima-u.ac.jp/~m-mat/MT/TINYMT/>`_
* `exsplus128 <https://github.com/jj1bdx/exsplus128>`_, an Xorshift128+
  implementation;
* `exs64 <https://github.com/jj1bdx/exs64>`_, an Xorshift64*
  implementation;
* `exs1024 <https://github.com/jj1bdx/exs1024>`_, an Xorshift1024*
  implementation; and
* `exsplus116 <https://github.com/jj1bdx/exsplus116>`_, an Xorshift116+
  implementation.

For the ``rand`` module, OTP Team finally chose exs64, exs1024, and
exsplus116 (called as ``exsplus`` in the ``rand`` module, the default
algorithm).

OTP Team developer Dan Gudmundsson, who is in charge of ``rand`` module,
even proposed the author of Xorshift*/+ algorithm Sebastiano Vigna to
invent a new algorithm *specifically for Erlang/OTP's limitation of
60-bit integers*, which is Xorshift116+, the algorithm for exsplus. Dan
was so helpful for actualizing the module for Erlang/OTP.

Releasing the code has many advantages including the following:

* Being used by many people will increase the chance to obtain
  the feedbacks for improvement;
* Even if the module won't be merged as a part of Erlang/OTP, many
  people still want to use as a part of their application software, so
  releasing them itself will be of a great service for those people; and
* Making the code public available will increase the awareness of the
  issues, which is about PRNG quality in my case.

Talk about your code
--------------------

Having a talk on your issues at a public conference or a workshop,
including the problem analysis and the possible solutions, will help
raising the awareness of the issues.

In my case, I gave PRNG-related presentations at influential conferences
such as:

* `Erlang Factory SF Bay Area 2011
  <http://www.erlang-factory.com/conference/SFBay2011/speakers/kenjirikitake>`_
* `ACM Erlang Workshop 2011
  <http://www.k2r.org/kenji/papers/file-archive/erlang2011-rikitake-sfmt-20110919.pdf>`_
* `ACM Erlang Workshop 2012
  <http://www.k2r.org/kenji/papers/file-archive/erlang2012-rikitake-tinymt-20120902.pdf>`_
* `London Erlang User Group Meetup in September 2013
  <https://speakerdeck.com/jj1bdx/erlang-random-numbers-and-the-security>`_
* `Erlang Factory SF Bay Area 2015
  <https://speakerdeck.com/jj1bdx/otp-searching-for-better-prngs>`_
* `Erlang User Conference 2016
  <https://speakerdeck.com/jj1bdx/fifteen-ways-to-leave-your-random-module>`_

A talk proposal for the module you want to commit for Erlang/OTP will be
a viable candidate to be presented in a Erlang-and-Elixir-related
conference. In such a conference, you can talk to an influential person,
or to a complete stranger, to personally obtain a direct feedback to
your idea. Such an occasion is precious and important, especially when
the person shows support to your idea.

Write a PoC and show what the problem is
----------------------------------------

I think the most influential activity for letting OTP Team make a
decision to change the default PRNG algorithm is the fact that the old
algorithm in ``random`` module, AS183, was practically easy to exploit
in less than eight hours with the proof-of-concept (PoC) code in my
`as183-c <https://github.com/jj1bdx/as183-c>`_, which I released in
December 2014. 

While writing and publishing a PoC code *do not* imply that the idea
represented in the code is new or that nobody proved the practicality
before the PoC code was published [#comm1]_, a PoC will surely raise an
awareness of the possible attack vectors against known vulnerabilities.

.. Rubric:: Footnotes

.. [#comm1] An Erlang/OTP veteran (whose name is withheld for respecting
            his privacy) sent me a personal email that my PoC code had
            no new discovery either in research or engineering aspects
            and *absolutely meaningless*. A good news was, however, that
            he also praised me for publishing alternative
            implementations for public use.
