# Feather Github Workflows
This repository contains a collection of [GitHub Workflows](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions) that can be reused across repos.

## Usage

To use a workflow in your project, simply create an new job and add the full path of the workflow you want to use with the `uses` keyword:

```yaml
jobs:
  update_release_draft:
    uses: getPopsure/github-workflows/.github/workflows/generate-release-draft.yml@v0.1.0
```

Make sure to use the latest version of the `github-workflows` repo adding the `@v` suffix.

⚠️ Avoid using the `@main` branch of the `github-workflows` repo, as this branch can potentially be unstable. 

### Example usage

The following configuration will trigger the `generate-release-draft` worfklow everytime a pull request is open.

```yaml
name: Generate release draft

on:
  pull_request:
    branches:
      - main

jobs:
  update_release_draft:
    uses: getPopsure/github-workflows/.github/workflows/generate-release-draft.yml@v0.1.0
```

### Using inputs and secrets

Some workflows require additional information or secrets to run. You can use the `with` or `secrets` keywords inside a job to pass the required information.

```yaml
jobs:
  lint:
    uses: getPopsure/github-workflows/.github/workflows/lint.yml@v0.1.0
    secrets:
      NPM_TOKEN: ${{ secrets.NPM_PKG_GITHUB_TOKEN }}
```

You can learn more on the [GitHub website.](https://docs.github.com/en/actions/using-workflows/reusing-workflows#using-inputs-and-secrets-in-a-reusable-workflow)

### Contributing

If you have duplicated workflows across different projects, feel free to open a PR to include them here. This project uses [SemVer](https://semver.org/) for versioning. 

### Next steps

- Add a visual regression workflow  
- [Cache dependencies to speed up workflows](https://docs.github.com/en/actions/using-workflows/caching-dependencies-to-speed-up-workflows)
