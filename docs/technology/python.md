# Python

Approved versions of Python:

- 3.11 (recommended)
- 3.10
- 3.9

When making a [Python Docker](https://hub.docker.com/_/python) application, aim to use one of the `python:3.x-slim` (bullseye) images:

- `python:3.11-slim`
- `python:3.10-slim`
- `python:3.9-slim`

## Code style

All Python code should be styled with [Black](https://black.readthedocs.io/en/stable/) and then [Flake8](https://flake8.pycqa.org/en/latest/).

### Black

To ensure compatibility with Flake8 (sometimes the two disagree) the following config can be used in a `pyproject.toml` file.

```toml
[tool.black]
line-length = 79
include = '\.pyi?$'
```

### Flake8

Flake8 follows the [PEP 8 style guide](https://peps.python.org/pep-0008/) for Python code.

The following configuration can be set in a `.flake8` file to ensure all projects remain consistent.

```toml
[flake8]
ignore = E203, E266, E501, W503, F403, F401
max-line-length = 79
max-complexity = 18
select = B,C,E,F,W,T4,B9
```

### isort

The order of the imports can be standardised with [isort](https://pycqa.github.io/isort/). Add the following configuration to your `pyproject.toml` file:

```toml
[tool.isort]
profile = "black"
```

## Dependencies

[TODO]

- pip/Poetry
- Django
- Wagtail
- Fabric
- WTForms

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
