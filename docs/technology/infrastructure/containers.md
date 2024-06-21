# Docker containers

## Working with Docker containers

As a general rule, we should approach working with Docker containers in the following way:

- Use a single working branch; `main`
- Start building your application with [Base Python images](#base-python-images)
- Build images for pushes to all working branches
- Clean up images created from working branches after you merge to `main`
- Regularly [delete untagged images](https://github.com/nationalarchives/ds-docker-actions/tree/main?tab=readme-ov-file#remove-untagged-docker-images)
- Add a healthcheck endpoint in your application `/healthcheck/live/` that returns a `200`

## Base Python images

Use one of the [TNA base Docker Python images](https://github.com/nationalarchives/docker). These will provide you with consistent Docker images of all your applications.

These base images:

- include common tools used within TNA (Poetry, nvm, Gunicorn, Uvicorn)
- extend the official Python images
- don't run as the `root` user
- work with the [Python frameworks used within TNA](../../backend/python/#frameworks) (Flask, Django and FastAPI)
- contain healthcheck definitons
- work for a number of preset environments
- can be customised in terms of their thread counts, worker numbers, log levels etc.
- build any NodeJS assets as part of their build process
- are linted with [hadolint](https://github.com/hadolint/hadolint) and [shellcheck](https://www.shellcheck.net/)
- can start up development NodeJS scripts to build assets in the background

### Simple example Dockerfile

```Dockerfile
FROM ghcr.io/nationalarchives/tna-python:latest

# Copy in the application code
COPY --chown=app . .

# Install dependencies
RUN tna-build

# Run the application
CMD ["tna-run", "my_application:app"]
```

### Advanced example Dockerfile

```Dockerfile
# This allows you to pass a build argument to change the image to a root level
# one such as tna-python-root
ARG IMAGE=ghcr.io/nationalarchives/tna-python

# This allows you to pass a build argument to change the base image version,
# for example in your local env, you could use the preview image
ARG IMAGE_TAG=latest

FROM "$IMAGE":"$IMAGE_TAG"

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

- a generated [calver version number](https://calver.org/) if the branch is `main` (e.g. `2024.06.21.1234`)
- the branch name (with slashes replaced with hyphens) for workflows triggered by pushes (e.g. `fix-a11y` or `feature-new-components`)
- the [semver version number](https://semver.org/) of the release for workflows triggered by tags with any prefixed `v` removed (e.g. `1.2.3` for the tag `v1.2.3` and `4` for the tag `v4`)
