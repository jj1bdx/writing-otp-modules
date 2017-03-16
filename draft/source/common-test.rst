.. -*- coding: utf-8 -*-

Testing with Common Test
========================

Read OTP source first to learn Common Test cases
------------------------------------------------

All OTP module unit tests are performed under `The Common Test Framework
<http://erlang.org/doc/man/common_test.html>`_. You need to learn the
Common Test for obtaining quality assurance of including your code into
OTP.

I think the easiest way to start writing Common Test cases is to read
the ones already written in the OTP source. Each OTP module has the
Common Test case source code under each application with the name of
``test/*_SUITE.erl`` [#ct1]_. You can find a lot of useful patterns.

Common Test manual chapter for `Writing Test Suites
<http://erlang.org/doc/apps/common_test/write_test_chapter.html>`_
provides a lot of useful examples, including the `Test Case Groups
<http://erlang.org/doc/apps/common_test/write_test_chapter.html#id76868>`_.

Use groups for parallel and sequential tests
--------------------------------------------

Common Test has the Test Case Groups, which allows programmers to
enforce the sequence of executing the tests and to specify parallel
execution of a set of tests.

The following code in ``rand`` module [#ct2]_ explains the sequence of
the tests to be performed, beginning from ``seed``, with a group called
``basic_stats`` and the last group of ``reference_jump``.

.. code-block:: erlang

  all() ->
    [seed, interval_int, interval_float,
     api_eq,
     reference,
     {group, basic_stats},
     plugin, measure,
     {group, reference_jump}
    ].

You need to list all the test functions and groups in  ``all/0``.

The group properties are defined in ``groups/0`` as follows, setting
*parallel execution* flag for each of the two groups with the test
functions in the group:

.. code-block:: erlang

  groups() ->
    [{basic_stats, [parallel],
      [basic_stats_uniform_1, basic_stats_uniform_2, basic_stats_normal]},
     {reference_jump, [parallel],
      [reference_jump_state, reference_jump_procdict]}].
     
.. Rubric:: Footnotes

.. [#ct1] For example, the Common Test cases for ``rand`` module is at
          ``lib/stdlib/test/rand_SUITE.erl`` in the OTP source code
          tree, since ``rand`` is a part of ``stdlib`` application.

.. [#ct2] The code will be appeared on OTP 20. See
          https://github.com/erlang/otp/commit/1c000086275c06596ad402081be12ef95db6ea40
          for the details.
