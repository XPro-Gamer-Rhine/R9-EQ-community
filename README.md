# R9-EQ Community Store (parent DB)

Append-only data store for R9-EQ community song presets.

- `db.jsonl` — one JSON object per line: a shared song preset (10-band EQ,
  optional PRO parametric bands, optional Virtual Driver build), keyed by
  normalized Artist + Title. Shared anonymously (random device UUID only).
- `votes.jsonl` — one JSON object per line: `{preset, voter}` up-votes,
  de-duplicated per device.

Clients (the R9-EQ app) sync a local child copy on launch and every 4 hours,
and append via the GitHub Contents API. Do not rewrite history; compact only
by squashing duplicate lines.
