# Version control

- Branching strategy
- Versioning

All TNA projects should be structured in a fairly similar manner. Consistency allows easier transfer of knowledge between projects and departments.

## Starting a new project

### Readme

A `README.md` written in markdown MUST be present and populated explaining the repository's purpose.

### Licence

The repository MUST contain a `LICENCE` or `LICENCE.txt` file.

Read more about [licences at TNA](../technology/standards/licences.md).

### Changelog

A changelog SHOULD be kept in the root of the repository.

Changelogs MUST use the [keep a changelog](https://keepachangelog.com/en/1.1.0/) standard.

## Using pull requests for peer review

All code should be reviewed using the pull request process before it is merged or deployed. This review should ensure all relevant standards are met.

## Version numbers

If your code is intended to be consumed by other services such as a library, use [semver](https://semver.org/).

If your code is an application that is regularly released, use [calver](https://calver.org/).
