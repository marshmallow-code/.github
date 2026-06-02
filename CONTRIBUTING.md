# Contributing guidelines

So you're interested in contributing to one of our [marshmallow-code projects](https://github.com/marshmallow-code)? That's awesome! We welcome contributions from anyone willing to work in good faith with other contributors and the community (see also our [Code of Conduct](./CODE_OF_CONDUCT.md)).

> [!NOTE]
> These guidelines apply to every project in the [marshmallow-code](https://github.com/marshmallow-code) organization. Throughout this document, replace `<repo>` with the name of the repository you're contributing to (e.g. `marshmallow`, `webargs`, `apispec`).

> [!IMPORTANT]
> If you use LLM / "AI" tools for your contributions, please read and follow our [_Generative AI / LLM Policy_](./AI_POLICY.md).

## Questions, feature requests, bug reports, and feedback…

…should all be reported on the relevant project's GitHub issue tracker, at `https://github.com/marshmallow-code/<repo>/issues`.

## Ways to contribute

- Comment on some of the project's [open issues](https://github.com/marshmallow-code). Share a solution or workaround. Make a suggestion for how a feature can be made better. Opinions are welcome!
- Improve the docs. For straightforward edits, click the edit button in the top-right corner of the page. See the [Documentation](#documentation) section below if you want to build the docs locally.
- If you think you've found a bug, open an issue.
- Send a PR for an open issue (especially one labeled "help wanted"). The next section details how to contribute code.

## Contributing code

### Setting up for local development

1.  Fork the repository on GitHub.

``` shell-session
$ git clone https://github.com/marshmallow-code/<repo>.git
$ cd <repo>
```

2.  Install [uv](https://docs.astral.sh/uv/getting-started/installation/).
3.  Install development requirements.

``` shell-session
$ uv sync
```

4.  (Optional but recommended) Install the pre-commit hooks, which will format and lint your git staged files.

``` shell-session
$ uv run pre-commit install --allow-missing-config
```

### Git branch structure

Our projects abide by the following branching model:

`dev`
Current development branch. **New features should branch off here**.

`X.Y-line`
Maintenance branch for release `X.Y`. **Bug fixes should be sent to the most recent release branch.** A maintainer will forward-port the fix to `dev`. Note: exceptions may be made for bug fixes that introduce large code changes.

**Always make a new branch for your work**, no matter how small. Also, **do not put unrelated changes in the same branch or pull request**. This makes it more difficult to merge your changes.

### Pull requests

1.  Create a new local branch.

For a new feature:

``` shell-session
$ git checkout -b name-of-feature dev
```

For a bugfix:

``` shell-session
$ git checkout -b fix-something X.Y-line
```

2.  Commit your changes. Write [good commit messages](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html).

``` shell-session
$ git commit -m "Detailed commit message"
$ git push origin name-of-feature
```

3.  Before submitting a pull request, check the following:

- If the pull request adds functionality, it is tested and the docs are updated.
- You've added yourself to `AUTHORS.rst`, if the project has one.

4.  Submit a pull request to the `dev` branch or the appropriate maintenance branch. The CI build must be passing before your pull request is merged.

### Running tests

To run all tests:

``` shell-session
$ uv run pytest
```

To run formatting and syntax checks:

``` shell-session
$ uv run tox -e lint
```

(Optional) To run tests in all supported Python versions in their own virtual environments (must have each interpreter installed):

``` shell-session
$ uv run tox
```

### Documentation

Contributions to the documentation are welcome. Documentation is written in [reStructuredText](https://docutils.sourceforge.io/rst.html) (rST). A quick rST reference can be found [here](https://docutils.sourceforge.io/docs/user/rst/quickref.html). Builds are powered by [Sphinx](https://www.sphinx-doc.org/).

To build and serve the docs in "watch" mode:

``` shell-session
$ uv run tox -e docs-serve
```

Changes to documentation will automatically trigger a rebuild.
