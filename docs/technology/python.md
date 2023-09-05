# Python

- Version
    - The version of Python used SHOULD be 3.11
    - The version of Python used MUST be 3.8 or above
    - Python projects SHOULD use one of the [TNA base Docker images](/developer-handbook/resources/docker-images)
- Style
    - Python code SHOULD be styled with [Black](#black), [Flake8](#flake8) and [isort](#isort)
    - The maximum [cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity) of the code SHOULD be no larger than 20
- Dependencies
    - Python dependencies SHOULD be managed using [Poetry](#poetry)
- Frameworks and tools
    - Python applications SHOULD use [Django](https://www.djangoproject.com/)
    - Python applications COULD use [Wagtail](https://wagtail.org/)
    - Python applications COULD use [Flask](https://flask.palletsprojects.com/)
    - Python applications COULD use [Fabric](https://www.fabfile.org/)
    - Python applications COULD use [WTForms](https://wtforms.readthedocs.io/)
- Packages
    - Python packages SHOULD be made using pip
    - Python packages SHOULD be deployed to [PyPi](/developer-handbook/third-party/pypi)
    - Python packages COULD be hosted in [AWS CodeArtifact](https://aws.amazon.com/codeartifact/)

## Black

[Black](https://black.readthedocs.io/en/stable/) gives you speed, determinism, and freedom from pycodestyle nagging about formatting.

To ensure compatibility with Flake8 (sometimes the two disagree) the following config can be used in a `pyproject.toml` file:

```toml
[tool.black]
line-length = 80
```

## Flake8

[Flake8](https://flake8.pycqa.org/en/latest/) is a Python linting tool that checks your Python codebase for errors, styling issues and complexity and follows the [PEP 8 style guide](https://peps.python.org/pep-0008/) for Python code.

The following configuration can be set in a `.flake8` file to ensure all projects remain consistent and compliant with Black:

```toml
[flake8]
ignore = E501 # Line too long (82 > 79 characters)
max-line-length = 80
max-complexity = 20
```

`max-complexity` will put a limit on the [cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity) of the code.

## isort

The order of the imports can be standardised with [isort](https://pycqa.github.io/isort/).

Add the following configuration to your `pyproject.toml` file:

```toml
[tool.isort]
profile = "black"
```

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
