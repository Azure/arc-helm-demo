# Official Helm based cluster configuration sample for Azure Arc enabled Kubernetes

This repository contains a sample Helm chart that can be deployed using GitOps to an Azure Arc enabled Kubernetes cluster.

## Contents

| File/folder          | Description                                |
|----------------------|--------------------------------------------|
| `charts`             | Contains sample helm chart                 |
| `releases`           | Release configuration picked up by Flux    |
| `.gitignore`         | Defines what to ignore at commit time.     |
| `README.md`          | This README file.                          |
| `CODE_OF_CONDUCT.md` | Microsoft code of conduct.                 |
| `LICENSE`            | The license for the sample.                |

## Prerequisites

One or more Kubernetes clusters are [connected to Azure Arc](https://docs.microsoft.com/en-in/azure/azure-arc/kubernetes/connect-cluster) using the `connectedk8s` Azure CLI extension.

## Running the sample

Create a GitOps configuration referencing this sample repo by using the Azure CLI extension `k8sconfiguration` or Azure portal. Complete documentation on the available options can be found [here](https://docs.microsoft.com/en-in/azure/azure-arc/kubernetes/use-gitops-connected-cluster).

After a configuration is created, Azure Arc enabled Kubernetes agents and flux will create use the configuration in the repository to create a Helm release on this cluster.

```bash
az k8sconfiguration create --name azure-js-app \
    --resource-group $RESOURCE_GROUP --cluster-name $CLUSTER_NAME \
    --operator-instance-name flux --operator-namespace arc-k8s-demo \
    --operator-params='--git-readonly --git-path=releases' \
    --enable-helm-operator --helm-operator-version='0.6.0' \
    --helm-operator-params='--set helm.versions=v3' \
    --repository-url https://github.com/Azure/arc-helm-demo.git  \
    --scope namespace --cluster-type connectedClusters
```

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
