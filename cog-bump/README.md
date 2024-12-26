# cog-bump

This Github Action bumps tags your repository with the next [Semantic Version](https://semver.org/) for you repository by using [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

This action uses [Cogogitto](https://github.com/cocogitto/cocogitto). Once a new version has been tagged you will need to push it to Github. Alternatively, you can configure Cocogitto to perform the push in a [`cog.toml`](https://docs.cocogitto.io/config/#general) file in your repository.

## Usage

### Prerequisites

You need to have your repository checked out with the full commit history and all tags. You you can do this with the following steps:

```yaml
- uses: actions/checkout@v4
  with:
    fetch-depth: 0
    # token is needed when branch protections are enabled on the target branch
    token: ${{ secrets.PAT_TOKEN }}
```

### Bumping the version

```yaml
- id: cog-bump
  uses: abhisheksr01/github-actions/cog-bump@v0.1.0 # Check the GitHub Repo Releases for latest version
```

## Inputs

| Name              | Description                                                                                                                  | Required | Default                    |
|-------------------|------------------------------------------------------------------------------------------------------------------------------|----------|----------------------------|
| working-directory | The directory to run the action in. Default is the root of the repository.                                                   | false    | null                       |
| git-user          | The name of the user to use when tagging the repository.                                                                     | false    | cog-automation-bot         |
| git-user-email    | The email of the user to use when tagging the repository.                                                                    | false    | cog.automation-gh@mail.com |
| skip-ci           | Appends `[skip ci]` to the commit message.                                                                                   | false    | true                       |
| package           | Specify which package to bump for monorepo                                                                                   | false    | null                       |
| dry-run           | Print the target version without bumping the version                                                                         | false    | false                      |
| version           | Manual version. Version regex matched against semver spec. Failure on regex match, action will default to auto version bump. | false    | null                       |

## Outputs

| Name              | Value                                                                                                |
|-------------------|------------------------------------------------------------------------------------------------------|
| previous-version  | The version before the bump occurred.                                                                |
| bump-version      | The version output of `cog bump` command either during tag creation or with `--dry-run`.             |
| current-version   | The version after the bump. This will be the same as previous-version when no new version is tagged. |
| is-version-bumped | Boolean value set to `true` if a new version was tagged.                                             |
