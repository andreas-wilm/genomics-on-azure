# Genomics on Azure

## Cromwell

TODO

## Microsoft Genomics

TODO

## Snakemake

Snakemake can be run as-is on a big Azure VM or an HPC cluster deployment like [Azure CycleCloud](https://azure.microsoft.com/en-us/features/azure-cyclecloud/).

### Commercial support

Snakemake is commerically supported through [BizData](https://www.bizdata.com.au/). The service is called [Genomics Pipeline Acceleration OnDemand](https://www.bizdata.com.au/genomics-ondemand) and runs on [Azure Batch Shipyard](https://azure.github.io/batch-shipyard/). It requires only minimal modifcation of your Snakefile. 
This was featured as a [Microsoft Customer story](https://news.microsoft.com/en-au/features/cloud-computing-spurs-australias-genome-research-opens-field-to-clinical-application/).

### Azure Kubernetes Services (AKS)

Snakemake can be run on AKS without the need for a shared filesystem (persistent volume). Data for each step is staged automatically in and out from Blob storage, which makes this cheap and resilient.

This hasn't been tested yet at scale or with low-prio VMs.

**References:**
- [Snakemake documentation on AKS](https://snakemake.readthedocs.io/en/stable/executor_tutorial/azure_aks.html)
- [Original Blog post: Running Snakemake on an auto-scaling Azure Kubernetes cluster without shared filesystem](https://andreas-wilm.github.io/2020-06-08-snakemake-on-ask/)
- [Blog post: Using Azure Container Registries with Snakemake and AKS](https://andreas-wilm.github.io/2020-06-11-snakemake-on-aks-with-acr/)


### Azure Batch

Azure Batch support is work in progress. At the time of writing use of spot instances, job placement and autoscaling
all needed testing or implementation.

**References:**
- [Original Blog post: Integrating Azure Batch support in Snakemake](https://andreas-wilm.github.io/2020-07-30-azure-batch-in-snakemake/)
- [Work in progress Github PR](https://github.com/snakemake/snakemake/pull/533)


## Nextflow

Nextflow can be run as-is n a big Azure VM or an HPC cluster deployment like [Azure CycleCloud](https://azure.microsoft.com/en-us/features/azure-cyclecloud/).

### Commercial support

Nextflow is supported through [SeqeraLabs](https://seqera.io/), which was founded by its authors. However Azure support is not an existing offer.

### Azure Kubernetes Services (AKS)

Nextflow can run on AKS using Nextflow's Kubernetes executor (`kuberun`). See this [blog post](https://yangfan2010.wordpress.com/2018/09/26/nextflow-with-azure-kubernetes-service-aks-a-tutorial-with-working-pipeline/) for more info. This uses a persistent (Azure Files) volume as shared filesystem. Note, this is based on an older version of Nextflow, so some details might have changed in the meantime.

### Azure Batch

Nextflow currently doesn't support Azure Batch. The reason was a missing feature in the Azure Java SDK (NIO FileSystemProvider), which has now (July 2020) been implemented. See references for more information and current status.

**References:**
- [Github issue: JSR203 NIO FileSystemProvider?](https://github.com/Azure/azure-sdk-for-java/issues/7158)
- [Github issue: Java NIO2 FileSystemProvider implementation for Azure](https://github.com/nextflow-io/nextflow/issues/839)
- [Github issue: Support Azure Batch as additonal executor #1430](https://github.com/nextflow-io/nextflow/issues/1430)


### Apache Ignite

Nextflow can be run on Azure using Apache Ignite with this [deployment template](https://azure.microsoft.com/en-us/resources/templates/nextflow-genomics-cluster-ubuntu/).

TODO:STATUS?

**References:**
- [Azure Deployment template](https://azure.microsoft.com/en-us/resources/templates/nextflow-genomics-cluster-ubuntu/).
- [Nextflow and Apache Ignite](https://www.nextflow.io/docs/latest/ignite.html)
