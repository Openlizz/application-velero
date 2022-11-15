<h1 align="center">Lizz compatible Velero application</h1>

Lizz compatible application to add the [Velero application](https://velero.io/) to a lizz managed Kubernetes cluster.

To learn more about Lizz, see the [documentation](https://openlizz.com).

## Requirements

To add the application, you first need to have a [Kubernetes cluster initialized with Lizz](https://openlizz.com/docs/guides/init).
You also need to have the [Lizz CLI installed](https://openlizz.com/docs/installation).

## Add the application

To add the application to your cluster, run the following:

```bash
lizz add github \
    --owner=$GITHUB_USER  \
    --fleet=fleet \
    --origin-url=https://github.com/openlizz/application-velero \
    --path=./default \
    --destination=nginx \
    --cluster-role \
    --personal
```

Check the [guide](https://openlizz.com/docs/guides/add) to understand how works the lizz add command.

> **Note**
> You can adapt the command depending on your use case. See the [command API](https://openlizz.com/docs/cli/lizz_add_github) for more information.

Reconcile the fleet repository to deploy the application using [Flux](https://fluxcd.io/):

```
flux reconcile source git flux-system
```

Check the pods with:

```
kubectl -n velero get pod
```

## Usage

Refer to the [user manuel](https://velero.io/docs/v1.10.0-rc.1/) to learn how to use Velero.

## Acknowledgements

This repository is only a wrapper to the [Helm chart](https://github.com/vmware-tanzu/helm-charts/tree/main/charts/velero) of the [Velero application](https://velero.io/) to help its deployment in a Kubernetes cluster managed by Lizz.

Therefore, the credit goes to the developers and maintainers of the application and the chart.
