
# Helm Cheat Sheet (Basic to Advanced)

This is a quick reference guide for common Helm commands with explanations, starting from basic to advanced usage.

## Basic Commands

| **Command** | **Description** |
|-------------|-----------------|
| `helm install <release-name> <chart>` | Install a Helm chart. Deploys a Helm chart into a Kubernetes cluster. `<release-name>` is the name of the release, and `<chart>` is the name of the chart to install. |
| `helm list` | List installed releases. Shows all Helm releases installed on the Kubernetes cluster. |
| `helm uninstall <release-name>` | Uninstall a release. Deletes a previously installed Helm release and associated resources. |
| `helm search <keyword>` | Search for charts. Searches Helm chart repositories by a keyword, helping you find available charts to install. |
| `helm repo add <repo-name> <repo-url>` | Add a Helm chart repository. Adds a remote chart repository to your Helm configuration. `<repo-name>` is the name for the repo, and `<repo-url>` is the URL where the chart repository is hosted. |
| `helm repo update` | Update the list of charts in repositories. Synchronizes your local chart repository cache with the remote repositories. |
| `helm fetch <chart>` | Download a chart archive. Downloads the chart to your local filesystem, but does not install it. |
| `helm show <chart>` | Display detailed info about a chart. Displays metadata and documentation for the specified chart. |

## Intermediate Commands

| **Command** | **Description** |
|-------------|-----------------|
| `helm upgrade <release-name> <chart>` | Upgrade a release. Upgrades an existing release to a newer version based on the specified chart. |
| `helm rollback <release-name> <revision>` | Roll back a release to a previous version. Restores a specific revision of a release. |
| `helm status <release-name>` | Get the status of a release. Displays the current status of a Helm release (e.g., deployed, failed). |
| `helm get all <release-name>` | Show all details of a release. Retrieves detailed information about the specified release, including its status and resources. |
| `helm template <chart>` | Generate Kubernetes manifests from a chart. Renders the chart templates locally and shows the Kubernetes resources that would be applied. |
| `helm test <release-name>` | Run tests for a release. Executes any test hooks defined in the chart to verify the application's functionality. |

## Advanced Commands

| **Command** | **Description** |
|-------------|-----------------|
| `helm lint <chart>` | Lint a chart for errors. This command checks a chart for common issues before installing it, helping ensure correctness. |
| `helm install <release-name> <chart> --dry-run` | Simulate an install without making changes. This command runs the installation without applying changes, useful for previewing results. |
| `helm install <release-name> <chart> --set <key=value>` | Override values when installing a chart. Allows you to set or override specific configuration values in the chart using key-value pairs. |
| `helm upgrade <release-name> <chart> --set <key=value>` | Override values when upgrading a release. Similar to install, but applies to existing releases that are being upgraded. |
| `helm fetch <chart> --untar` | Download and extract a chart archive. Fetches a chart and extracts it to a folder, useful for inspection or modification. |
| `helm dependencies update <chart>` | Update dependencies for a chart. Downloads and updates any dependencies listed in the chart's `Chart.yaml`. |
| `helm history <release-name>` | Show the release history. Displays the list of revisions of a given release, showing past versions. |
| `helm uninstall <release-name> --purge` | Uninstall a release and remove all associated resources. Ensures complete removal, including any residual Kubernetes resources. |
| `helm status <release-name> -o yaml` | Show the release status in YAML format. Displays the status of a release in YAML, useful for parsing or automation. |

