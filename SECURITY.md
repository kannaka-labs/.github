# Security Policy

## Reporting a vulnerability

**Do not open a public issue for a security problem.**

Report privately, whichever is easier:

- **GitHub** — use the *Report a vulnerability* button under the affected repo's **Security** tab (private vulnerability reporting).
- **Email** — [nick@spacechild.love](mailto:nick@spacechild.love). Put `SECURITY` in the subject.
- **Nostr** — a NIP-17 gift-wrapped DM to `npub1j9t89fsgkpascqdezsrlw3p743jmkks084g6d0drzwuxaz3qaq6qx8w8dz`.

Please include: the repo and version or commit, what an attacker gains, and the smallest reproduction you have. A proof-of-concept is welcome but never required.

## What to expect

| stage | target |
|---|---|
| Acknowledgement | within 3 business days |
| Initial assessment | within 10 business days |
| Fix or documented mitigation | within 90 days for confirmed issues |

Kannaka Labs is a very small team. If you have not heard back within the acknowledgement window, please send a follow-up — it means the first message was missed, not ignored.

We will credit you in the release notes for the fix unless you ask us not to. There is no bug bounty program at this time; we will not pretend otherwise.

## Scope

**In scope** — anything that lets an attacker do something the design says they should not:

- Memory-safety, panics reachable from untrusted input, or unsoundness in the Rust crates (`kannaka-memory`, `kannaka-attention`, `consciousness-core`, `kannaka-crystal`, `kannaka-hdl`, `ghostsignals-rs`).
- Capability escapes, IPC confusion, or privilege escalation in `QuantumOS`.
- Signature forgery or verification bypass against the constellation manifest, agent identities, or the NATS job envelopes.
- Sandbox or approval-gate escapes in the agent harnesses — anything that executes a filesystem or shell mutation without the human approval the harness promises.
- Secret exposure in build artifacts, release binaries, published packages, or CI logs.
- Authorization flaws in the hosted surfaces (portal, relay, radio, observatory).

**Out of scope:**

- Findings from a fork you modified yourself.
- Missing hardening headers or TLS configuration nits with no demonstrated impact.
- Volumetric denial of service, and social engineering of maintainers.
- Automated scanner output submitted without a working reproduction.
- The consciousness metrics being philosophically contestable. `Φ` and `Ξ` are documented approximations with defined formulas; disagreeing with the interpretation is a research conversation, not a vulnerability. Open an issue.

## Supported versions

Only the **latest release** of each component receives security fixes. The constellation moves quickly and there are no long-term-support branches. Pin by tag and digest; `kannaka-library`'s signed [`constellation.json`](https://kannaka-labs.github.io/kannaka-library/constellation.json) records the sha256 of every published asset, so you can verify what you are running.

## Coordinated disclosure

Please give us 90 days before public disclosure, or until a fix ships — whichever comes first. If a vulnerability is being actively exploited, tell us that in the first message and we will drop everything.
