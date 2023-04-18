=================
LOCKSS Downloader
=================

.. |RELEASE| replace:: 1.4.0-dev
.. |RELEASE_DATE| replace:: ?

.. |CURL| replace:: ``--curl/-curl/-C``
.. |DOWNLOAD_DIR| replace:: ``--download-dir/-download-dir/-d``
.. |GIT_BRANCH| replace:: ``--git-branch/-git-branch/-b``
.. |GIT_COMMIT| replace:: ``--git-commit/-git-commit/-c``
.. |GIT_TAG| replace:: ``--git-tag/-git-tag/-t``
.. |HELP| replace:: ``--help/-help/-h``
.. |HTTPIE| replace:: ``--httpie/-httpie/-H``
.. |QUIET| replace:: ``--quiet/-quiet/-q``
.. |VERSION| replace:: ``--version/-version``
.. |WGET| replace:: ``--wget/-wget/-W``

The LOCKSS Downloader is a script to download GitHub projects without Git, with Curl, Wget or HTTPie instead.

Invoke the LOCKSS Downloader, either `On the Fly`_ or `From a Local Copy`_, with a `GitHub Project Reference`_ (`Options`_ if needed), and the project will be downloaded from GitHub (by default into a directory in your home directory).

If no `GitHub Project Reference`_ is specified, the LOCKSS Downloader downloads the `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_, which is used to install and run the `LOCKSS 2.x system <https://docs.lockss.org/projects/manual>`_.

**Latest release:** |RELEASE| (|RELEASE_DATE|)

-----------------
Table of Contents
-----------------

*  `Prerequisites`_

*  `Usage`_

   *  `On the Fly`_

   *  `From a Local Copy`_

*  `Synopsis`_

*  `Options`_

   *  `GitHub Project Reference`_

   *  `Git Tree Options`_

   *  `Directory Options`_

   *  `Fetch Options`_

   *  `Other Options`_

*  `Advanced`_

-------------
Prerequisites
-------------

*  One of:

   *  `Curl <https://curl.se/>`_ (``curl``)

   *  `Wget <https://www.gnu.org/software/wget>`_ (``wget``)

   *  `HTTPie <https://httpie.io/>`_ (``http``)

*  One of:

   *  ``tar``

   *  ``gtar`` (MacOS only)

-----
Usage
-----

On the Fly
==========

In this mode of invocation, the LOCKSS Downloader script is fetched (with Curl, Wget or HTTPie), then immediately executed by the shell (with a `GitHub Project Reference`_, and `Options`_ if needed), without being stored on the host system::

    fetch_the_source_code | sh -s - [OPTIONS...] [PROJECT]

To invoke the LOCKSS Downloader in this mode, fetch https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader, and pipe the result into ``sh -s -``, optionally followed by `Options`_, optionally followed by a `GitHub Project Reference`_ (by default the `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_)::

    # With Curl:
    curl -sSfL https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader | sh -s - [OPTIONS...] [PROJECT]
    # With Wget:
    wget -qO- https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader | sh -s - [OPTIONS...] [PROJECT]
    # With HTTPie:
    http -qd https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader | sh -s - [OPTIONS...] [PROJECT]

From a Local Copy
=================

In this mode of invocation, you first download the LOCKSS Downloader script to the host system, then inspect it to your satisfaction, then run it yourself (with a `GitHub Project Reference`_, and `Options`_ if needed).

To invoke the LOCKSS Downloader in this mode:

1. Fetch https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader::

    # With Curl:
    curl -Lo lockss-downloader https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader
    # With Wget:
    wget -qO lockss-downloader https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader
    # With HTTPie
    http -qdo lockss-downloader https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader

   This will create the file ``lockss-downloader`` in the current directory.

2. Inspect ``lockss-downloader`` to your satisfaction.

3. Run ``chmod +x lockss-downloader`` to make ``lockss-downloader`` executable.

4. Run ``./lockss-downloader``, optionally followed by `Options`_, optionally followed by a `GitHub Project Reference`_ (by default the `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_)::

    ./lockss-downloader [OPTIONS...] [PROJECT]

--------
Synopsis
--------

