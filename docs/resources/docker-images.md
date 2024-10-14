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
- work with the [Python frameworks used within TNA](../technology/backend/python.md#frameworks) (Flask, Django and FastAPI)
- contain healthcheck definitons
- work for a number of preset environments
- can be customised in terms of their thread counts, worker numbers, log levels etc.
- can build any NodeJS assets as part of their build process
- are linted with [hadolint](https://github.com/hadolint/hadolint) and [shellcheck](https://www.shellcheck.net/)
- can start up development NodeJS scripts to build assets in the background

## Included scripts

### `tna-build`

1. Checks for the presence of `pyproject.toml` and `poetry.lock` files
1. If `$NPM_BUILD_COMMAND` is defined, run `tna-node "$NPM_BUILD_COMMAND"` (See [tna-node](#tna-node))
1. Installs `gunicorn`, `uvicorn`, `uvicorn-worker`
1. Installs `tool.poetry.dependencies` from `pyproject.toml`
    - `tna-python-dev` image also installs `tool.poetry.group.dev.dependencies`
1. In `tna-python-django`, collect all static assets if `django.contrib.staticfiles` is used

### `tna-node [command]`

1. Checks for the presence of `package.json`, `package-lock.json` and `.nvmrc` files
1. Sets the Node version to that defined in `.nvmrc`
1. Installs Node dependencies from `package.json`
1. Runs the passed `[command]` as `npm run [command]` (e.g. `build` from in `package.json`)

### `tna-run [-a] [application]`

1. In `tna-python-django`, run all database migrations
1. If `$ENVIRONMENT` is set to `develop` and `$NPM_DEVELOP_COMMAND` has been defined then run `tna-node "$NPM_DEVELOP_COMMAND"` (See [tna-node](#tna-node))
1. Calculate the default worker and thread count based on the number of CPU cores
1. If `$ENVIRONMENT` is set to `develop`:
    1. If Django is installed, run the Django development server
    1. Else if Flask is installed, run the Flask development server
    1. Else if FastAPI is installed, run uvicorn with reloading
    1. Else run the applciation through gunicorn with reloading using the async worker if the `-a` flag is passed
1. Else for any other environment, start `gunicorn` with values appropriate to the environment taking into account any overrides

### Included scripts in `tna-python-dev`

See [Commands for the Dockerfile](https://github.com/nationalarchives/docker/blob/main/docker/tna-python-dev/README.md#commands-for-the-dockerfile).

## Simple example Dockerfile

```Dockerfile
FROM ghcr.io/nationalarchives/tna-python:latest

# Copy in the application code
COPY --chown=app . .

# Install dependencies
RUN tna-build

# Run the application
CMD ["tna-run", "my_application:app"]
```

## Advanced example Dockerfile

```Dockerfile
# This allows you to pass a build argument to change the image to a root level
# one such as tna-python-root
ARG IMAGE=ghcr.io/nationalarchives/tna-python

# This allows you to pass a build argument to change the base image version,
# for example in your local env, you could use the preview image
ARG IMAGE_TAG=latest

FROM "$IMAGE":"$IMAGE_TAG"

# Using the Docker build scripts, you can accept a BUILD_VERSION and pass it in as an envrironment variable which will allow you to output the build version in the code
# https://github.com/nationalarchives/ds-docker-actions/blob/main/.github/actions/docker-build/action.yml#L34
ARG BUILD_VERSION
ENV BUILD_VERSION="$BUILD_VERSION"

# Provide a build command used from your package.json to build Node assets
ENV NPM_BUILD_COMMAND=compile

# Copy in the application code
COPY --chown=app . .

# Install dependencies
RUN tna-build

# Delete source files and tests
RUN rm -fR /app/src /app/test

# Run the application
CMD ["tna-run", "my_application:app"]
```

## Build Docker images in GitHub Actions

Use the [Docker build scripts](https://github.com/nationalarchives/ds-docker-actions) in your GitHub Actions to build images.

This script:

- runs the `Dockerfile` through [hadolint](https://github.com/hadolint/hadolint) ignoring rules `DL3045` and `DL3007`
- builds the image and tags it with the provided verion
- optionally tags the image with `latest`
- pushes the image to the container repository of the current project

### Computed version numbers

The [`get-version-tag` GitHub Action](https://github.com/nationalarchives/ds-docker-actions/tree/main/.github/actions/get-version-tag/action.yml) will provide you with a version tag to use for your images:

The version tag returned will be:

- a generated [calver version number](https://calver.org/) if the branch is `main` (e.g. `24.06.21.123`)
- the branch name (with slashes replaced with hyphens) for workflows triggered by pushes (e.g. `fix-a11y` or `feature-new-components`)
- the [semver version number](https://semver.org/) of the release for workflows triggered by tags with any prefixed `v` removed (e.g. `1.2.3` for the tag `v1.2.3` and `4` for the tag `v4`)


