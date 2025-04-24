---
title: "AKS Cluster Login Access"
permalink: /samples/aks-access/
layout: single
author_profile: false
---

## Overview
Before managing or deploying workloads in the Azure Kubernetes Service (AKS), you must gain access to the relevant cluster using Azure CLI and kubectl. 
---

## Prerequisites

- Install Azure CLI 
- Install kubectl 
- If IP is allowed if cluster IP restrictions are enabled 

## Gaining Cluster Access

1. Navigate to the relevant AKS cluster. 
2. Use Privileged Identiy Management (PIM) to assign yourself the role: **TRG Custom Role | MGMT AKS Cluster Administrator**. 
3. Open the Azure CLI and run the following commands. 
	- Log in to Azure 

	```bash
	az login
	``` 

	- Set the correct subscription: 

	```bash
	az account set --subscription <SUBSCRIPTION_ID>
	``` 

	- Retrieve the AKS Cluster Credentials: 

	```bash
	az aks get-credentials –resource-group <RESOURCE_GROUP> --name <AKS_CLUSTER_NAME>
	``` 

	- Verify the connection: 

	```bash
	kubectl cluster-info
	``` 

If successful, the Kubernetes control plane and services should be visible. If not, recheck the prerequisites and ensure PIM role assignment is complete.
