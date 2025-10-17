# GitHub Workflow Example

This repository contains an example GitHub workflow that demonstrates how to use the `peter-evans/create-pull-request` action with a `workflow_dispatch` trigger.

## Workflow: Update Data

The workflow file is located at `.github/workflows/update-data.yml`.

### What it does:

1. Can be triggered manually through the GitHub UI or API
2. Makes changes to data files (simulated in this example)
3. Creates a pull request with those changes using `peter-evans/create-pull-request` action

### Inputs:

When manually triggering the workflow, you can provide:

- **Commit message**: The message used for the commit and PR title
- **Branch name**: The name of the branch for the PR

### How to use:

1. Navigate to the "Actions" tab in your repository
2. Select the "Update Data" workflow
3. Click "Run workflow"
4. Fill in the inputs (or use the defaults)
5. Click "Run workflow" to start the process
6. Once completed, a new pull request will be created with your changes

## Key Features

- Uses `workflow_dispatch` for manual triggering
- Allows customization through workflow inputs
- Creates PRs automatically with peter-evans/create-pull-request@v7
- Sets appropriate PR title, body, and labels
- Outputs PR information for reference