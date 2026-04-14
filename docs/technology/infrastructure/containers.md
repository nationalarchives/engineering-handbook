# Docker containers

## Working with Docker containers

- The `Dockerfile` and application configuration MUST use a production-by-default approach
- You SHOULD use a single `Dockerfile` (having a separate `Dockerfile` for local development introduces potential differences between local and deployed applications)
- Configuration for lower environments (e.g. staging/dev) SHOULD extend and overwrite production values
- The [base Python images](../../resources/docker-images.md) SHOULD be used to build your application
- The [TNA application templates](../../resources/application-templates.md) COULD be used to start building your application
- The required [healthcheck endpoints](#healthcheck-endpoints) MUST be added
- Development dependencies such as Pytest or Webpack MUST NOT appear in your production image (production by default)
- Setting environment variables during local development SHOULD be done in `docker-compose.yml` as it is not used outside of local development

When working with source control, you COULD:

- Use a single working branch; `main`
- Build all images for pushes to any working branch
- Clean up images created from working branches after you merge to `main`

## Healthcheck endpoints

Your container MUST expose at least one healthcheck endpoint.

Any implimented healthcheck endpoints MUST respond with a `200` HTTP status.

| Route                              | Expected content                             |
| ---------------------------------- | -------------------------------------------- |
| `/healthcheck/` (optional)         | Any truthy value (e.g. `ok`, `okay` or `up`) |
| `/healthcheck/live/`               | Any truthy value (e.g. `ok`, `okay` or `up`) |
| `/healthcheck/version/` (optional) | Application version (e.g. `26.04.14.12345`)  |
