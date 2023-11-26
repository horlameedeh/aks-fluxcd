# Terraform AKS cluster, running with FluxCD

This Terraform script will build out an AKS cluster running with FluxCD, which is deployed via Helm. 

If you're unfamiliar with FluxCD, its best to have a read about it on their [website](https://fluxcd.io/). Simply put, it's like a middle men that syncs what's inside your repository with your cluster.

Once, you've the AKS cluster in place, running with Flux. Just grab the credentials for that cluster with the command below.

```bash
 az aks get-credentials --name {your-aks-name} --resource-group {your-aks-rg}
```
You will see, only FluxCD and default related objects as of now. 

As described [here](https://github.com/fluxcd/flux/blob/master/docs/tutorials/get-started.md#giving-write-access), you to need provide your repo the public key and create a deploy key with write access. 

To get the public key, simply run:

```bash
fluxctl identity --k8s-fwd-ns fluxcd
```

Once that's in place, you will see the cluster creating the objects specified within the repo. 

Additional settings for Flux Helm chart [here](https://github.com/fluxcd/helm-operator/tree/master/chart/helm-operator).
