# Laravel Deployment Workflow

This repository contains a reusable GitHub Actions workflow for deploying Laravel applications.

## Usage

To use this workflow in your Laravel repository:

```yaml
jobs:
  deploy:
    uses: TheYGSGroup/workflows/.github/workflows/deploy.yml@v0.0.1
    secrets: inherit
```

@TODO JAKE FINISH DOCUMENTING