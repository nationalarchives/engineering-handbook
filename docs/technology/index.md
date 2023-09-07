# Our technology

## New applications

New National Archive applications SHOULD use the following approved languages and tools:

- [HTML](./html/)
- [Python](./python/)
- [JavaScript](./javascript/) - for either [progressive enhancement](../ways-of-working/service-standard/#progressive-enhancement) or for compiling web assets using tools like Webpack through NodeJS
- [CSS](./css/)
- [Postgres](./postgres/)
- [Docker](./containers/) - to create deployable containers
- [Nginx](./nginx/) - to provide a reverse proxy in front of Docker containers
- [Terraform](./terraform/) - to provision and manage infrastructure in the cloud

In addition to this, developers COULD also use:

- [TypeScript](./javascript/#typescript) - which must be compiled down to [JavaScript](./javascript/)
- [SCSS](./css/#sassscss) - allows us to more easily write CSS

Any other technologies MUST be proposed to and agreed by the [Technical Governance Board](../organisation/technical-governance-board/) through the process of [requesting changes](https://nationalarchives.github.io/developer-handbook/ways-of-working/documentation/#requesting-changes).

## Existing technologies

There are a number of existing applications which rely on technologies such as:

- .NET
- ASP
- C#
- Java
- PHP (used by a number of WordPress sites)
- Scala
- MongoDB
- Triplestore
- Perl
- Vue

The choice to use any of these technologies for new projects MUST be discussed with a member of the [Technical Governance Board](../organisation/technical-governance-board/).
