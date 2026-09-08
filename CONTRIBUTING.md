# Contributing to Kannaka Labs

Thanks for being here. This is the org-wide default — a repo with its own `CONTRIBUTING.md` overrides it.

## Before you write code

**Open an issue first for anything non-trivial.** The constellation is one system with load-bearing invariants across repo boundaries; a clean patch that breaks a documented contract still gets rejected, and neither of us enjoys that.

**Read the ADRs.** Most repos keep numbered Architecture Decision Records under `docs/adr/`. If a design looks wrong, there is often a record explaining the trade-off. Disagreeing with an ADR is fine and welcome — say so in an issue that references it by number, and if we agree, the change lands as a new ADR that supersedes the old one. ADRs are never edited to rewrite history.

## The rules that are not negotiable

- **Claims are gated by CI.** If you add a capability to a README, add the test or smoke gate that proves it in the same PR. "What runs today" sections describe what actually runs today.
- **Metrics say what they measure.** Do not describe an approximation as an exact computation. `compute_phi` is a connectivity approximation, not a bipartition search, and its docs say so. Hold new metrics to the same standard.
- **Frontends do not link backends.** `kannaka-tui` shells out to the `kannaka` binary; the Claude Code plugin ships zero dependencies. If your patch adds a dependency edge between layers, expect to justify it.
- **Approval gates stay closed.** Any code path that mutates a filesystem or runs a shell command on a user's behalf goes through the harness's human approval dialog. No exceptions, no convenience bypass flags.
- **Third-party code keeps its notice.** If you vendor, port, or adapt someone else's work, preserve their copyright and license text and record it in the repo's attribution section. This applies to snippets, not just whole files.

## Developer Certificate of Origin

All commits must be signed off. This certifies you wrote the patch or otherwise have the right to submit it under the repo's license — see [developercertificate.org](https://developercertificate.org/).

```sh
git commit -s -m "your message"
```

Some repos enforce this with a DCO check; assume it applies everywhere.

## Pull requests

- **Branch from `main`**, keep the PR focused on one thing.
- **Explain the why**, not the what — the diff already says what changed.
- **Tests pass locally before you push.** `cargo test` / `node --test test/` / `pytest`, depending on the repo.
- **Rust:** `cargo fmt` and `cargo clippy -- -D warnings` must be clean. No panics in library code — return a typed error.
- **Link the issue** the PR closes.

Small fixes — a broken link, a typo, a wrong path in a doc — do not need an issue. Just send them.

## What is unlikely to be merged

- Renaming things to be more conventional. The vocabulary is deliberate.
- Adding a dependency to a crate that advertises having none.
- Broad reformatting mixed into a functional change.
- Removing an approval gate, a spend guard, or a budget cap because it was inconvenient during development.

## Licensing

Contributions are accepted under the license of the repo you are contributing to — check its `LICENSE` file, since the constellation is not uniformly licensed. Most repos use the [Space Child License v1.0](https://legal.spacechild.love); some are MIT, one is BUSL-1.1, one is GPL-2.0.

## Security

Do not report vulnerabilities through issues or pull requests. See [SECURITY.md](SECURITY.md).
