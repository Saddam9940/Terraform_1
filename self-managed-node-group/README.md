# EKS Cluster w/ Self Managed Node Groups

## Features

If there are features that you think are missing, please feel free to open up a discussion via a GitHub issue. This is a great way to collaborate within the community and capture any shared knowledge for all to see; I will do my best to ensure that knowledge is captured somewhere within this project so that others can benefit from it.

- Very simple and straightforward EKS cluster that utilizes self managed node groups

## Steps to Provision

### Prerequisites:

Ensure that you have the following tools installed locally:

1. [aws cli](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
2. [kubectl](https://Kubernetes.io/docs/tasks/tools/)
3. [terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli)

### Deployment

1. Provision resources as they are defined in the `us-east-1` directory using:

```bash
terraform init -upgrade=true
terraform apply
```

2. Once the cluster is up and running and the node group is provisioned, update your Terraform state to align with changes made by the AWS API. This doesn't modify any resources, it just simply aligns your statefile with the current state. You can read more about this at the following links if interested:

- https://github.com/hashicorp/terraform/pull/28634
- https://github.com/hashicorp/terraform/issues/28803

```bash
terraform apply -refresh-only
terraform plan # should show `No changes. Your infrastructure matches the configuration.`
```

### Tear Down & Clean-Up

1. Remove the resources created by Terraform

```bash
terraform destroy
```
