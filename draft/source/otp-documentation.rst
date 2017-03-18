.. -*- coding: utf-8 -*-

Writing documentation for Erlang/OTP Releases
=============================================

Learning erl_docgen
-------------------

Writing documentation for Erlang/OTP requires adherence to the standard
and format of the `Erlang/OTP manual <http://erlang.org/doc/>`_. To
prepare the document, you need to use the tool called `erl_docgen
<http://erlang.org/doc/apps/erl_docgen/doc-build.html>`_.

Erl_docgen uses the own XML tags and notation for writing the
manual. The XML definition for writing a documentation of a module or an
application is listed as the `Reference Manual DTDs
<http://erlang.org/doc/apps/erl_docgen/refman_dtds.html>`_. I am not
going into the details of the XML tag definitions, because they are
given in the erl_docgen documentation, and rather can be easily
understood by reading actual XML documentation.

Example of rand module documentation
------------------------------------

For prototyping ``rand`` module, I set up a locally executable
documentation build environment. See `the xml-doc directory of the
prototype repository
<https://github.com/jj1bdx/emprng/tree/0.9.2/xml-doc>`_ for the further
details. `You can also try doing full building of the documentation
<https://github.com/erlang/otp/wiki/Documentation>`_.

The following list is an example source XML file for Erlang/OTP ``rand``
module, `as provided in the prototype repository
<https://github.com/jj1bdx/emprng/blob/0.9.2/xml-doc/rand.xml>`_. The
rendered result can be accessed as `an html file <_static/rand.html>`_.

.. literalinclude:: _static/rand.xml
   :language: xml
   :encoding: utf-8
              
