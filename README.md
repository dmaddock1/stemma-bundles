# stemma-bundles

Per-language data bundles for the [Stemma](https://github.com/dmaddock1/stemma)
language-learning app. The app downloads these at runtime; you don't
need to do anything with this repo unless you're working on Stemma
itself.

## What's here

Each release tag (`bundles-YYYY.MM.DD`) ships every active bundle as
a release asset, plus a `manifest.json` that the app reads to discover
download URLs + checksums.

The `manifest.json` on `main` mirrors the latest non-preview release —
that's the stable URL the app polls:
`https://raw.githubusercontent.com/dmaddock1/stemma-bundles/main/manifest.json`.

Two bundle kinds:

- **morphology-`<code>`-v`<N>`.db** — per-language: inflected-form →
  lemma index, lemma frequency ranks, paradigm cell catalogue. One
  per language Stemma supports (Romance, Germanic, Latin so far). Size
  range: ~3 MB (Norwegian) to ~53 MB (German).
- **linguistics-v`<N>`.db** — shared cognate-graph database that
  drives Stemma's "you might recognise this word from English /
  Spanish / …" hints. Single file, all languages combined. ~140 MB.

## How releases are produced

Built by [`publish_bundles.py`](https://github.com/dmaddock1/stemma/blob/main/linguistics/tools/bundle-publish/publish_bundles.py)
in the main Stemma repo. The script bumps `manifest.json` on `main`
as the last step of each release, so users always land on a
consistent view.

Bundles whose content hasn't changed since the previous release are
re-linked rather than re-uploaded, so older release tags continue to
serve as the canonical URL for unchanged bundles. Don't delete old
releases without checking what the current `manifest.json` points at.

## Licensing & attribution

The bundle contents are derived works under
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) —
see [`NOTICES`](NOTICES) for source acknowledgement.
