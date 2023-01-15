
# Virtual WAN - Single Hub (Mixed)

## Overview

This terraform code deploys a multi-hub (multi-region) virtual WAN architecture playground to observe dynamic routing patterns. In this architecture, we integrate the standard hubs to the virtual WAN hubs.

![Virtual WAN (Single Hub)](../../images/vwan-dual-hub.png)

VNET hubs:
 - `Hub1` (region1) connected to `vHub1` via VWAN VNET connection
 - `Hub2` (region2) connected to `vHub2` via VWAN VNET connection

 Spokes:
 - Direct spoke `Spoke1` (region1) connected to VWAN hub `vHub1`
 - Direct spoke `Spoke4` (region2) connected to VWAN hub `vHub2`
 - Indirect spoke `Spoke2` (region1) with VNET peering to the `Hub1`
 - Indirect spoke `Spoke5` (region2) with VNET peering to the `Hub2`
 - Isolated `Spoke3` (region1) reachable from `Hub1` via Private Link Service
 - Isolated `Spoke6` (region2) reachable from `Hub2` via Private Link Service

 Onprem branches:
 - `Branch1` (region1) simulated in a VNET with a router (cisco-csr-1000v)
 - `Branch3` (region2) simulated in a VNET with a router (cisco-csr-1000v)


## Prerequisites

1. Ensure that you have setup [Azure Cloud Shell](https://learn.microsoft.com/en-us/azure/cloud-shell/overview) environment.
2. (Optional) If you prefer to run the code on a local terminal, ensure that you have installed and configured [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli) and [Terraform](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli), and ignore step 3.
3. Launch a `Cloud Shell` terminal to be used for the remaining steps.

## Clone the Lab

Open a Cloud Shell terminal and run the following command:
1. Clone the Git Repository for the Labs
```sh
git clone https://github.com/kaysalawu/azure-network-terraform.git
```

2. Change to the lab directory
```sh
cd ~azure-network-terraform/2-virtual-wan/2-virtual-wan-dual-hub
```

## Deploy the Lab

To deploy the lab run the following terraform commands and type **yes** at the prompt:
```sh
terraform init
terraform plan
terraform apply
```

## Cleanup

Delete the resource group to remove all resources installed. Run the following Azure CLI command:

```sh
az group delete --name VwanS2RG --yes --no-wait
```

## [Troubleshooting](../../troubleshooting/)

Go to the [troubleshooting](../../troubleshooting/) section for tips on how to resolve common issues that may occur during the deployment of the lab.