ATD Contribution Guidelines
==

This is a collection of guides to help contributors to the ATD
project.

Whenever possible, we prefer to automate things over having people
read documents and follow rules.

Releasing `atd`
--

The release process involves assigning a
[version ID](https://semver.org/), tagging a git commit with this
version ID, building an archive, and publishing the opam packages that
use this archive.
[dune-release](https://github.com/ocamllabs/dune-release) makes this
process easy and safe. Refer to its documentation for more information.

1. Review and update the changelog `CHANGES.md`.
2. Create a section with the desired version e.g. `2.3.0 (2022-03-10)`.
3. Commit the changes.
4. Install [dune-release](https://github.com/ocamllabs/dune-release)
   if not already installed:
   `opam install dune-release`
5. Run `dune-release tag`. It will pick up the version from the
   changelog and ask for confirmation.
6. Run `dune-release distrib` to create a tarball.
7. Run `dune-release publish` to upload the tarball to GitHub and
   create GitHub release including the changes extracted from the
   changelog.
8. Create opam packages with `dune-release opam pkg`.
9. Submit the opam packages to opam-repository using
   `dune-release opam submit`.

Contributing to a specific subproject
--

Each subproject has its own README:

* [atdgen](atdgen): targets OCaml, Bucklescript
* [atdj](atdj): targets Java
* [atdpy](atdpy): targets Python
* [atds](atds): targets Scala

Updating the documentation
--

### Documentation setup

The user documentation is published at https://atd.readthedocs.io/.
It's automatically published from the main branch of the GitHub repo
from the files found in `/doc`.

The [format of the documentation is Restructured
Text](https://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html#restructured-text-rest-and-sphinx-cheatsheet)
because it's more expressive that Markdown and it's not that hard to
pick up.

You can either edit the `.rst` files and hope that everything will
turn out fine or you can preview it by running Sphinx locally. The
latter is recommended for large edits. Try this:

Install sphinx and the theme we're using:
```
pip install -r doc/requirements.txt
```

Compile the documentation and run a local
[HTTP server on port 8888](http://0.0.0.0:8888):
```
make livedoc
```

### Writing good documentation

Don't assume that our existing documentation is already good (!)

Good documentation separates concerns. This not only makes it easy
to read but also easier to write.
Daniele Procida has a wonderful presentation about the four kinds of
documentation and why they're best kept separate:

* [website](https://documentation.divio.com/)
* [30-min presentation](https://www.youtube.com/watch?v=t4vKPhjcMZg)

![the four kinds of documentation](https://user-images.githubusercontent.com/343265/153692997-07752757-2227-4ba7-b53f-e5e85a71e71a.png)
