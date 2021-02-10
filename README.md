# Code scanning alerts bulk dismissal
An action that lets you automatically dismiss a large amount of code scanning alerts, based on the file(s) source

**Table of Contents**

- [Platforms](#platforms)
- [Usage](#usage)

## Platforms

The action works on:

- **windows-latest**
- **ubuntu-latest**

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
            alerts_dis_path: 'folder/'

```

- both parameters are **REQUIRED**

- the secret's name used for token is only exemplary

- see [action.yml](action.yml) for the full documentation for this action's inputs and outputs.

- the action is intended to be used in an independent workflow, with the [**workflow_dispatch**](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#workflow_dispatch) event to [start it manually](https://github.blog/changelog/2020-07-06-github-actions-manual-triggers-with-workflow_dispatch/), after reviewing the results of the code scanning workflow and determining the source of the alerts
