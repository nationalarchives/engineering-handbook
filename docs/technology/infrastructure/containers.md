# Docker containers

## Working with Docker containers

As a general rule, we should approach working with Docker containers in the following way:

- Use a single working branch; `main`
- Start building your application with the [TNA application templates](../../resources/application-templates.md) or the [base Python images](../../resources/docker-images.md)
- Build images for pushes to all working branches
- Clean up images created from working branches after you merge to `main`
- Regularly [delete untagged images](https://github.com/nationalarchives/ds-docker-actions/tree/main?tab=readme-ov-file#remove-untagged-docker-images)
- Use production values by default and overwrite them for lower environments
- Add a healthcheck endpoint in your application `/healthcheck/live/` that returns a `200`
- Don't include development dependencies such as Pytest or Webpack in your production image
