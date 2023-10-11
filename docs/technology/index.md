# Our technology

## New applications

New National Archive applications SHOULD use the following approved languages and tools:

- [HTML](./html/)
- [JavaScript](./javascript/) - for either [progressive enhancement](../ways-of-working/progressive-enhancement) or for compiling web assets using tools like Webpack through NodeJS
- [CSS](./css/)
- [Python](./python/)
- [Postgres](./postgres/)
- [Docker](./containers/) - to create deployable containers
- [Terraform](./terraform/) - to provision and manage infrastructure in the cloud
- [Nginx](./nginx/) - to provide a reverse proxy in front of Docker containers

In addition to this, developers COULD also use:

- [TypeScript](./javascript/#typescript) - which must be compiled down to [JavaScript](./javascript/)
- [SCSS](./css/#sassscss) - allows us to more easily write CSS

Any other technologies MUST be proposed to and agreed by the [Technical Architects Group](../organisation/technical-architects-group/) through the process of [requesting changes](https://nationalarchives.github.io/developer-handbook/ways-of-working/documentation/#requesting-changes).

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

If you want to use one of these languages for a new project it first MUST be discussed with a member of the [Technical Architects Group](../organisation/technical-architects-group/) and/or the [Technical Governance Board](../organisation/technical-governance-board/).
