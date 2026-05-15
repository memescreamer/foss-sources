# memescreamer/foss-sources

Source archive mirror for FOSS components redistributed by memescreamer
products (rAIdio.bot, vAIdeo.bot, and future siblings on the
[doomscroll.fm](https://doomscroll.fm) family).

## Why this repo exists

Several FOSS licenses we redistribute under impose source-availability
obligations on the distributor:

- **GPL-2.0 / GPL-3.0 §3 (or-later equivalents)** — when distributing
  binaries, you must accompany them with corresponding source OR a
  written offer to provide source for at least 3 years.
- **LGPL-2.1 / LGPL-3.0 §6** — same source-availability requirement plus
  the additional obligation to enable relinking of the application
  against a different build of the LGPL library.
- **MPL-2.0 §3.1** — source for any covered files must be available to
  recipients of the binary.
- **Apache-2.0 §4(a)** — copies of the License must be retained;
  attribution requirements per §4(d).

When the canonical upstream of these components is hosted by a third
party (e.g., `ffmpeg.org`, `pypi.org`, project-specific git forges), our
compliance posture depends on that third party staying online for the
distribution lifetime of our binaries. That's a fragility we can fix by
mirroring the exact source artefact we built from into a location we
control.

This repo is that location. It pairs with the per-component git-fork
mirrors at `memescreamer/<component-name>` for projects whose canonical
form is a git repo; this repo holds the artefacts that aren't naturally
git-shaped (release tarballs, sdists, vendor drops).

## How it's organized

Each release (Git release, GitHub-Releases UI) corresponds to a
mirroring event — typically anchored to a memescreamer-family product
release. Release assets are the upstream source archives, named exactly
as upstream named them, with their canonical SHA-256 hash recorded in
the release notes.

Releases:

| Release tag | Anchor | Components mirrored |
|---|---|---|
| `RC-1-Gold-0.30` | rAIdio.bot 2026-05-15 | ffmpeg-7.1, CPython-3.12.10, libsndfile-1.2.2 |

## SHA-256 verification

Every release asset's SHA-256 is recorded in the corresponding release
notes alongside its filename. To verify an artefact matches upstream:

```bash
sha256sum ffmpeg-7.1.tar.gz
# Compare against the release notes value AND against upstream
# (e.g., ffmpeg.org's published checksum if upstream publishes one).
```

If you find a hash discrepancy, please open an issue immediately —
the canonical source on this repo MUST byte-match upstream.

## Coverage scope

This repo holds source archives for components used in production by
memescreamer-family products. Coverage criteria:

- Components with a copyleft license (GPL/LGPL/MPL/EPL/CDDL/AGPL family) —
  mandatory mirror, regardless of upstream stability.
- Components with permissive licenses (MIT/BSD/Apache/ISC) whose
  canonical home is a fragile third-party URL (project-specific webserver
  rather than crates.io / npmjs / PyPI / GitHub) — mirrored as a
  defensive measure.
- Components hosted on permanent package archives (crates.io, npmjs.org,
  PyPI, GitHub forks at `memescreamer/<name>`) — NOT mirrored here; the
  package archive is itself the durable mirror.

If a component you depend on is missing from this repo and you believe
it should be here, open an issue.

## Cross-references

- [rAIdio.bot](https://store.steampowered.com/app/4600000) (memescreamer
  product) — AI-assisted music production. Per-release SBOM at
  [rAIdio-bot/sbom](https://github.com/rAIdio-bot/sbom).
- [vAIdeo.bot] (memescreamer product, sibling) — AI-assisted video
  production. Shares the audio compliance posture with rAIdio.bot.

## License

This repo's organization and documentation: CC0-1.0 (no rights
reserved on the mirror infrastructure itself).

The source archives stored as release assets retain their original
upstream licenses (GPL-3.0-or-later for ffmpeg, PSF-2.0 for CPython,
LGPL-2.1-or-later for libsndfile, etc.). Mirroring does not grant any
license to redistribute beyond what upstream's license already
permits.
