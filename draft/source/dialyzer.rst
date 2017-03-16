.. -*- coding: utf-8 -*-

Adding type specifications with Dialyzer
========================================

Type specifications are required in OTP modules
-----------------------------------------------

All OTP exported functions (i.e., those defined with ``-export()``
attribute) have `the type specifications
<http://erlang.org/doc/reference_manual/typespec.html>`_. The
specifications are essential to define the type constraints for enabling
static analysis of the Erlang code. Some module also have their own
types, and they are essential to get access to the data structures
defined in the module.

Having a correct type specification for each of the exported/global
modules and related types is mandatory to be accepted as a part of
Erlang/OTP. *Without the necessary type specifications, your code will
not be accepted by the OTP Team* [#dialyze1]_.

Using Dialyzer
--------------

`Dialyzer <http://erlang.org/doc/apps/dialyzer/dialyzer_chapter.html>`_
is the tool of Erlang for performing the static analysis with the source
code and the BEAM binary code with the debugging option enabled. You can
invoke dialyzer as:

.. code-block:: sh

  dialyzer --build_plt --apps erts kernel stdlib

Note well that the build tools may have Dialyzer options as well, such
as ``rebar3 dialyzer`` for rebae3 or ``make dialyze`` of erlang.mk.

Dialyzer on improper lists
--------------------------

Erlang/OTP ``rand`` module has the Xorshift116+ code, which extensibly
uses an improper list for an internal data structure. Dialyzer is picky
on detecting the improper list, so the following attribute for the
warning option has to be configured to prevent unnecessary warnings:

.. code-block:: erlang
                
  -dialyzer({no_improper_lists, exsplus_next/1}).

See the section of `Requesting or Suppressing Warnings in Source Files
in the Dialyzer Reference Manual
<http://erlang.org/doc/man/dialyzer.html#suppression>`_ for the further
details.
               

.. Rubric:: Footnotes

.. [#dialyze1] You should also be careful that providing the type
               specification for non-exported (private) functions or
               types are not necessary.

