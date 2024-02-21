# Our technology

## New applications

New National Archive applications SHOULD be deployed to the [Public Cloud](aws.md) and use the following approved languages and tools:

- [HTML](html.md)
- [JavaScript](javascript.md) - for either [progressive enhancement](../ways-of-working/progressive-enhancement.md) or for compiling web assets using tools like Webpack through NodeJS
- [CSS](css.md)
- [Python](python.md)
- [Postgres](postgres.md)
- [Docker](containers.md) - to create deployable containers
- [Terraform](terraform.md) - to provision and manage infrastructure in the cloud
- [Nginx](nginx.md) - to provide a reverse proxy in front of Docker containers

In addition to this, engineers COULD also use:

- [TypeScript](javascript.md#typescript) - which must be compiled down to [JavaScript](javascript.md)
- [SCSS](css.md#sassscss) - allows us to more easily write CSS

Any other technologies MUST be proposed to and agreed by the [Technical Architects Group](../organisation/technical-architects-group.md) through the process of [requesting changes](https://nationalarchives.github.io/engineering-handbook/ways-of-working/documentation/#requesting-changes).

These decisions have been guided by [The GDS Way - Programming languages](https://gds-way.cloudapps.digital/standards/programming-languages.html).

There will be sensible reasons to not follow the above guidance on languages. For example when you're:

- extending an existing codebase or ecosystem
- scripting in a particular environment
- experimenting during an alpha (with an expectation that it's replaced by something we have more confidence in for beta)
- working in a very specific or unusual problem domain, like heavy use of WebSockets

The set of languages we're comfortable supporting will change over time.

## Other technologies

There are a number of existing applications which rely on technologies such as:

- .NET/ASP/C#
- Java
- PHP (used by a number of WordPress sites)
- Scala
- MongoDB
- Triplestore
- Perl
- Vue

If you want to use one of these languages for a new project it first MUST be discussed with a member of the [Technical Architects Group](../organisation/technical-architects-group.md) and/or the [Technical Governance Board](../organisation/technical-governance-board.md).
