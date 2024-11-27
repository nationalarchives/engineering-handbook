# Base Docker images

![Build status](https://img.shields.io/github/actions/workflow/status/nationalarchives/docker/build.yml?style=flat-square&event=push&branch=main)

- [Docker images source code on GitHub](https://github.com/nationalarchives/docker)
- [Docker images wiki on GitHub](https://github.com/nationalarchives/docker/wiki)
- [Docker container images on GitHub](https://github.com/orgs/nationalarchives/packages?repo_name=docker)

Use one of the TNA base Docker Python images which provide you with consistent Docker images of all your applications.

These base images:

- extend the official Python images
- include common tools used within TNA (Poetry, nvm, Gunicorn, Uvicorn)
- don't run as the `root` user
- are built for use on both `amd64` and `arm64` architectures
- work with the [Python frameworks used within TNA](../technology/backend/python.md#frameworks) (Flask, Django and FastAPI)
- contain healthcheck definitons
- work for a number of preset environments
- can be customised in terms of their thread counts, worker numbers, log levels etc.
- can build any NodeJS assets as part of their build process
- are linted with [hadolint](https://github.com/hadolint/hadolint) and [shellcheck](https://www.shellcheck.net/)
- can start up development NodeJS scripts to build assets in the background

## `tna-python`

Use the `tna-python` image to run Python applications.

To see examples of how to use the image, check out [example usage](https://github.com/nationalarchives/docker/wiki/Example-usage) on the base Docker images wiki or the [Django application template](https://github.com/nationalarchives/django-application-template).

## `tna-python-django`

The `tna-python-django` image extends `tna-python` but introduces the extra bits that Django requires such as a `manage.py` script and the introduction of a `DJANGO_SETTINGS_MODULE` environment variable.

## `tna-python-dev`

The `tna-python-dev` image can be used as a "buddy" to your development environment. It should mount the same application code as your main image so that it can support the application development.

Using the dev image will enable the installation of additional dependencies such as a test library. This avoids developmental dependencies being installed into production images.

The dev image has scripts for helping to [format your code](https://github.com/nationalarchives/docker/tree/main/docker/tna-python-dev#format) and run tasks/scripts within a standardised environment.

See how to [run scripts within a dev container](https://github.com/nationalarchives/docker/tree/main/docker/tna-python-dev#mountable-scripts).
