Introduction
============

Purpose of this documentation
-----------------------------

Erlang/OTP accepts many pieces of user-contributed code, but the
contribution process is not necessarily trivial. In this document, I
(the author) will describe possible issues for contributing a piece of
code to Erlang/OTP, and how the issues can be effectively solved, based
on my experience of writing `Erlang rand module
<http://erlang.org/doc/man/rand.html>`_.

This documentation is written for people who want to know

* how the practical tips about writing Erlang/OTP modules;
* how the OTP code is developed and released; and
* what to do for contributing their pieces of code to OTP.

This documentation is originally written for a presentation called
`Writing A New Erlang/OTP Module for Beginners
<http://www.erlang-factory.com/sfbay2017/kenji-rikitake.html>`_ to be
held in March 2017, including the contents which are not necessarily
suitable for the presentation.
  
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
*not* a group of volunteers; *they are paid developers*. Erlang/OTP is
not a hobby product; it is a mission-critical product for many parts of
the telecommunication and internet infrastructure systems.

Unfortunately, even for such a great product, you might find *numerous*
bugs. Sometimes those bugs are nasty enough to prevent writing further
code, or may result in a serious vulnerability or a security hole. If
you find any of the bugs, they *must be reported first to the OTP Team*,
even if you cannot fix them. Erlang/OTP uses `the bug reporting site
<https://bugs.erlang.org/>`_ [#intro1]_ solely for this purpose.

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

.. rubric: Footnotes

.. [#intro1] You need to create your account first for ``bugs.erlang.org``.

