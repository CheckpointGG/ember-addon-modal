# CLAUDE.md

## Bumping Node

The Node runtime version lives in `.nvmrc` at the repo root. To bump:

1. Update `.nvmrc` to the new major.
2. Update `engines.node` in package.json to match (e.g. `^<next>.0.0`).
3. Update any `FROM node:<version>` lines in Dockerfile(s) / the serverless `runtime:` if you are also moving the deployed runtime.
4. CI reads `.nvmrc` via `actions/setup-node`'s `node-version-file`, so no workflow edits are needed. (If CI has no setup-node step, add one pointing at `node-version-file: '.nvmrc'`.)
5. Reinstall locally on the new version to refresh the lockfile if needed.
