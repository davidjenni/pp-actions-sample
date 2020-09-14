# Power Platform GitHub Actions Sample

[GitHub Action](https://help.github.com/en/actions) for Power Platform

## Secrets

The workflow in .github/workflows/CI.yml references a PowerPlatform password, matching to the username in the .yml file

Create a secret named 'PASSWORD' in your repo, under 'Settings' | 'Secrets' | 'New secret'

## Referencing microsoft/powerplatform/* actions

Currently, the PowerPlatform GH actions are not yet publicly visible; hence they cannot be referenced via their global
repo name; instead this repo keeps a local cache and references those using the [local action reference syntax](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions#example-using-action-in-the-same-repository-as-the-workflow)

### Populating local cache of actions

Approach is to directly commit the actions repo, but deleting its .git repo folder so that the repo src artifacts can be commited into this repo
(without deleting the .git folder, git will insist on that folder to become a git submodule; to checkout a submodule, the actions repo would again need to be public...)

```bash
git clone https://github.com/microsoft/powerplatform-actions.git ./microsoft/powerplatform/actions
rm -Recurse -Force ./microsoft/powerplatform/actions/.git
rm .\microsoft\powerplatform\actions\.gitignore
git add ./microsoft/powerplatform/actions
```

## Change action names

Instead of using the actions' repo path, convert it to point to the actions in the local repo:

```bash
    - name: Test who-am-i action
      # uses: microsoft/powerplatform/actions/who-am-i
      uses: ./microsoft/powerplatform/actions/who-am-i
```

Once the powerplatform/actions repo becomes publicly visible, the local cached copy is obsolete and can be deleted.
Change the ```uses:``` lines to just the public repo naming scheme (drop the ```./``` prefix)
