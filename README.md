# `lockss-github-download`

## Prerequisites

`lockss-github-download` requires:

*   `curl` or `wget`

*   `tar` or `gtar`

## Invoking

### On the Fly

To invoke `lockss-github-download` on the fly:

1.  Use `curl -sSfL` or `wget -qO-` to fetch <https://github.com/lockss/lockss-github-download/raw/main/lockss-github-download>, then pipe the result into `sh -s -` optionally followed by the desired options. For example:

    ```shell
    curl -sSfL https://github.com/lockss/lockss-github-download/raw/main/lockss-github-download | sh -s - --git-project=https://github.com/lockss/lockss-installer
    ```

    or:

    ```shell
    wget -qO- https://github.com/lockss/lockss-github-download/raw/main/lockss-github-download | sh -s - --help
    ```

### From a Downloaded Copy

To invoke a downloaded copy of `lockss-github-download`:

1.  Use `curl -Lo lockss-github-download` or `wget` to fetch <https://github.com/lockss/lockss-github-download/raw/main/lockss-github-download>.

2.  Inspect `lockss-github-download` to your satisfaction.

3.  Run `chmod +x lockss-github-download` to make `lockss-github-download` executable.

4.  Run `./lockss-github-download` optionally followed by the desired options. For example:

    ```shell
    ./lockss-github-download --git-project=https://github.com/lockss/lockss-installer
    ```

    or:

    ```shell
    ./lockss-github-download --help
    ```

## Options

*   For a list of all supported options, invoke `lockss-github-download` with `--help`.

*   By default, `lockss-github-download` downloads <https://github.com/lockss/lockss-installer>, but you can specify any GitHub project with `--git-project=${project}`, where `${project}` is in one of the following equivalent styles:

    *   `https://github.com/foo/bar`

    *   `https://github.com/foo/bar.git`

    *   `git@github.com:foo/bar`

    *   `git@github.com:foo/bar.git`

    *   `foo/bar` (GitHub implied)

*   By default, `lockss-github-download` downloads the `master` branch of the target project, but you can specify any branch with `--git-branch=${branch}`, or tag with `--git-tag=${tag}`, or commit with `--git-commit=${commit}`.

*   By default, `lockss-github-download` downloads the target project <https://github.com/foo/bar> into `${HOME}/bar-download` (i.e. derived from the repository name by adding `-download`), but you can specify the target directory of your choice with `--download-dir=${dir}`.

*   By default, `lockss-github-download` replaces the target directory wholesale, but you can request that it keep a backup copy of the existing download directory with `--keep-previous` by renaming to a name with a unique suffix.

*   With `--version`, `lockss-github-download` displays its version number and exits.

## Running a Particular Version

The URL <https://github.com/lockss/lockss-github-download/raw/main/lockss-github-download> corresponds to the latest stable  version of `lockss-github-download`, on the `main` branch of its Git repository <https://github.com/lockss/lockss-github-download>, but you can substitute a different URL:

*   For a given branch of the `lockss-github-download` Git repository, use <https://github.com/lockss/lockss-github-download/raw/${branch}/lockss-github-download>, for example <https://github.com/lockss/lockss-github-download/raw/develop/lockss-github-download> for the `develop` branch. See <https://github.com/lockss/lockss-github-download/branches>.

*   For a given tag of the `lockss-github-download` Git repository, use <https://github.com/lockss/lockss-github-download/raw/${tag}/lockss-github-download>, for example <https://github.com/lockss/lockss-github-download/raw/version-1.0.0/lockss-github-download> for the tag `version-1.0.0`. See <https://github.com/lockss/lockss-github-download/tags>.

*   For a given commit of the `lockss-github-download` Git repository, use <https://github.com/lockss/lockss-github-download/raw/${commit}/lockss-github-download>, for example <https://github.com/lockss/lockss-github-download/raw/ec60067fdcdbee6148e139c77ce92d43aba75637/lockss-github-download> for commit `ec60067fdcdbee6148e139c77ce92d43aba75637`. See <https://github.com/lockss/lockss-github-download/commits>.
