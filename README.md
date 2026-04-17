# RevitCortex – Release Metadata

This repository serves `latest.json` over `raw.githubusercontent.com` so the
RevitCortex plugin can check for a newer version at startup.

**Source code** lives in a **private** repository. This repo only contains
metadata (version number, download URL, changelog) — nothing sensitive.

## Manifest URL

```
https://raw.githubusercontent.com/LuDattilo/revitcortex-releases/main/latest.json
```

## Release workflow

When a new RevitCortex release ships:

1. Build + upload the release ZIP to the distribution location (e.g. OneDrive).
2. Generate (or reuse) a shareable link for that ZIP.
3. Update `latest.json` in this repo:
   - `version`: new semver string (`1.0.3`, etc.)
   - `downloadUrl`: the shareable link from step 2
   - `changelog`: concise release notes
4. Commit and push. The plugin picks up the change at the next Revit start.

The plugin compares `version` against its own `AssemblyVersion` using
`System.Version`, so there are no string-match gotchas.
