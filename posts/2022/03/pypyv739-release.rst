.. title: PyPy v7.3.9 security release
.. slug: pypy-v738-release
.. date: 2022-03-30 05:53:45 UTC
.. tags: release
.. category: 
.. link: 
.. description: 
.. type: rest
.. author: The PyPy Team

============================
PyPy v7.3.9 security release
============================

The PyPy team is proud to release version 7.3.9 of PyPy. This is a security
release to match the recent `CPython release`_ and updates the portable pypy
tarballs with ``bzip2 1.0.8``, ``openssl1.1.1n``, and ``libexpat 2.4.7``. Along
the way this release fixes some issues discovered after the 7.3.8 release and
updates ``sqlite3`` to 3.38.2. It includes:

  - PyPy2.7, which is an interpreter supporting the syntax and the features of
    Python 2.7 including the stdlib for CPython 2.7.18+ (the ``+`` is for
    backported security updates)

  - PyPy3.7,  which is an interpreter supporting the syntax and the features of
    Python 3.7, including the stdlib for CPython 3.7.13. This will be the last
    release of PyPy3.7.

  - PyPy3.8, which is an interpreter supporting the syntax and the features of
    Python 3.8, including the stdlib for CPython 3.8.13.

  - PyPy3.9, which is an interpreter supporting the syntax and the features of
    Python 3.9, including the stdlib for CPython 3.9.12. We relate to this as
    "beta" quality. We welcome testing of this version, if you discover
    incompatibilities, please report them so we can gain confidence in the version. 

The interpreters are based on much the same codebase, thus the multiple
release. This is a micro release, all APIs are compatible with the other 7.3
releases. Highlights of the release, since the release of 7.3.8 in February 2022,
include:

  - Fixed some failing stdlib tests on PyPy3.9
  - Update the bundled libexpat to 2.4.6 and sqlite3 to 3.38.2

We recommend updating. You can find links to download the v7.3.9 releases here:

    https://pypy.org/download.html

We would like to thank our donors for the continued support of the PyPy
project. If PyPy is not quite good enough for your needs, we are available for
direct consulting work. If PyPy is helping you out, we would love to hear about
it and encourage submissions to our blog_ via a pull request
to https://github.com/pypy/pypy.org

We would also like to thank our contributors and encourage new people to join
the project. PyPy has many layers and we need help with all of them: `PyPy`_
and `RPython`_ documentation improvements, tweaking popular modules to run
on PyPy, or general `help`_ with making RPython's JIT even better. Since the
7.3.7 release, we have accepted contributions from 6 new contributors,
thanks for pitching in, and welcome to the project!

If you are a python library maintainer and use C-extensions, please consider
making a HPy_ / CFFI_ / cppyy_ version of your library that would be performant
on PyPy.
In any case both `cibuildwheel`_ and the `multibuild system`_ support
building wheels for PyPy.

.. _`PyPy`: https://doc.pypy.org/
.. _`RPython`: https://rpython.readthedocs.org
.. _`help`: https://doc.pypy.org/en/latest/project-ideas.html
.. _CFFI: https://cffi.readthedocs.io
.. _cppyy: https://cppyy.readthedocs.io
.. _`multibuild system`: https://github.com/matthew-brett/multibuild
.. _`cibuildwheel`: https://github.com/joerick/cibuildwheel
.. _blog: https://pypy.org/blog
.. _HPy: https://hpyproject.org/
.. _`CPython release`: https://discuss.python.org/t/py-day-is-coming-a-joint-security-release-spree-for-python-3-7-3-8-3-9-and-3-10-on-march-14th

What is PyPy?
=============

PyPy is a Python interpreter, a drop-in replacement for CPython 2.7, 3.7, 3.8 and
3.9. It's fast (`PyPy and CPython 3.7.4`_ performance
comparison) due to its integrated tracing JIT compiler.

We also welcome developers of other `dynamic languages`_ to see what RPython
can do for them.

This PyPy release supports:

  * **x86** machines on most common operating systems
    (Linux 32/64 bits, Mac OS X 64 bits, Windows 64 bits, OpenBSD, FreeBSD)

  * 64-bit **ARM** machines running Linux. A shoutout to Huawei for sponsoring
    the VM running the tests.

  * **s390x** running Linux

  * big- and little-endian variants of **PPC64** running Linux,

PyPy support Windows 32-bit, PPC64 big- and little-endian, and ARM 32 bit, but
does not release binaries. Please reach out to us if you wish to sponsor
releases for those platforms.

.. _`PyPy and CPython 3.7.4`: https://speed.pypy.org
.. _`dynamic languages`: https://rpython.readthedocs.io/en/latest/examples.html

Known Issues with PyPy3.9
=========================

- We slightly modified the concurrent future's ``ProcessExcecutorPool`` to
  start all the worker processes when the first task is received (like on
  Python3.8) to avoid an apparent race condition when using ``fork`` and
  threads (issue 3650_).


What else is new?
=================

For more information about the 7.3.9 release, see the `full changelog`_.

Please update, and continue to help us make PyPy better.

Cheers,
The PyPy team

.. _`full changelog`: https://doc.pypy.org/en/latest/release-v7.3.9.html#changelog 
.. _3650: https://foss.heptapod.net/pypy/pypy/-/issues/3650
