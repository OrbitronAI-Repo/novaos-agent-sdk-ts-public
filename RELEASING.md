# Release Process

Publishes `novaos-agent-sdk` to npm via GitHub Actions trusted publishing (OIDC) —
no npm token stored in this repo.

## One-time setup (do before first release)

1. Create the `orbitronai` npm org at npmjs.com (or publish under an existing org/user
   with rights to the `novaos-agent-sdk` name).
2. On the package's npm page → Settings → Trusted Publisher, add:
   - Provider: GitHub Actions
   - Repository: `OrbitronAI-Repo/novaos-agent-sdk-ts-public`
   - Workflow: `release.yml`
   (Same "pending publisher" pattern as PyPI — this reserves nothing until the
   first publish succeeds.)

## Release Checklist

1. Bump `version` in `package.json` (and `src/index.ts`'s `VERSION` if kept in sync).
2. Commit, PR, merge to `main`.
3. Tag the merge commit: `git tag -a vX.Y.Z -m "Release vX.Y.Z" && git push origin vX.Y.Z`.
4. Create a GitHub Release from that tag — `.github/workflows/release.yml` builds and
   publishes to npm automatically.
