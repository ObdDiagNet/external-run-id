# Get External Workflow Run ID
[![GitHub Marketplace](https://img.shields.io/badge/Marketplace-External_Workflow_ID-brightgreen?logo=github)](https://github.com/marketplace/actions/get-external-workflow-run-id)

A GitHub Action that fetches the ID of the latest successful workflow run from an external repository. It may be useful to configure download Artifacts from other repositories.

## Usage

```yaml
- name: Get External Run ID
  id: get-run-id
  uses: ObdDiagNet/external-run-id@v1
  with:
    repository: 'owner/repo'
    workflow-file: 'build.yml'
    github-token: ${{ secrets.PAT_TOKEN }}

- name: Use the run ID
  run: echo "Latest run ID is ${{ steps.get-run-id.outputs.run_id }}"
```

## Inputs

| Input | Description | Required |
|-------|-------------|----------|
| `repository` | The owner/repo name of the source repository (e.g., `my-org/my-app`) | Yes |
| `workflow-file` | The file name of the source workflow (e.g., `build.yml`) | Yes |
| `github-token` | Personal Access Token (PAT) with `actions:read` scope for the source repo | Yes |

## Outputs

| Output | Description |
|--------|-------------|
| `run_id` | The ID of the latest successful workflow run |

## Requirements

- The GitHub token must have `actions:read` permission for the target repository
- For private repositories, a Personal Access Token (PAT) with appropriate permissions is required

## License

[MIT](LICENSE)
