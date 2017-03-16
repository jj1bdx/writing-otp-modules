.. -*- coding: utf-8 -*-

Introduction
============

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
