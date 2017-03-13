Prototyping the modules
=======================

Create an independent testing environment
-----------------------------------------

Erlang/OTP is a complex set of Erlang modules, largely dependent on each
other. Building an independent testing environment for each development
project is much safer and more practical than tweaking the running
system.

Building your own testing environment for Erlang/OTP
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Try-and-error debug on a running Erlang/OTP system is not a good idea,
especially when the system is being used in the production
system. Building an independent BEAM on your own is often required,
especially when you have to debug the BEAM or Erlang Run-Time System
(ERTS) by yourself.

For maintaining and switching between multiple BEAMs, I use `kerl
<https://github.com/kerl/kerl>`_ because kerl provides a way to build
your own Erlang/OTP environment from your own Git repository. The same
principle is also applicable to other essential software packages, such
as Elixir. For Elixir, I use `kiex <https://github.com/taylor/kiex>`_ to
use a separate environment from the system Elixir implementation.






