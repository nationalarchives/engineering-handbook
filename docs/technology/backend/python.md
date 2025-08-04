# Python

1. **Version**
    1. The version of Python used SHOULD be 3.11 or above
    1. The version of Python used MUST be 3.8 or above
    1. Python projects SHOULD use one of the [TNA base Docker images](../../resources/docker-images.md)
1. **Style/linting**
    1. Python code MUST be styled with [Black](#black), [Flake8](#flake8) and [isort](#isort)
    1. The maximum [cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity) of the code MUST be no larger than 20
    1. The maximum cyclomatic complexity of the code SHOULD be no larger than 12
    1. Line lengths SHOULD NOT exceed 80 characters
    1. Absolute imports SHOULD be used
    1. Relative imports COULD be used for importing files within the same directory
1. **Dependencies**
    1. Python dependencies SHOULD be managed using [Poetry](#poetry)
1. **Frameworks, tools and libraries**
    1. Python applications MUST use one of the approved [frameworks](#frameworks)
1. **Packages**
    1. Python packages SHOULD be made using pip
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

| Tool/library                                                            | Use case                                                                                    |
| ----------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [Wagtail](https://wagtail.org/)                                         | Services that require a CMS                                                                 |
| [WTForms](https://wtforms.readthedocs.io/)                              | Validating form inputs from Flask applications                                              |
| [flask-talisman](https://github.com/GoogleCloudPlatform/flask-talisman) | Adding a [CSP and other security measures](../standards/security.md) to Flask applications  |
| [django-csp](https://github.com/mozilla/django-csp)                     | Adding a [CSP and other security measures](../standards/security.md) to Django applications |
| [WhiteNoise](https://github.com/evansd/whitenoise)                      | Serving static files in production from `django.contrib.staticfiles`                        |

When choosing other tools and libraries, pay close attention to the [licences](../standards/licences.md).

Aim to use as few libraries as possible. Using small or unnecessarily libraries widens our attack surface and slows down our build times. If in doubt, talk to a lead developer.

## Formatters and linters

### Black

[Black](https://black.readthedocs.io/en/stable/) gives you speed, determinism, and freedom from pycodestyle nagging about formatting.

To ensure compatibility with Flake8 (sometimes the two disagree) the following config can be used in a `pyproject.toml` file:

```toml
[tool.black]
line-length = 80
include = '\.pyi?$'
```

### Flake8

[Flake8](https://flake8.pycqa.org/en/latest/) is a Python linting tool that checks your Python codebase for errors, styling issues and complexity and follows the [PEP 8 style guide](https://peps.python.org/pep-0008/) for Python code.

The following configuration can be set in a `.flake8` file to ensure all projects remain consistent and compliant with Black:

```toml
[flake8]
ignore = E203, E266, E501, W503, F403, F401
exclude = venv*,__pycache__,node_modules,migrations
max-line-length = 80
max-complexity = 12
select = B,C,E,F,W,T4,B9
```

`max-complexity` will put a limit on the [cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity) of the code.

Note: you can also ignore rules on particular lines of code or files by adding a # noqa comment - see [flake8's noqa syntax](https://flake8.pycqa.org/en/latest/user/violations.html#in-line-ignoring-errors).

If using the `tna-python-dev` Docker image, [this Flake8 configuration is included](https://github.com/nationalarchives/docker/blob/main/docker/tna-python-dev/lib/.flake8).

### isort

The order of the imports can be standardised with [isort](https://pycqa.github.io/isort/).

Add the following configuration to your `pyproject.toml` file:

```toml
[tool.isort]
profile = "black"
```

### Dev Docker image

The [Dev Docker image](https://github.com/nationalarchives/docker/tree/main/docker/tna-python-dev) comes preinstalled with Black, Flake8 and isort. It also includes all the relevant [configurations](https://github.com/nationalarchives/docker/tree/main/docker/tna-python-dev/lib).

You can use it to lint your code by mounting the container image with your project code in your `docker-compose.yml`:

```Dockerfile
services:
  dev:
    image: ghcr.io/nationalarchives/tna-python-dev:latest
    volumes:
      - ./:/app
```

Now you can lint your code by running:

```sh
docker compose exec dev format
```

Alternatively, you can simply run `format` inside the container.

## Poetry

[Poetry](https://python-poetry.org/) is a tool for dependency management and packaging in Python.

## PEP 20 – The Zen of Python

If in doubt, consult [The Zen of Python](https://peps.python.org/pep-0020/):

```
Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```
