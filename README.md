# `lockss-downloader`

The LOCKSS Downloader is a script to download GitHub projects (by default the LOCKSS Installer) with `curl` or `wget`.

## Prerequisites

The LOCKSS Downloader requires:

*   `curl` or `wget`

*   `tar` or `gtar`

## Invoking

### On the Fly

To invoke the LOCKSS Downloader on the fly:

1.  Use `curl -sSfL` or `wget -qO-` to fetch <https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader>, then pipe the result into `sh -s -` optionally followed by the desired options. For example:

    ```shell
    curl -sSfL https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader | sh -s - --git-project=https://github.com/lockss/lockss-installer
    ```

    or:

    ```shell
    wget -qO- https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader | sh -s - --help
    ```

### From a Local Copy

To create and use a local copy of the LOCKSS Downloader:

1.  Use `curl -Lo lockss-downloader` or `wget` to fetch <https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader>.

2.  Inspect `lockss-downloader` to your satisfaction.

3.  Run `chmod +x lockss-downloader` to make `lockss-downloader` executable.

4.  Run `./lockss-downloader` optionally followed by the desired options. For example:

    ```shell
    ./lockss-downloader --git-project=https://github.com/lockss/lockss-installer
    ```

    or:

    ```shell
    ./lockss-downloader --help
    ```

## Options

*   For a list of all supported options, invoke `lockss-downloader` with `--help`.

*   **By default, the LOCKSS Downloader downloads the [LOCKSS Installer](https://github.com/lockss/lockss-installer)**, but you can specify any GitHub project with `--git-project=${project}`, where `${project}` is in one of the following equivalent styles:

    *   `https://github.com/foo/bar`

    *   `https://github.com/foo/bar.git`

    *   `git@github.com:foo/bar`

    *   `git@github.com:foo/bar.git`

    *   `foo/bar` (GitHub implied)

*   By default, the LOCKSS Downloader downloads the `master` branch of the target project, but you can specify any branch with `--git-branch=${branch}`, or tag with `--git-tag=${tag}`, or commit with `--git-commit=${commit}`.

*   By default, the LOCKSS Downloader downloads the target project <https://github.com/foo/bar> into `${HOME}/bar` (i.e. derived from the repository name), but you can specify the target directory of your choice with `--download-dir=${dir}`.

*   With `--version`, the LOCKSS Downloader displays its version number and exits.

## Running a Particular Version

The URL <https://github.com/lockss/lockss-downloader/raw/main/lockss-downloader> corresponds to the latest stable version of the LOCKSS Downloader, on the `main` branch of its Git repository <https://github.com/lockss/lockss-github-download>, but you can substitute a different URL:

*   For a given branch of the `lockss-downloader` Git repository, use <https://github.com/lockss/lockss-downloader/raw/${branch}/lockss-downloader>, for example <https://github.com/lockss/lockss-downloader/raw/develop/lockss-downloader> for the `develop` branch. See <https://github.com/lockss/lockss-downloader/branches>.

*   For a given tag of the `lockss-downloader` Git repository, use <https://github.com/lockss/lockss-downloader/raw/${tag}/lockss-downloader>, for example <https://github.com/lockss/lockss-downloader/raw/version-1.2.0/lockss-downloader> for the tag `version-1.2.0`. See <https://github.com/lockss/lockss-downloader/tags>.

*   For a given commit of the `lockss-downloader` Git repository, use <https://github.com/lockss/lockss-downloader/raw/${commit}/lockss-downloader>, for example <https://github.com/lockss/lockss-github-download/raw/c8760ff347ce9cd3ed483e8bceb3ab7783ef274a/lockss-downloader> for commit `c8760ff347ce9cd3ed483e8bceb3ab7783ef274a`. See <https://github.com/lockss/lockss-downloader/commits>.
