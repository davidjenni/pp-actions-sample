# Power Platform GitHub Actions Sample

[GitHub Action](https://help.github.com/en/actions) for Power Platform

## Referencing microsoft/powerplatform/* actions

Currently, the PowerPlatform GH actions are not yet publicly visible; hence they cannot be referenced via their global
repo name; instead this repo keeps a local cache and references those using the [local action reference syntax](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions#example-using-action-in-the-same-repository-as-the-workflow)

### Populating local cache of actions

```bash
git submodule add https://github.com/microsoft/powerplatform-actions.git .github/pp-actions
```
