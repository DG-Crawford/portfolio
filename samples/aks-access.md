---
title: "AKS Cluster Login Access"
permalink: /samples/aks-access/
layout: single
author_profile: true
author: davidcrawford
---

3-minute walkthrough. Objective: authenticate to Azure, pull AKS credentails, and verify cluster connectivity.

<div class="video">
  <iframe
    width="900"
    height="506"
    src="https://www.youtube-nocookie.com/embed/TsGVjjBd62Y"
    title="AKS Cluster Login Access - Walkthrough"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    allowfullscreen>
  </iframe>
  <p><a href="https://youtu.be/TsGVjjBd62Y" target="_blank" rel="noopener">Watch on YouTube.</a></p>
</div>

## Overview
Before managing or deploying workloads in the Azure Kubernetes Service (AKS), you must gain access to the relevant cluster using Azure CLI and kubectl.

## Prerequisites

- Install Azure CLI 
- Install kubectl 
- If the cluster restricts inbound IPs, your client IP must be allowlisted (or you must be on the required network/VPN). 

## Gaining Cluster Access

1. Navigate to the relevant AKS cluster. 
2. Use Privileged Identity Management (PIM) to assign yourself the role: **TRG Custom Role - MGMT AKS Cluster Administrator**. 
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
	az aks get-credentials –-resource-group <RESOURCE_GROUP> 
	--name <AKS_CLUSTER_NAME>
	``` 

	- Verify the connection: 

	```bash
	kubectl cluster-info
	``` 

If successful, the Kubernetes control plane and services should be visible. If not, recheck the prerequisites and ensure PIM role assignment is complete.
