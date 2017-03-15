Prototyping the modules
=======================

Create an independent prototype repository
------------------------------------------

Erlang/OTP is a complex set of Erlang modules, largely dependent on each
other. Building an independent prototype repository for each development
project is much safer and more practical than tweaking the running
system. Making a small independent source code repository for
prototyping which can be integrated into other projects is a better
choice than putting everything in a mixed-up run-time system.

Building your own testing environment for Erlang/OTP
----------------------------------------------------

Try-and-error debug on a running Erlang/OTP run-time system is not a
good idea, especially when the system is being used in the production
system. Building an independent BEAM on your own is often required,
especially when you have to debug the BEAM or Erlang Run-Time System
(ERTS) by yourself.

For maintaining and switching between multiple BEAMs, I use `kerl
<https://github.com/kerl/kerl>`_ because kerl provides a way to build
your own Erlang/OTP environment from your own Git repository. The same
principle is also applicable to other essential software packages, such
as Elixir. For Elixir, I use `kiex <https://github.com/taylor/kiex>`_ to
use a separate environment from the system Elixir implementation.

Setting up a project repository for your module
-----------------------------------------------

In a modern software development procedure, you need to set up a
building environment before writing code. For Erlang/OTP, there are a
few building schemes to set up:

* `Rebar3 <https://www.rebar3.org/>`_ is an actively developed building
  and package managing tool for Erlang/OTP, which is chosen as a
  prospective package management tool for Erlang/OTP itself. Note that
  it is *not* backward compatible with the predecessor `Rebar 2
  <https://github.com/rebar/rebar>`_, which is deprecated but still in
  use for many existing projects.
* `Erlang.mk <https://erlang.mk/>`_ is a GNU Make based building tool,
  which also resolves dependencies for popular software packages. If you
  are an old-school ``make`` type of programmer like me, this tool is
  easy to use. If you need to embed non-Erlang code such as Native
  Interface Functions (NIFs) written in C or C++, erlang.mk will fit
  very well.
* `Mix <https://hexdocs.pm/mix/Mix.html>`_ is the default building,
  dependency resolution, and package management tool for Elixir. The
  packaging system `Hex <https://hex.pm/>`_ is also well accepted in
  Erlang/OTP community, for relatively easy configuration and
  documentation support on `HexDocs <https://hexdocs.pm/>`_. If you want
  to make your modules usable on Elixir (and you will surely want to do
  so), supporting mix is essential. You need to have some fluency on
  Elixir to use mix, because mix configuration language is based on
  Elixir [#proto1]_.

Execution path on loading modules
---------------------------------

For testing your own module, you need to guarantee the code of the
module should be chosen and loaded *prior to* the system module of the
same name [#proto2]_.

When running BEAM, the loading path priority can be controlled by
``-pa`` and ``-pz`` path of the `erl
<http://erlang.org/doc/man/erl.html>`_ command. Some package tools have
their own commands for setting the execution path, such as `Rebar3 shell
command <http://ferd.ca/rebar3-shell.html>`_. On Elixir, the interactive
shell `iex <https://hexdocs.pm/iex/IEx.html>`_ has the similar
functionality.

Write your own test code
------------------------

Testing code and providing a regression test set is a critical part of
modern software development. Unit testing is essential as a minimum
requirement. `EUnit <http://erlang.org/doc/man/eunit.html>`_ is a good
place to start. For Erlang/OTP module development, however, providing
tests under the `Common Test
<http://erlang.org/doc/man/common_test.html>`_ framework is mandatory.

Testing code should cover various aspects including checking the
function arguments, value range, and error handling to reject illegal
values. For a complex algorithm, you need to provide the reference
output from a reference implementation which is not necessarily written
in Erlang, and compare the output with the corresponding testing
program.

For prototyping the `rand` module algorithms, I picked up the code from
the reference implementations in C, wrote a small testing value
generation code, collected the computed results, and embedded them into
the unit testing code of the Erlang module. Having this kind of full
regression tests help finding a bug possibly caused by the version
change or implmentation glitches caused by the base Erlang/OTP
distribution. 

.. Rubric:: Footnotes

.. [#proto1] See `Introduction to Mix
             <http://elixir-lang.org/getting-started/mix-otp/introduction-to-mix.html>`_
             as the primer for learning Mix.

.. [#proto2] Erlang module namespace is *not* hierarchical, so the
             module name collision may occur at any time.

