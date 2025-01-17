
# Helm Cheat Sheet

This is a quick reference guide for common Helm commands with explanations.

| **Command** | **Description** |
|-------------|-----------------|
| `helm install <release-name> <chart>` | Install a Helm chart. This command deploys a Helm chart into a Kubernetes cluster. `<release-name>` is the name you give to the release, and `<chart>` is the name of the chart to install. |
| `helm upgrade <release-name> <chart>` | Upgrade a release. If the release already exists, this command upgrades it to a newer version based on the specified chart. |
| `helm uninstall <release-name>` | Uninstall a release. This command deletes a previously installed Helm release and all associated resources. |
| `helm list` | List installed releases. This shows all the Helm releases that are installed on the Kubernetes cluster. |
| `helm search <keyword>` | Search for charts. You can search a Helm chart repository by a keyword. This command helps you find available charts to install. |
| `helm show <chart>` | Display detailed info about a chart. This command provides metadata and documentation for the specified chart. |
| `helm repo add <repo-name> <repo-url>` | Add a Helm chart repository. Adds a remote chart repository to your Helm configuration. `<repo-name>` is the name you assign to the repo, and `<repo-url>` is the URL where the chart repository is hosted. |
| `helm repo update` | Update the list of charts in repositories. It synchronizes your local chart repository cache with the latest version from the remote repositories. |
| `helm fetch <chart>` | Download a chart archive. This command downloads a chart to the local filesystem, but it does not install it. |
| `helm template <chart>` | Generate Kubernetes manifests from a chart. This command renders the chart templates locally and displays the Kubernetes resources that would be applied. |
| `helm install <release-name> <chart> --dry-run` | Simulate an install without making changes. It runs the install command without applying any changes to the cluster, useful for previewing the result. |
| `helm get all <release-name>` | Show all details of a release. Retrieves all information about the specified release, including its status and resources. |
| `helm status <release-name>` | Get the status of a release. Displays the status of a specific Helm release, showing if it is deployed or in a different state. |
| `helm rollback <release-name> <revision>` | Roll back a release to a previous version. This restores a specific revision of the release to its previous state. |
| `helm history <release-name>` | Show the release history. Displays the list of revisions of a given release. |
| `helm test <release-name>` | Run tests for a release. This executes any test hooks defined in the chart to verify if the application is working properly. |
| `helm lint <chart>` | Lint a chart for errors. This command checks a chart for common issues before installing it. |
| `helm dependencies update <chart>` | Update dependencies for a chart. Downloads and updates any dependencies for the specified chart. |
| `helm install <release-name> <chart> --set <key=value>` | Override values when installing a chart. Allows you to customize the chart values by providing a key-value pair. |
| `helm upgrade <release-name> <chart> --set <key=value>` | Override values when upgrading a release. Similar to install, but used to update an existing release with new configuration. |
| `helm fetch <chart> --untar` | Download and extract a chart archive. Fetches a chart and extracts it to a folder for inspection or modification. |
| `helm status <release-name> -o yaml` | Show the release status in YAML format. Displays the status of the release in YAML format for easier parsing or automation. |
| `helm uninstall <release-name> --purge` | Uninstall a release and remove all associated resources. This ensures complete removal, including any residual Kubernetes resources. |
