Solving licensing issues of contributed code
============================================

*Note: the author is not a lawyer and the contents in this section may
not be legally complete. Ask lawyers for the legal advices.*

License of Erlang/OTP: Apache License 2.0 
-----------------------------------------

Erlang/OTP has been licensed under `Apache License 2.0
<https://www.apache.org/licenses/LICENSE-2.0>`_ since the release of
Erlang/OTP 18.0 [#license1]_ on May 2015.

Rami Sass explains the summary of how Apache License 2.0 works in the
blog entry `Top 10 Apache License Questions Answered
<https://www.whitesourcesoftware.com/whitesource-blog/top-10-apache-license-questions-answered/>`_. Some
of the points are quoted here as follows:

* Apache License 2.0 is a permissive open source license.
* You can freely use, modify, distribute and sell a software licensed
  under the Apache License without worrying about the use of software:
  *personal, internal or commercial.*
* If you redistribute software with any Apache licensed components, you
  must include a copy of the license, provide a clear Apache License
  attribution, and add modification notices to all the files that you
  modify.
* You can choose to release the modified or derived products under
  different licenses. The unmodified parts of the software, however,
  must retain the Apache License.
* You cannot name your modified version in any way that suggests that
  the final product is endorsed or created by the Apache Software
  Foundation.
* Every licensed file must contain any original copyright, patent,
  trademark, and attribution notices in its redistributed code.
* Each modified file must also contain a notice about all the changes
  made to the original file.

Compatibility of Apache License 2.0 with other licenses
-------------------------------------------------------

Mixing source code which has other licenses than Apache License 2.0
should be done carefully.

GPL version 2 and 3
^^^^^^^^^^^^^^^^^^^

Software under GNU Public License (GPL) cannot be directly linked to
Erlang/OTP, due to the license compatiblity with Apache License 2.0.

According to the `document of Apache Software Foundation about Apache
License 2.0 and GPL compatibility
<http://www.apache.org/licenses/GPL-compatibility.html>`_, the following
issues must be considered:

* Software with Apache License 2.0 is compatible with GPL
  version 3 (GPLv3), but the derived product *must be licensed under GPLv3*.
* Software with GPL version 2 (GPLv2) is *incompatible* with Apache
  License 2.0, citing the patent termination and indemnification
  provisions as restrictions not present in the older GPL license.

MIT and BSD licenses
^^^^^^^^^^^^^^^^^^^^

Including MIT and BSD license code in Erlang/OTP does not require any
special process, because both license allow relicensing of the software,
under the restriction of keeping the original notices.

CC0 license (Public Domain)
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Code explicitly stated as `Creative Commons CC0 licensed
<https://creativecommons.org/publicdomain/zero/1.0/>`_, which means
equivalent to be placed in the Public Domain, can be freely relicensed.

Relicensing your code to Erlang/OTP
-----------------------------------

When OTP Team decides to include your code as a part of OTP, you need to
comply the following rules:

* The code is relicensed as Apache License 2.0, and no other licenses
  are allowed in the code.
* The copyright notice in the code must be a simple one like this:

    Copyright (c) 2017 by Kenji Rikitake.

  Note that the notice has no "All Rights Reserved" or other words
  except the year and the name.

OTP Team will let you know the details on the exact conditions before
merging your code, so that the legal issues will be cleared.

If you are using other authors' algorithms and code, they must be
compatible with Apache License 2.0 of Erlang/OTP. You may need to obtain
written permissions from the original algorithm authors for specific
relicensing to Erlang/OTP.

.. rubric:: Footnotes
            
.. [#license1] On versions 17.x and before, Erlang/OTP was licensed
               under `Erlang Public License 1.1
               <http://www.erlang.org/EPLICENSE>`_, a modified license
               from Mozilla Public License. This is no longer applicable.
