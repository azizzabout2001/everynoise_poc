# everynoise_poc

Proof-of-concept: Last.fm tag clustering → 2D artist placement.

**Status: scaffold only — no code yet.**

## Layout (planned)

```
everynoise_poc/
├── ingest.py          # Last.fm API → data/cache/
├── cooccurrence.py    # tag co-occurrence from raw tags
├── anchors.py         # hand-picked reference artists
├── cluster.py         # shared geometric primitive (used by infer + placement)
├── infer.py           # tag inference via cluster primitive
├── placement.py       # 2D artist projection via same primitive
└── report.py          # output
run_poc.py             # CLI entry, --offline flag
data/cache/            # raw Last.fm responses (gitignored)
data/derived/v1/       # processed outputs (gitignored)
```

## Pipeline

`ingest → cooccurrence → anchors → infer → placement → report`

## Notes

- Errors surface real status codes (invalid-key 403, unresolvable artist) — verified by hand, not assumed.
- Rerunnable offline via `--offline` (uses cache only).
- Spec source: claude.ai/code session (now lost); this repo is rebuilt from a brief.
