# .github

Organization-level defaults for [Kannaka Labs](https://github.com/kannaka-labs).

| path | what it does |
|---|---|
| `profile/README.md` | The org profile page rendered at [github.com/kannaka-labs](https://github.com/kannaka-labs) |
| `SECURITY.md` | Default security policy for every repo without its own |
| `CONTRIBUTING.md` | Default contribution guide, including the DCO sign-off requirement |
| `CODE_OF_CONDUCT.md` | Default code of conduct |
| `.github/ISSUE_TEMPLATE/` | Default issue forms inherited org-wide |

Files here are inherited by any repo in the org that does not define its own copy.
A repo-local file always wins.

## Editing the profile

`profile/README.md` is the constellation's front door. When a component is added,
renamed, moved, or retired, update the layer tables here in the same change —
the profile and [`kannaka-library`](https://github.com/kannaka-labs/kannaka-library)'s
`sources.json` should never disagree about what the constellation is.

Every URL in the profile is expected to resolve. Check before merging:

```sh
grep -oE 'https://[^)"< ]+' profile/README.md | sort -u | \
  xargs -I{} sh -c 'printf "%-70s %s\n" "{}" "$(curl -s -o /dev/null -w "%{http_code}" -L --max-time 15 "{}")"'
```
