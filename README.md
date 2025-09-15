# Laravel Deployment Workflow

This repository contains a reusable GitHub Actions workflow for deploying Laravel applications.

## Usage

To use this workflow in your Laravel repository:

```yaml
name: Deploy

on:
  push:
  workflow_dispatch:
    inputs:
      environment:
        description: 'Environment to deploy to'
        required: true
        default: 'staging'
        type: choice
        options:
          - production
          - staging
          - development

jobs:
  deploy:
    uses: TheYGSGroup/workflows/.github/workflows/deploy.yml@v0.0.1
    secrets: inherit
```

The workflow will automatically determine whether to deploy based on the branch configuration in your `gs_develop/config/deploy.yml` file. The environment options in the workflow_dispatch should match those defined in your config file.

@TODO JAKE FINISH DOCUMENTING

## Development Guidelines

### Creating a New Release

When making changes to the workflow, follow these steps to create a new release:

1. Make your changes to the workflow files
2. Commit your changes
   ```bash
   git add .
   git commit -m "Description of changes"
   ```
3. Tag the new version following semantic versioning
   ```bash
   git tag -a v0.1.0 -m "Description of the release"
   ```
4. Push the changes and the tag
   ```bash
   git push origin main
   git push origin v0.1.0
   ```

### Updating Projects to Use a New Version

To update a project to use a new version of the workflow:

```yaml
jobs:
  deploy:
    uses: TheYGSGroup/workflows/.github/workflows/deploy.yml@v0.1.0
    secrets: inherit
```

### Using the Latest Version (Not Recommended for Production)

For development purposes, you can reference the main branch directly:

```yaml
jobs:
  deploy:
    uses: TheYGSGroup/workflows/.github/workflows/deploy.yml@main
    secrets: inherit
```

**Note:** Using the main branch is not recommended for production environments as it may contain breaking changes.