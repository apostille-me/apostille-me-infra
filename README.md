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

## Environment secrets

Secrets live in this repo **encrypted** with [sops](https://github.com/getsops/sops) + [age](https://github.com/FiloSottile/age):
`env/enc/<dev|prod>.env.enc` is committed; `just env-use <name>` decrypts it to
`env/dec/<name>.env` (gitignored, mode 0600) and symlinks `./.env` to it. The
Nix dev shell provides the tooling, `just env-audit` runs keyless in CI, and
containers decrypt at `docker run` — never at build. See [`env/README.md`](env/README.md).
