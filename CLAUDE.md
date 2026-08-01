# CLAUDE.md

## Bumping Node

The Node runtime version lives in `.nvmrc` at the repo root. To bump:

1. Update `.nvmrc` to the new major.
2. Update `engines.node` in package.json to match (e.g. `^<next>.0.0`).
3. Update any `FROM node:<version>` lines in Dockerfile(s) / the serverless `runtime:` if you are also moving the deployed runtime.
4. This repo has no GitHub Actions CI — there is no `.github/` directory at any ref, so there is no `actions/setup-node` step reading `node-version-file` and no workflow to edit. The only CI configuration is `.travis.yml`, which hardcodes `node_js: - "8"` and is not driven by `.nvmrc`; if the Travis config is ever revived or replaced, that Node version has to be moved by hand.
5. Reinstall locally on the new version to refresh the lockfile if needed.
