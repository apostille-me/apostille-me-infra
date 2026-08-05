# apostille-me-infra (superseded)

> This repository is frozen. The canonical source of truth is [`apme-infra`](https://github.com/apostille-me/apme-infra).

The organization was bootstrapped with both short-name and full-name scaffolds. The short repository is the canonical implementation. This repository remains available only for history and provenance.

## Migrate

- Open issues, pull requests, releases, and new work in `apostille-me/apme-infra`.
- Point any retained submodule at `apostille-me/apme-infra` and classify it according to the canonical monorepo's composition policy.
- Prefer Zed packages for application dependencies; infrastructure repositories should not become runtime package dependencies.
- For intentionally retained source submodules, use:

  ```bash
  git submodule update --init --recursive
  zed install --git-submodules
  ```

Do not source the same repository through both Zed and a gitlink.

No source is removed by this consolidation. Git history remains intact; genuinely unique infrastructure changes should be ported to the canonical repository in a reviewed PR before an organization administrator archives this repository.
