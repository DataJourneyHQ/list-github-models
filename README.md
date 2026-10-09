# List GitHub AI Models (retired)

> **This action is retired and is no longer maintained.** GitHub retired the GitHub Models service on **July 30, 2026**, including its model catalog and REST API.

The source and existing releases remain available for historical reference.

## Why the action stopped working

GitHub Models is no longer available to any customer. Its playground, model catalog, inference API, and bring your own key (BYOK) features have all been retired. See [GitHub's retirement announcement](https://github.blog/changelog/2026-07-30-github-models-is-now-retired/) and the [current GitHub Models documentation](https://docs.github.com/en/github-models).

The action fetched its catalog from `https://models.github.ai/catalog/models`. That endpoint now returns **HTTP 200** with a plain-text `OK` response instead of a JSON catalog, causing the reported JSON validation failure. A successful HTTP status alone does not mean the catalog is available.

There is no supported replacement endpoint for the retired GitHub Models catalog.

## If you use this action

- Remove `datajourneyhq/list-github-models` from your workflows.
- Disable scheduled workflows dedicated to fetching this catalog.
- Download any historical artifacts you want to keep before their retention period expires.

For projects that need AI model access, GitHub points to [Microsoft Foundry](https://ai.azure.com/). For AI-powered workflows on GitHub, see [GitHub Copilot](https://docs.github.com/en/copilot). Neither restores this action's retired catalog API.

## About the project

We built this action at DataJourney HQ after models we relied on disappeared from GitHub's listings. It captured daily catalog snapshots to help track changes and produced three artifact files:

| File | Contents |
|------|----------|
| `github-models.json` | Full model catalog returned by the API |
| `github-models-mini.json` | Model IDs, names, and summaries |
| `models-report.md` | Human-readable catalog report |

Historical snapshots describe what was available when they were captured; they do not represent current model availability.

## Author

[DataJourney HQ](https://github.com/DataJourneyHQ)
