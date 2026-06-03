# Python

1. **Version**
    1. The version of Python used MUST be 3.10 or above
    1. Python projects SHOULD use one of the [TNA base Docker images](../../resources/docker-images.md)
1. **Style/linting**
    1. Python code SHOULD be styled with [Ruff](#linting-and-formatting)
    1. The maximum [cyclomatic complexity](#cyclomatic-complexity) of the code MUST be no larger than 20
    1. The maximum [cyclomatic complexity](#cyclomatic-complexity) of the code SHOULD be no larger than 12
    1. Line lengths SHOULD NOT exceed 88 characters
    1. Absolute imports SHOULD be used
    1. Relative imports COULD be used for importing files within the same directory
1. **Dependencies**
    1. Python dependencies SHOULD be managed using [Poetry](#poetry)
1. **Frameworks, tools and libraries**
    1. Python applications MUST use one of the approved [frameworks](#frameworks)
1. **Building packages**
    1. Python packages SHOULD be built using pip or Poetry
    1. Python packages SHOULD be deployed to [PyPI](../../third-party/pypi.md)
    1. Python packages COULD be hosted in [AWS CodeArtifact](https://aws.amazon.com/codeartifact/)
1. **Security**
    1. A CSP SHOULD be set up

## Frameworks

Use either [Flask](https://flask.palletsprojects.com/), [Django](https://www.djangoproject.com/) or [FastAPI](https://fastapi.tiangolo.com/) for your Python applications.

| Framework                                   | Best choice for making                                 |
| ------------------------------------------- | ------------------------------------------------------ |
| [Flask](https://flask.palletsprojects.com/) | Applications with a UI                                 |
| [Django](https://www.djangoproject.com/)    | Applications that need to work with data and databases |
| [FastAPI](https://fastapi.tiangolo.com/)    | RESTful JSON APIs                                      |

[Application templates](../../resources/application-templates.md) have been made for new projects to enable you to get started much quicker.

## Tools and libraries

Some suggested tools and libraries for Python applications are:

| Tool/library                                                                  | Use case                                                             |
| ----------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| [National Archives Python Utilities](https://pypi.org/project/tna-utilities/) | Helpful library of common functions                                  |
| [Wagtail](https://wagtail.org/)                                               | Services that require a CMS                                          |
| [WTForms](https://wtforms.readthedocs.io/)                                    | Validating form inputs from Flask applications                       |
| [WhiteNoise](https://github.com/evansd/whitenoise)                            | Serving static files in production from `django.contrib.staticfiles` |

When choosing other tools and libraries, pay close attention to the [licences](../standards/licences.md).

Aim to use as few libraries as possible. Using small or unnecessarily libraries widens our attack surface and slows down our build times. If in doubt, talk to a lead developer.

## Linting and formatting

The National Archives uses [Ruff](https://docs.astral.sh/ruff/) as a Python linter and formatter.

The two published [National Archives Ruff configurations](https://github.com/nationalarchives/ruff-config) available are:

- `ruff.toml` - a general purpose Ruff configuration
- `ruff-strict.toml` - a configuration with a stricter set of rules

### Cyclomatic complexity

When using the standard `ruff.toml` configuration, the [cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity) of the code is set to a maximum of `20`. When using `ruff-strict.toml`, the maximum complexity is reduced to `12`.

### Using the dev Docker image

The [Dev Docker image](https://github.com/nationalarchives/docker/tree/main/docker/tna-python-dev) comes preinstalled with Ruff as well as all the National Archives configurations.

You can use it as a drop-in replacement for the main Python image by configuring your `docker-compose.yml`:

```Dockerfile
services:
  app:
    build:
      context: .
      args:
        IMAGE: ghcr.io/nationalarchives/tna-python-dev
        IMAGE_TAG: preview
```

Now you can lint your code by running:

```sh
docker compose exec app format
```

Alternatively, you can simply run `format` inside the `app` container. Read more about [formatting code in `tna-python-dev`](https://github.com/nationalarchives/docker/tree/main/docker/tna-python-dev#format).

## Poetry

[Poetry](https://python-poetry.org/) is a tool for dependency management and packaging in Python.
