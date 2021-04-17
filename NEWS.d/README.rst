This is the directory for news fragments used by
`towncrier <https://github.com/hwkowl/towncrier>`_

New news fragments should be created for each Pull Request.
Do this from the top directory of the scons git, as that's
where the ``towncrier.toml`` configuration file is found.

Use one of the defined change categories, and a name that is
either the issue number if fixing a specific GitHub issue,
or an arbitrary, but descriptive, tag. An issue number is
preferred, but is not required.

Example::

    $ towncrier create --edit foo.bugfix

The defined categories are:
*feature*, *bugfix*, *doc*, *removal*, *misc*.
(*removal* includes both removals and deprecations).

The news fragments go into the ``next`` subdirectory,
and you should commit your fragment into the PR.
Use the category ``misc`` for changes to functionality
that aren't specifically "fix a bug".

When a release is made, it is generated as the file
``RELEASE.rst``, and all the fragments in ``next`` are
staged for removal with a ``git rm``. The maintainer
needs to commit this file as well as the removals,
and make a copy into a version-named file as well.

Example::

    $ towncrier build --version 4.2

You can use ``towncrier build --draft`` to see what
would be made without processing the removals and
actually creating the release file.
