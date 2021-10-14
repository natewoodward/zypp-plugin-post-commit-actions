A zypper plugin for executing arbitrary commands after a package is installed or removed.

## Install

Put `post-commit-actions` in `/usr/lib/zypp/plugins/commit`
and create folder `/etc/zypp/post-actions.d` .

## Usage

**/etc/zypp/post-actions.d/sample.action**

    # the format of each line is:
    #
    #    package:state:command
    #
    # package is a glob pattern matching a package name
    # state is one of: install, remove, any
    # command is a shell command
    #  the following are passed as environment variables to the command:
    #   $name  - package name
    #   $arch  - package arch
    #   $ver   - package version
    #   $rel   - package release
    #   $epoch - package epoch
    #   $state - state of the commit, i.e. "install" or "remove"
    
    *:install:touch /tmp/$name-installed
    zsh:remove:touch /tmp/zsh-removed
    zsh:install:touch /tmp/zsh-installed-also
    z*h:any:touch /tmp/bin-zsh-any

## Documentation

Project documentation can be found in these files:

* LICENSE - Terms and conditions
* README  - This document

