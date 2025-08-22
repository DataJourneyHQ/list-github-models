## List GitHub AI Models

[![GitHub release](https://img.shields.io/github/release/datajourneyhq/list-github-models.svg)](https://github.com/datajourneyhq/list-github-models/releases)
[![GitHub marketplace](https://img.shields.io/badge/marketplace-list--github--models-blue?logo=github)](https://github.com/marketplace/actions/list-github-models)

Fetch GitHub AI models catalog and uploads it as an artifact for daily tracking and analysis.

## Inspiration  

At DJHQ, we rely heavily on GitHub’s AI models.  
One fine day, without warning, a few of our trusted models vanished from the listings.  

👉 [DataJourney’s workflow](https://github.com/DataJourneyHQ/DataJourney/blob/main/.github/workflows/list-github-models.yml)

## Features

- 📊 Fetches complete GitHub AI models catalog
- 📝 Creates simplified summary with key model information
- 📋 Generates markdown report for easy viewing
- 💾 Uploads all data as downloadable artifacts
- ⏰ Perfect for scheduled workflows to track model changes

## Usage

### Basic Usage

```yaml
name: Track GitHub Models
on:
  schedule:
    - cron: '0 3 * * *'  # Daily at 3 AM UTC

jobs:
  track-models:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: datajourneyhq/list-github-models@v1.0.0
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

### Advanced Usage

```yaml
- uses: datajourneyhq/list-github-models@v1.0.0
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    artifact-name: 'my-custom-models-catalog'
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `github-token` | GitHub token for API access | No | `${{ github.token }}` |
| `artifact-name` | Name for the uploaded artifact | No | `github-models-catalog` |

## Outputs

| Output | Description |
|--------|-------------|
| `artifact-name` | Name of the uploaded artifact |

## Artifacts

The action creates an artifact containing:

- **`github-models.json`** - Complete models catalog from GitHub API
- **`github-models-mini.json`** - Simplified version with id, name, and summary
- **`models-report.md`** - Human-readable markdown report

## Example Workflow

```yaml
name: Daily GitHub Models Tracking

on:
  workflow_dispatch:
  schedule:
    - cron: '0 3 * * *'

permissions:
  contents: read

jobs:
  track-models:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        
      - name: Set date
        run: echo "DATE=$(date +'%Y-%m-%d')" >> $GITHUB_ENV
    
      - name: Fetch GitHub Models
        uses: datajourneyhq/list-github-models@v1.0.0
        with:
          artifact-name: 'models-${{ env.DATE }}'
```

## Author

**DataJourney HQ**
- GitHub: [@datajourneyhq](https://github.com/datajourneyhq)
