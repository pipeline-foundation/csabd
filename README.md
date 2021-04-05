# Code scanning alerts bulk dismissal

This action lets you automatically dismiss a large amount of code scanning alerts, based on one or more source files/folders

**Table of Contents**

- [Platforms](#platforms)
- [Usage](#usage)

## Platforms

The action is written in PowerShell and is executed inside a PowerShell Core shell, therefore the action is cross-platform and works on all latest available GitHub Actions operation systems:

- **windows-latest**
- **ubuntu-latest**
- **macos-latest**

## Usage

```

name: CSABD

on: [workflow_dispatch]

jobs:
  test:
    runs-on: windows-latest
    steps:
      - name: Run CSABD tool
        uses: pipeline-foundation/csabd@main
        with:
            token: ${{ secrets.CSABD_TOKEN }}
            source: '/folder/'
            # for multiple entries use the following syntax with no spaces around commas
            # source: '/folder/,file.cs,/folder/file.cs,/main-folder/sub-folder/'

```

- both parameters are **REQUIRED**

- the secret's name used for token is only exemplary

- be sure to use forward slash in the beginning and end of the folder name `/name-of-folder/` to select a particular folder, because `name-of-folder/` or `name-of-folder` would match `some-name-of-folder/` and/or `/name-of-folder-1` (same with a forward slash in the beginning of a file declaration `/file.cs`)

- see [action.yml](action.yml) for the full documentation for this action's inputs and outputs.

- the action is intended to be used in an independent pipeline, with the [**workflow_dispatch**](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#workflow_dispatch) event to [start it manually](https://github.blog/changelog/2020-07-06-github-actions-manual-triggers-with-workflow_dispatch/), after reviewing the results of a code scanning pipeline and determining the source of the alerts
