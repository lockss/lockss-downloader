=================
LOCKSS Downloader
=================

.. |RELEASE| replace:: 1.5.0
.. |RELEASE_DATE| replace:: 2026-04-08

.. |CURL| replace:: ``--curl/-curl/-C``
.. |DOWNLOAD_DIR| replace:: ``--download-dir/-download-dir/-d``
.. |GIT_BRANCH| replace:: ``--git-branch/-git-branch/-b``
.. |GIT_COMMIT| replace:: ``--git-commit/-git-commit/-c``
.. |GIT_TAG| replace:: ``--git-tag/-git-tag/-t``
.. |HELP| replace:: ``--help/-help/-h``
.. |QUIET| replace:: ``--quiet/-quiet/-q``
.. |VERSION| replace:: ``--version/-version``
.. |WGET| replace:: ``--wget/-wget/-W``

The LOCKSS Downloader is a script to download GitHub projects without Git, with Curl or Wgetinstead.

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

*  One of:

   *  ``tar``

   *  ``gtar`` (MacOS only)

-----
Usage
-----

On the Fly
==========

In this mode of invocation, the LOCKSS Downloader script is fetched (with Curl or Wget), then immediately executed by the shell (with a `GitHub Project Reference`_, and `Options`_ if needed), without being stored on the host system::

    fetch_the_source_code | sh -s - [OPTIONS...] [PROJECT]

To invoke the LOCKSS Downloader in this mode, fetch https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader, and pipe the result into ``sh -s -``, optionally followed by `Options`_, optionally followed by a `GitHub Project Reference`_ (by default the `LOCKSS Installer <https://github.com/lockss/lockss-installer>`_)::

    # With Curl:
    curl -sSfL https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader | sh -s - [OPTIONS...] [PROJECT]
    # With Wget:
    wget -qO- https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader | sh -s - [OPTIONS...] [PROJECT]

From a Local Copy
=================

In this mode of invocation, you first download the LOCKSS Downloader script to the host system, then inspect it to your satisfaction, then run it yourself (with a `GitHub Project Reference`_, and `Options`_ if needed).

To invoke the LOCKSS Downloader in this mode:

1. Fetch https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader::

    # With Curl:
    curl -Lo lockss-downloader https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader
    # With Wget:
    wget -qO lockss-downloader https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader

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
      lockss-downloader [--download-dir=DIR] [--branch=BRA|--commit=COM|--tag=TAG] [--curl|--wget] [--quiet] [PROJECT]
      lockss-downloader --version
      lockss-downloader --help
    
    PROJECT argument format (default: https://github.com/lockss/lockss-installer)
      https://github.com/<x>/<y>
      https://github.com/<x>/<y>.git
      git@github.com:<x>/<y>
      git@github.com:<x>/<y>.git
      <x>/<y> (GitHub implied)
    
    Directory options
          --download-dir, -d DIR  Download into DIR (default: $HOME/<y> with <y> from PROJECT)
    
    Git options (default: master branch of PROJECT)
          --branch, --git-branch, -b BRA 
                                  Use the Git branch BRA (deprecated: --git-branch)
          --commit, --git-commit, -c COM 
                                  Use the Git commit COM (deprecated: --git-commit)
          --tag, --git-tag, -t TAG 
                                  Use the Git tag TAG (deprecated: --git-tag)
    
    Downloader options (default: Curl then Wget)
          --curl, -C              Force the use of Curl
          --wget, -W              Force the use of Wget
    
    Other options
          --help, -h              Display this help message and exit
          --quiet, -q             Produce no output unless an error occurs
          --version               Display the version and exit


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

By default, the LOCKSS Downloader detects one of Curl (``curl``) or Wget (``wget``) on the host system to perform the download, in this order, but you can force the choice with the |CURL| or |WGET| options, respectively.

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