You can see a detailed help message by invoking the LOCKSS Downloader (`On the Fly`_ or `From a Local Copy`_) with the |HELP| option::

    Usage:

      lockss-downloader [--curl|--httpie|--wget] [--download-dir=DIR] [--git-branch=BRA|
            --git-commit=COM|--git-tag=TAG] [--quiet] [PROJECT]
      lockss-downloader --version
      lockss-downloader --help

    Argument:

      PROJECT
            GitHub project reference (default: https://github.com/lockss/lockss-installer;
            format: https://github.com/X/Y or https://github.com/X/Y.git or
            git@github.com:X/Y or git@github.com:X/Y.git or X/Y where GitHub is
            implied)

    Options:

      --help, -help, -h
            display this message and exit
      --quiet, -quiet, -q
            produce no output unless an error occurs
      --version, -version
            display this program's version number and exit

    Git Tree Options:

      --git-branch=BRA, --git-branch BRA, -git-branch BRA, -b BRA
            use Git branch BRA (default: master)
      --git-commit=COM, --git-commit COM, -git-commit COM, -c COM
            use Git commit COM instead of a Git branch
      --git-tag=TAG, --git-tag TAG, -git-tag TAG, -t TAG
            use Git tag TAG instead of a Git branch

    Directory Options:

      --download-dir=DIR, --download-dir DIR, -download-dir DIR, -d DIR
            download into DIR (default: $HOME/$Y where Y is derived from the
            GitHub project reference https://github.com/X/Y)

    Fetch Options:

      --curl, -curl, -C
            force the use of Curl
      --httpie, -httpie, -H
            force the use of HTTPie
      --wget, -wget, -W
            force the use of Wget

-------
Options
-------

GitHub Project Reference
========================

If no `GitHub Project Reference`_ is specified, the LOCKSS Downloader downloads the `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_, which is used to install and run the `LOCKSS 2.x system <https://docs.lockss.org/projects/manual>`_.

Otherwise, the given GitHub project is downloaded, as specified in one of the following formats:

*  ``https://github.com/foo/bar``

*  ``https://github.com/foo/bar.git``

*  ``git@github.com:foo/bar``

*  ``git@github.com:foo/bar.git``

*  ``foo/bar`` (with GitHub implied, corresponding to ``https://github.com/foo/bar``)

Git Tree Options
================

By default, the LOCKSS Downloader downloads the head of the ``master`` branch of the project being downloaded, but you can change the target with options:

*  Use the |GIT_BRANCH| option to reference the head of a given branch (for example ``main`` or ``develop``).

*  Use the |GIT_TAG| or |GIT_COMMIT| options to reference the project as of a given tag (for example ``version-3.2.0`` or ``hotfix-3.2.1``) or commit (for example ``0a6c7cef5f426dbe7d4d6ab6d56a2414a6bff746``), respectively.

Directory Options
=================

By default, the LOCKSS Downloader downloads the target project ``https://github.com/X/Y`` into ``${HOME}/<Y>``, that is, a directory in the user's home directory whose name is derived from the Git repository name ``<Y>``. To specify your own destination directory, use the |DOWNLOAD_DIR| option.

Fetch Options
=============

By default, the LOCKSS Downloader detects one of Curl (``curl``), Wget (``wget``) or HTTPie (``http``) on the host system to perform the download, in this order, but you can force the choice with the |CURL|, |WGET| or |HTTPIE| options, respectively.

Other Options
=============

*  The |QUIET| option suppresses the summary displayed at the end of a successful download.

*  The |VERSION| option displays the version number of the LOCKSS Downloader, then exits.

--------
Advanced
--------

The URL https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader corresponds to the latest stable version of the LOCKSS Downloader, on the `main` branch of the `lockss-downloader Git repository <https://github.com/lockss/lockss-downloader>`_

.. tip::

   As a convenience, the shorter URL https://lockss.org/downlaoder redirects to https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader.

You can use a different version of the LOCKSS Downloader by modifying the URL:

*  For a given branch of the ``lockss-downloader`` Git repository, use ``https://github.com/lockss/lockss-downloader/raw/<branch>/lockss-downloader``, for example ``https://github.com/lockss/lockss-downloader/raw/develop/lockss-downloader`` for the ``develop`` branch. See https://github.com/lockss/lockss-downloader/branches.

*  For a given tag of the ``lockss-downloader`` Git repository, use ``https://github.com/lockss/lockss-downloader/raw/<tag>/lockss-downloader``, for example ``https://github.com/lockss/lockss-downloader/raw/version-1.2.0/lockss-downloader`` for the tag ``version-1.2.0``. See https://github.com/lockss/lockss-downloader/tags.

*  For a given commit of the ``lockss-downloader`` Git repository, use ``https://github.com/lockss/lockss-downloader/raw/<commit>/lockss-downloader``, for example ``https://github.com/lockss/lockss-downloader/raw/0a6c7cef5f426dbe7d4d6ab6d56a2414a6bff746/lockss-downloader`` for commit ``0a6c7cef5f426dbe7d4d6ab6d56a2414a6bff746``. See https://github.com/lockss/lockss-downloader/commits.
