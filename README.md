# GitHub Action - Variable creation/updation

This action is made for creating and updating GitHub variables for a specific environment.

## Usage

The action is quite simple and can be used for any GitHub organization, the main need is an [Personal Access Token] with the necessary permissions.

When something go wrong the action will throw an error and break the workflow.

### Example workflow

```yaml
name: My Workflow
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: Run action

      uses: <orgnization>/gha-create-repo-variable-for-env@main
      with:
        VariableName: "variable-name"
        VariableValue: "variable-value"
        Environment: "dev"
        Organization: "<orgnization>"
        Repository: "repository name"

```

### Inputs

| Input                                             | Description                                        |
|------------------------------------------------------|-----------------------------------------------|
| `GitHubToken`  | Personal access token from GitHub - it must have permission to create projects in the requested organization    |
| `VariableName`  | Variable name that needs to be added to a specific reposistpory within an environment    |
| `VariableValue`  | Variable value that needs to be created/updated to a specific reposistpory within an environment    |
| `Environment`  | Environment to which the variable needs to be created/updated    |
| `Organization`   | Organization where to create the environments    |
| `Repository`   | Repository name where the environment variable needs to be created/updated  |

## Examples

### Using the optional input

This is how to use the optional input.

```yaml
    uses: ./gha-create-repo-variable-for-env/
    with:
      GitHubToken: ${{ variables.PAT }}
      VariableName: "ClientID"
      VariableValue: "ClientID_Value"
      Environment: "dev"
      Organization: "<orgnization>"
      Repository: "npet-testingsolutionrepo"
```
