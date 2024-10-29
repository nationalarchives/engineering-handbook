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
