.. -*- coding: utf-8 -*-

Effectively issueing pull requests on GitHub
============================================

Opening a pull request (PR) to `Erlang/OTP GitHub repository
<https://github.com/erlang/otp/>`_ is the default contribution prodecure
described in the `contribution guideline of Erlang/OTP
<https://github.com/erlang/otp/wiki/Contribution-Guidelines>`_.

What is required in a pull request
----------------------------------

The commit message of the PR should contain the following elements:

* What you are going to do with the PR;
* How the PR changes the behavior of the code;
* What and how the changes induced by the PR will affect to the other
  modules and applications; and
* What and how the changes induced by the PR will *not* affect to the
  other modules and applications.

The changed code and documentation should meet the following standards:

* For a new feature, the new PR should be committed to the ``master``
  branch.
* If the contribution is a bugfix, reporting the bug is mandatory.
* The code should be built and tested on all major platforms, such as
  Linux, Windows, macOS, and FreeBSD, unless implementing a
  platform-specific feature.
* The documentation should be updated as well.
* Backward compatibility is a requirement. Even if a non-compatible
  feature is accepted, the old code will remain for one or two major
  OTP releases.
* The coding style must meet the standard for OTP. In short: 4 spaces,
  use Emacs erlang-mode.
* Make separate commits for separate changes.
* Make sure that each commit can be compiled and that the commit works.

How to work together on GitHub with the OTP Team
------------------------------------------------

OTP Team usually takes a conservative approach to new features and
code. The team member may frequently and repeatedly review your PRs and
will suggest you to change the PRs for improvement. You are supposed to
follow their requests, unless you have a legitimate reason to oppose;
you need to find an agreement with the OTP Team, rather than to make a
confrontation, because time and other resources for the OTP Team is
limited. In short: OTP Team members have *no time to waste for
confrontational arguments*.

Rewriting a pull request
------------------------
  
Rewriting a pull request often results in a large number of commits,
where the purpose and meaning of each commit is hard to understand
later. OTP Team often request you to squash the commits to simplify the
committed code for easier understanding. Being able to handle ``git
rebase`` command is required for simplifying and streamlining your
commits. If you need to commit against the ``master`` branch, you may
frequently need to perform ``git rebase -i master``.
