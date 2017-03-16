.. -*- coding: utf-8 -*-

Maintenance after the initial release
=====================================

Your responsiblity on adding a module to Erlang/OTP
---------------------------------------------------

When you add a module to Erlang/OTP, that means you are *also
responsible* for maintaining the module, especially when the security
issues or vulnerabilities are found. As in the case of typical Open
Source Software, you are not legally bound to provide a help, but you
are *morally and professionally bound* to provide a help when it is
requested by the OTP Team. Also, you are expected to contribute a
further enhancement or a new feature when they are available.

An unmaintained piece of code will be deprecated and removed from OTP by
the OTP Team's discretion. Old code is prone to vulnerability or
degradation leading to new security issues. For example. ``random``
module, the predecessor of ``rand`` module, survived for a very long
time at least from February 1999 [#maint1]_, but finally to be phased
out and removed from OTP 20, which will be released in June 2017
[#maint2]_. Generally speaking, an 18-year old code should be reviewed
and revised simply because it is *old enough*.

Move carefully for adding a new feature
---------------------------------------

Adding a new feature to an existing Erlang/OTP module may require the
same or even more effort to write a new module. OTP Team generally takes
conservative approach to changes, and the users of Erlang/OTP do not
want drastic changes, especially when they break the backward
compatibility. So you need to be careful on moving for adding a new
feature to an existing module, even if that is under your control.

.. Rubric:: Footnotes

.. [#maint1] The oldest available source code archive of Open Source
             Erlang at
             http://erlang.org/download/OLD/erlang_base-47.4.1.src.tar.gz
             suggests the ``random`` module code resided at
             ``erlang-47.4.1/lib/stdlib/src/random.erl``. The time stamp
             of the file was on ``Feb 24 1999``.

.. [#maint2] Quoted from `Kenneth Lundin's presentation slides of News
             from The OTP Team, at Erlang User Conference 2016 in
             Stockholm, Sweden, September 2016
             <http://www.erlang-factory.com/static/upload/media/1474551034604761kennethlundinotpnewseuc2016.pdf>`_.
