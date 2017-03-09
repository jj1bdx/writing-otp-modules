Introduction
============

Erlang/OTP and the OTP Team need your help
------------------------------------------

`Erlang/OTP <http://www.erlang.org/>`_ is a well-designed and highly
stable product, as well as a language and a concurrent system. Most of
the features are carefully designed and easy to use. Reading the `OTP
online manual <http://www.erlang.org/doc/>`_ will solve most of the
problems you will encounter. (If you haven't, you should do it now.)
Erlang/OTP is well maintained by the **OTP Team**.

Unfortunately, even for such a great product, you might find *numerous*
bugs. Sometimes those bugs are nasty enough to prevent writing further
code, or may result in a serious vulnerability or a security hole.
Those bugs *must be reported first to the OTP Team*, even if you cannot
fix them. Erlang/OTP uses the Atlassian JIRA system for `the bug
reporting site <https://bugs.erlang.org/>`_ [#intro1]_ .

Also, OTP team has been chronically understaffed, so their bug fixing
resources are limited. Lots of other people are helping the OTP team,
such as Erlang Solutions, Industrial Erlang User's Group, and the
committers of the `OTP GitHub Repository
<https://github.com/erlang/otp/>`_. Many people from the `Elixir
language <http://elixir-lang.org/>`_ community also help a lot.

Why (not) writing Erlang/OTP modules?
-------------------------------------

In Erlang, a group of functions are called *module*. Erlang/OTP is a set
of modules [#intro2]_. Writing a module is an essential part of the OTP
software development process. And a set of modules is called *application*.

Erlang/OTP provides various useful functions as their own modules. You
will be astonished to find out the functions in the modules provided in
the basic two applications, `kernel
<http://erlang.org/doc/apps/kernel/index.html>`_ and `stdlib
<http://erlang.org/doc/apps/stdlib/index.html>`_.

Developers of Erlang software can write their own modules and make them
their own applications. They can even pack their own applications
combined with the OTP runtime environment as a *release*. In many cases
having a *release* for your specific tasks will be enough for running
your own software.







.. rubric: Footnotes

.. [#intro1] You need to create your account first for ``bugs.erlang.org``.

.. [#intro2] Erlang VM, or **BEAM**, has its own native functions called *built-in functions* (BIFs). BIFs are considered as a part of ``erlang`` module of OTP.
