# PKGBUILD management framework for the [Makedeb Package Repository](https://mpr.makedeb.com)

## Install
The standard `make && sudo make install` routine is used. The following additional variables are supported:
* `DESTDIR` -- staged installs for distro packaging
* `PREFIX` -- where to install generated script, defaults to /usr/local
* `HOOKSDIR` -- where to install [githooks](#hooks), defaults to `<PREFIX>/share/mprpublish`

## How it works
Commit PKGBUILDs in named subdirectories. Export them to the MPR with the `mprpublish` command, using the subtree push stratagem.
This preserves an independent history for third-party hosting, pull requests... ;)

## Commands
* `mprpublish setup`
> Initialize a new repository with [githooks](#hooks).

* `mprpublish PACKAGE`
> Push PACKAGE to the MPR. With "--speedup", merges the split history back in.

* `mprpublish -p PACKAGE`
> Pull package from the MPR (if you adopted an existing package, or have a co-maintainer).

* `mprpublish log PACKAGE`
> View the git log of a package subtree.

* `import-from-aur3.sh PACKAGE`
> Experimental. Download the history of a non-migrated AUR3 package, and commit it to a new subtree.

## Hooks
* pre-commit
> Warn about whitespace errors, fail if checksums don't match, and auto-generate .SRCINFO for all changed PKGBUILDs.

* prepare-commit-msg
> Prefill the commit message with a list of added/updated/deleted packages + versions (if any).

## Copyright
This repository is licensed under the GPLv2 or (at your option) any later version.
