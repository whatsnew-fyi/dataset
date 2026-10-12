# What's New release facts

Release facts for the software, games and operating systems [What's New](https://whatsnew.fyi/) tracks: each product, and each release's version, date, the vendor's own release-notes URL, prerelease flag and channel, the CVE ids it mentions, and breaking-change signals. Rebuilt nightly from the same database the site and its API serve.

This branch holds no data. Every night's dataset is published as a release of this repository.

## Files

- `products.jsonl.gz`: one product per line, validated by `product.schema.json`.
- `releases.jsonl.gz`: one release per line, validated by `release.schema.json`. A release's `product` is a product's `slug`.
- `product.schema.json` and `release.schema.json`: the JSON Schemas for each row.
- `manifest.json`: row counts, sizes and sha256 for every file.
- `README.md`: a dataset card for that night's release.

## Download

Every night is a release tagged `data-YYYY-MM-DD`, marked latest when it is published. Releases and tags older than 30 days are removed. The newest files are always at stable URLs:

- https://github.com/whatsnew-fyi/dataset/releases/latest/download/products.jsonl.gz
- https://github.com/whatsnew-fyi/dataset/releases/latest/download/releases.jsonl.gz
- https://github.com/whatsnew-fyi/dataset/releases/latest/download/product.schema.json
- https://github.com/whatsnew-fyi/dataset/releases/latest/download/release.schema.json
- https://github.com/whatsnew-fyi/dataset/releases/latest/download/manifest.json
- https://github.com/whatsnew-fyi/dataset/releases/latest/download/README.md

For a fixed snapshot, download from a dated tag instead of `latest`, and keep your own copy: a tag lasts 30 days.

## Fields worth knowing

- `signals.breakingMention` is a literal reading of the vendor's text: it says "breaking" and does not say "no breaking change".
- `signals.classified` comes from the release's change categories, which a model assigns (or a Declarative Changelog's publisher declares). It is `null` for a release that has not been categorized yet.
- `provenance: "seed"` marks hand-curated sample data, not a vendor's own entry.
- `packages` holds purls and namespace claims (`pkg:maven/org.example/*`); a namespace claim is not itself a purl.

## What is not included

The dataset holds no release-note text. Each release links to the vendor's own notes (`url`), which remain their publisher's, and to its page on What's New (`permalink`). What's New's summaries and categorized change lists are not part of the dataset.

## Live API

The same facts, per product or per package URL: https://whatsnew.fyi/api/v1/openapi.json

## Licence

The facts are licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The full legal code is in [LICENSE](LICENSE).

When you reuse them, include this attribution:

> Release facts from What's New (whatsnew.fyi), licensed CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/). Attribute "What's New (whatsnew.fyi)" with a link to https://whatsnew.fyi/. Summaries and other prose are not covered: https://whatsnew.fyi/terms#reuse.
