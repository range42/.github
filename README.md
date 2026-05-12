# range42 Community Health Defaults

This repository contains the default community health files for the `range42` organization. GitHub automatically applies these to any public repo under `range42` that does not provide its own version.

---

## Why this exists

- **Uniform standards** — consistent contribution, conduct, and security guidelines across all repositories.
- **Single source of updates** — modify once here; GitHub applies changes everywhere automatically.
- **Clean repo history** — defaults are not included in individual repo clones or Git history.

---

## Included files

| File | Purpose |
|------|---------|
| `CODE_OF_CONDUCT.md` | Community standards and enforcement |
| `CONTRIBUTING.md` | How to contribute — bugs, features, pull requests |
| `GITWORKFLOW.md` | How we use Git and GitHub at range42 |
| `SECURITY.md` | Vulnerability reporting procedures |
| `SUPPORT.md` | Support and communication channels |
| `ROADMAP.md` | Project direction and priorities |
| `CODINGSTYLE.md` | Coding style guidelines |
| `profile/README.md` | Org homepage shown on github.com/range42 |

> **Note:** A `LICENSE` file must be added to each repository individually — it cannot be inherited.

---

## How it works

When someone opens an issue or pull request in any public `range42/*` repo:

1. GitHub checks that repository for community health files.
2. If a file is missing, it falls back to this `.github` repo (searches `.github/`, root, then `docs/`).
3. Local overrides take full precedence; defaults remain hidden from repo history.

---

## Updating defaults

1. Edit or add files in this repository.
2. Commit and push to the default branch.
3. Changes take effect automatically across all public `range42/*` repositories that lack local overrides.

---

## Contributing

1. Fork this repository.
2. Make changes or add files (e.g., new issue templates).
3. Submit a pull request with context for your changes.
4. At least one review is required before merging.

---

## License

Licensed under the GNU General Public License v3.0.
