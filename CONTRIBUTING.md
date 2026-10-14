# Contributing to StellarAid

Thanks for helping build StellarAid, a decentralized mutual-aid social network on Stellar.
This guide applies to every repository in the organization. Each repo's own `README.md`
adds specifics on top of it.

## The README is the spec

Each repository's `README.md` is the **source of truth**. If code and README disagree,
either fix the code or open a PR that updates the README with justification. Never let
them drift silently.

## Workflow: issue -> branch -> PR

1. **Find or open an issue.** Search existing issues first; if you are starting work,
   comment so others know. Labels such as `good first issue` and `help wanted` mark good
   starting points.
2. **Branch from `main`.** Use a short, descriptive branch name, e.g.
   `feat/giveaway-claim-batching` or `fix/refund-double-spend`.
3. **Make small, focused commits.** See Conventional Commits below.
4. **Open a pull request** using the repository's PR template. Link the issue. At least
   one maintainer review is required; changes that move funds need two.
5. **Keep it green.** CI must pass (fmt, lint, typecheck, tests) before merge.

## Conventional Commits

Use the [Conventional Commits](https://www.conventionalcommits.org/) format:
`type(scope): summary`, for example `feat(sdk): add claim batching`, `fix(api): reject
expired challenge`, `docs(contracts): clarify refund rules`. Common types: `feat`, `fix`,
`docs`, `test`, `refactor`, `chore`, `ci`.

## Cross-repo change order

Dependency direction is `contracts -> sdk -> web / api`. Do not hand-write what the
bindings will generate, and `web` and `api` never import from each other:

1. Merge `contracts` first (ABI, events, errors, storage).
2. Then `sdk` (regenerate bindings, update wrappers, release).
3. Then `web` and `api` (consume the new SDK version).

A contract ABI change is **breaking**: it needs an RFC and a matching major release of
`sdk`.

## RFC process

Cross-repo and breaking changes start as an RFC. Copy `rfcs/0000-template.md` to
`rfcs/0000-my-proposal.md`, fill it in, and open a PR (or a discussion) in this
repository. Contract and API changes that alter public interfaces, event shapes, or
storage layouts require an accepted RFC before implementation.

## Ground rules

- **No secrets in code, ever.** Use `.env.example` with placeholders.
- **Money on-chain, social off-chain.** The API never custodies funds; the chain wins any
  disagreement about money.
- **Tests ship with the feature**, not after it.
- **Never edit auto-generated code** (for example `sdk/src/generated`,
  `web/lib/api-client`).
- Unplanned ideas go to `docs/backlog.md` or an issue labeled `post-85`.

## Reporting security issues

Do **not** open a public issue for a vulnerability. See [SECURITY.md](./SECURITY.md).
