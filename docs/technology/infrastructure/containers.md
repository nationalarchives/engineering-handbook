# Docker containers

1. **Approach**
    1. The `Dockerfile` and application configuration MUST use a production-by-default approach
    1. The required [healthcheck endpoints](#healthcheck-endpoints) MUST be added
    1. Development dependencies such as Pytest or Webpack MUST NOT appear in your production image (production by default)
    1. An application SHOULD use a single `Dockerfile` (having a separate `Dockerfile` for local development introduces potential differences between local and deployed applications)
    1. Configuration for lower environments (e.g. staging/dev) SHOULD extend and overwrite production values
    1. The [base Python images](../../resources/docker-images.md) SHOULD be used to build your application
    1. Setting environment variables during local development SHOULD be done in `docker-compose.yml` as it is not used outside of local development
    1. The [TNA application templates](../../resources/application-templates.md) COULD be used to start building your application
1. **Source control**
    1. You SHOULD use a single working branch; `main` and build production-ready images with every push to it
    1. You COULD build all images for pushes to any working/feature branch (allowing you to deploy an image for any feature branch)
    1. You COULD remove all images created from working/feature branches after you merge to `main`

## Healthcheck endpoints

Your container MUST expose at least one healthcheck endpoint.

Any implimented healthcheck endpoints MUST respond with a `200` HTTP status.

| Route                              | Expected content                             |
| ---------------------------------- | -------------------------------------------- |
| `/healthcheck/` (optional)         | Any truthy value (e.g. `ok`, `okay` or `up`) |
| `/healthcheck/live/`               | Any truthy value (e.g. `ok`, `okay` or `up`) |
| `/healthcheck/version/` (optional) | Application version (e.g. `26.04.14.12345`)  |
