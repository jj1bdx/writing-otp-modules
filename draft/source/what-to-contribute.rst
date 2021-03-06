.. -*- coding: utf-8 -*-

Deciding what to contribute
===========================

In this section, I will describe what a contributor should do and should
not do for choosing what to contribute for Erlang/OTP.

Erlang/OTP and the OTP Team need your help
------------------------------------------

Before getting into the details, I would like to emphasize the fact that
*the Erlang community and OTP Team always need your help* to fix the bugs
and improve the software.

`Erlang/OTP <http://www.erlang.org/>`_ is a well-designed and highly
stable product, as well as a language and a concurrent system. Most of
the features are carefully designed and easy to use. Reading the `OTP
online manual <http://www.erlang.org/doc/>`_ will solve most of the
problems you will encounter. (If you haven't, you should do it now.)

Erlang/OTP is actively maintained by the **OTP Team**. The OTP Team is
*not* a group of volunteers; *they are paid developers* hired by
Ericsson, and takes the final responsibility of the code
quality. Erlang/OTP is not a hobby product; it is a mission-critical
product for many parts of the telecommunication and internet
infrastructure systems.

Unfortunately, even for such a great product, you might find *numerous*
bugs. Sometimes those bugs are nasty enough to prevent writing further
code, or may result in a serious vulnerability or a security hole. If
you find any of the bugs, they *must be reported first to the OTP Team*,
even if you cannot fix them. Erlang/OTP uses `the bug reporting site
<https://bugs.erlang.org/>`_ [#wtc3]_ solely for this purpose.

Also, OTP team has been chronically understaffed, so their bug fixing
resources are limited. Lots of other people are helping the OTP team,
such as `Erlang Solutions <https://www.erlang-solutions.com/>`_,
`Industrial Erlang User Group
<http://erlangcentral.org/industrial-erlang-user-group/>`_, and the
contributors of the `Erlang/OTP GitHub Repository
<https://github.com/erlang/otp/>`_. Many people from the `Elixir
language <http://elixir-lang.org/>`_ community also help a lot.

The development history of Erlang/OTP can be found here as a paper
written by Joe Armstrong, the principal author of Erlang and one of the
four leading developers of Erlang, as `a presentation called "A History
of Erlang" presented in HOPS III conference held in 2007
<https://doi.org/10.1145/1238844.1238850>`_.

What is considered as a contribution?
-------------------------------------

Erlang/OTP has become an open source software (OSS) product
since 1998. OSS is a community product, and every OSS has the own
governance system. For Erlang/OTP, the OTP Team makes the final decision
on what should be accepted or not as a contribution. It's more like a
commercial product governance than other OSS products, based on the
centralized approach of making decisions, while accepting broader
contributions from the users through the GitHub repository and the Pull
Request workflow.

Erlang/OTP has the own `contribution guideline page
<https://github.com/erlang/otp/wiki/Contribution-Guidelines>`_. It is
mainly focused onto contributing code, but other fixes such as those for
the documentation are also frequently accepted.  Describing the *reason
to change* is essential for proposing a change to Erlang/OTP. Here's a
quote from the guideline:

    It is important to write a good commit message explaining why the
    feature is needed. We [OTP Team] prefer that the information is in
    the commit message, so that anyone that want to know two years later
    why a particular feature can easily find out. It does no harm to
    provide the same information in the pull request (if the pull
    request consists of a single commit, the commit message will be
    added to the pull request automatically).

Note that a proposal which contains the Erlang language and semantic
changes should be proposed as a part of `Erlang Enhancement Process
(EEP) <http://www.erlang.org/erlang-enhancement-proposals>`_ as an
*Erlang Extension Proposal* (also called EEP).  You can find the archive
of `Erlang Enhancement Process and the proposals in GitHub
<https://github.com/erlang/eep>`_. In this document, I will not discuss
the details on writing an EEP, because writing an EEP is for changing
the syntax and semantics of Erlang and OTP, and it requires far deeper
and broader knowledge than writing an OTP module.
    
How *not* to write Erlang/OTP modules
-------------------------------------

In Erlang, a group of functions is called *module*. Erlang/OTP is a set
of modules [#wtc1]_. Writing a module is an essential part of the OTP
software development process. And a set of modules is called *application*.

Making a decision of writing or not writing a module should be done
carefully.  Erlang/OTP provides various useful functions as their own
modules. You will be astonished to find out the functions in the modules
provided in the basic two applications, `kernel
<http://erlang.org/doc/apps/kernel/index.html>`_ and `stdlib
<http://erlang.org/doc/apps/stdlib/index.html>`_. You can find many
other functions and modules in OTP suitable for your work.

A general tip for choosing a function to use is to always consider using
the existing functions in the OTP modules first *before* reinventing or
even inventing your own ones. In most cases you can do what you want to
do by choosing an existing function. In short: *read the OTP
documentation first* before writing your own code; your problem can be
solved by combining existing functions.

Development of Erlang software usually means writing the
project-specific modules and make them the project-specific
applications. The developed OTP applications can be combined with
the OTP runtime environment as a *release*. In many cases having a
*release* for your specific tasks will be sufficient for running your
own software [#wtc2]_, even you have to include your own modules.

Why writing Erlang/OTP modules then?
------------------------------------

In most cases you don't have to write the modules which should reside in
OTP. For some cases, however, you need to write and contribute your code
to the Erlang/OTP modules. You need to consider a few issues before
thinking about making a contribution to OTP, as described in this
section.

Is the module or new code really needed in OTP?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

OTP is part of Erlang and cannot be separated from OTP [#wtc4]_. If your
module is accepted to OTP, that will affect *all* users of Erlang/OTP,
including other Erlang-derived language users, such as those of Elixir
and LFE. If your contribution is a critical bug fix, it should be merged
as soon as possible. If it's a feature or an enhancement, it would take
a much longer time to assess the impact of change.

Who needs the new code?
^^^^^^^^^^^^^^^^^^^^^^^

If what you want to do with your contribution can be done without
changing other parts of Erlang/OTP, it should be separated from the
OTP. Just because your code provides a cool feature does not necessarily
justify that the code should be a part of Erlang/OTP.

Removing old code from OTP is hard
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Removing an OTP module is extremely difficult after once it is accepted
as a part of OTP. For example, the module ``random``, which is being
replaced by a new module ``rand`` which has become official since OTP
18.0, will remain for two major versions; it is now *deprecated* on OTP
version 19, and will be *removed* on OTP version 20. The life of single
OTP version is usually one year [#wtc5]_, so *two years* will be
required as minimum to replace an obsolete piece of code by the
respective new code.

A case study: rand module
-------------------------

The module ``rand``, a pseudo random number generator (PRNG) which I
contributed with Dan Gudmundsson as the corresponding OTP maintainer for
Erlang/OTP 18.0, had many specific reasons to be a part of OTP as
follows:

* AS183, the algorithm of ``random``, has been exploited less than a day
  with a modern computer [#wtc6]_, so there was a strong need to provide
  the alternative to plug the security hole;
* Finer resolution of the output, which gives sufficient precision for
  Erlang float numbers;
* Much longer period for preventing prediction of *random* number
  values;
* Fully compatible or even simplified API for the programmer;
* Multiple choices of algorithms available for future extension and
  bugfix; and
* the execution speed for the default algorithm is as fast as ``random``
  on a modern 64bit CPU.

There are also other situational factors on making ``rand`` module possible:

* `Xorshift*/+ <http://xoroshiro.di.unimi.it/>`_, a compact and
  well-tested PRNG implementation became available in the Public Domain;
* Awareness on improving algorithms of language-specific PRNGs increased
  (e.g, `JavaScript V8 Engine failure discovered on November 2015
  <https://v8project.blogspot.jp/2015/12/theres-mathrandom-and-then-theres.html>`_);
  and
* I gained expertise of building PRNG module on Erlang/OTP by building
  prototypes for many different algorithms. On the other hand, it took
  *four* years to actually start implementing the ``rand`` module after
  `the first PRNG security incident of Erlang/OTP discovered by Geoff
  Cant on May 2011 <http://www.kb.cert.org/vuls/id/178990>`_.

My lessons learned through the ``rand`` module development process are
as follows:

* Software is a sticky being. You need to convince a lot of people to
  revise an old piece of software, even it has a critical vulnerability.
* Contribution of lots of people are needed to actualize revision of a
  piece of software. Having a good idea itself is *not enough*.
* You need to take time for the whole process unravels.

  
.. rubric:: Footnotes

.. [#wtc1] Erlang VM, or **BEAM**, has its own native functions called
           *built-in functions* (BIFs). BIFs are considered as a part of
           `erlang <http://erlang.org/doc/man/erlang.html>`_ module of OTP.

.. [#wtc2] You can even specify a version of Erlang/OTP when building a
           release, since a release is a complete set of executable
           program for an operating system.

.. [#wtc3] You need to create your account first for
           ``bugs.erlang.org``. The bug tracking system is currently
           using Atrassian's JIRA.

.. [#wtc4] OTP itself has been under restructuring and may be split into
           multiple parts of applications or modules which may be
           classified by OTP Team. The change, however, has not been
           happened yet as of March 2017.

.. [#wtc5] In the past R14, R15, and R16 releases of OTP, the length of
           the major version was two years. For the further details,
           check out the release dates of each OTP release.

.. [#wtc6] See https://github.com/jj1bdx/as183-c for the
           proof-of-concept code to exploit all the possible values of
           AS183.
