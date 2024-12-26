# setup-cocogitto

This action installs the specified version of [cocogitto](https://github.com/cocogitto/cocogitto) to use in your GitHub Actions workflow.

## Inputs

| Name         | Description                                             | Required | Default                   |
|--------------|---------------------------------------------------------|----------|---------------------------|
| version      | The version of cocogitto to install                     | false    | 6.2.0                     |
| architecture | The architecture of the machine to install cocogitto on | false    | x86_64-unknown-linux-musl |

## Usage

```yaml
# Uses the default version of cocogitto (currently 6.2.0)
- uses: abhisheksr01/github-actions/setup-cocogitto@v0.2.0 # Check the GitHub Repo Releases for latest version

# Uses a specific version of cocogitto
- uses: abhisheksr01/github-actions/setup-cocogitto@v0.2.0 # Check the GitHub Repo Releases for latest version
  with:
    version: "6.1.0"

# Verify the version of cocogitto
- run: cog --version
```
