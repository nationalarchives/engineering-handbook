# GitHub

1. **Branch protection**
    1. The main branch SHOULD be called `main`
    1. The main branch in public repositories MUST be protected such that:
        - A pull request is required before merging
        - At least 1 reviewer's approval is required to merge
        - [Signed commits](#commit-signing) are required
    1. The main branch in public repositories SHOULD be protected such that:
        - "Do not allow bypassing the above settings" is enabled
        - Dismiss stale pull request approvals when new commits are pushed
        - Require status checks to pass before merging - Note that pre-commit should be a check that always passes and any testing that must pass can also be easily enforced with the checks mechanism
        - Require branches to be up to date before merging - a sub option of the above (this can still be enabled even if there are no checks present)
1. **Naming conventions**
    1. Repositories SHOULD be prefixed with a department or project code (e.g. `ds-` for Digital Services, `da-` for Digital Archiving or `tdr-` for Transfer of Digital Records)
1. **Archiving projects/making read-only**
    1. Once no longer maintained, teams SHOULD [archive repositories](https://docs.github.com/en/repositories/archiving-a-github-repository/archiving-repositories)

## Commit signing

- https://github.com/microsoft/vscode/wiki/Commit-Signing

## GitHub Actions

[Deployment](../ways-of-working/deployment.md)
