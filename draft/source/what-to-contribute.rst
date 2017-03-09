Deciding what to contribute
===========================

In this section, I will describe what a contributor should do and should
not do for choosing what to contribute for Erlang/OTP.

What constitutes a contribution?
--------------------------------

Erlang/OTP has become an open source software (OSS) product
since 1998. OSS is a community product, and has the own governance
rule. For Erlang/OTP, the OTP Team makes the final decision on what
should be accepted or not as a contribution. It's more like a commercial
product governance than many other OSS products, based on the
centralized approach of making decisions, while accepting broader
contributions from the users through the GitHub repository and the Pull
Request workflow.

Erlang/OTP has the own `contribution guideline page
<https://github.com/erlang/otp/wiki/Contribution-Guidelines>`_. It is
mainly focused onto contributing code, but other fixes such as those for
the documentation is also frequently accepted.  Describing the *reason
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
changes should be proposed as a part of `*Erlang Enhancement Process*
(EEP) <http://www.erlang.org/erlang-enhancement-proposals>`_ as an
*Erlang Extension Proposal* (also called as EEP).  You can find the
archive of `Erlang Enhancement Process and the proposals in GitHub
<https://github.com/erlang/eep>`_. In this document, I will not discuss
the details on writing an EEP.
    
Why (not) writing Erlang/OTP modules?
-------------------------------------

In Erlang, a group of functions are called *module*. Erlang/OTP is a set
of modules [#wtc1]_. Writing a module is an essential part of the OTP
software development process. And a set of modules is called *application*.

Erlang/OTP provides various useful functions as their own modules. You
will be astonished to find out the functions in the modules provided in
the basic two applications, `kernel
<http://erlang.org/doc/apps/kernel/index.html>`_ and `stdlib
<http://erlang.org/doc/apps/stdlib/index.html>`_.

Developers of Erlang software can write their own modules and make them
their own applications. They can even pack their own applications
combined with the OTP runtime environment as a *release*. In many cases
having a *release* for your specific tasks will be sufficient for
running your own software.

.. [#wtc1] Erlang VM, or **BEAM**, has its own native functions called
           *built-in functions* (BIFs). BIFs are considered as a part of
           ``erlang`` module of OTP.
