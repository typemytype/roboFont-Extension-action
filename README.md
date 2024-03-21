# RoboFont Extension Action

RoboFont Extension builder for GitHub Actions

## Usage

```yaml
name: Validate and Build the Extension
on:
  push

jobs:
  validate_and_build:
    runs-on: ubuntu-latest
    steps:
      - name: Validate and Build
        uses: typemytype/roboFont-Extension-action@v0.1.0
        with:
          autotagging: true  # set to false by default

```

## Autotagging

When `autotagging` is set to `true`, the action will automatically generate a release named with the version number set in the `info.yaml` file (if not existing yet). In other words, when you'll edit the extension version number and push to the remote, the action will automatically take care of making a new release. Anytime a letter `b` is contained in the version number (as for `4.0b` or `3.4-beta1`), the action will consider the version as beta and generate a release marked as "pre-release". In this way [Mechanic 2](https://github.com/robofont-mechanic/mechanic-2) will not distribute it as a stable release.

## Naming

GitHub does not allow assets attached to release to contain word spaces. If your extension name is made of multiple words, like `Glyph Nanny`, we suggest to set a `path` in the `build.yaml` with a name not containing any space (`Glyph_Nanny.roboFontExt`).

## Permissions

Besides allowing actions in your repository, you'll also need to provide read and write permissions. Check Settings > Actions > General before setting the workflow.