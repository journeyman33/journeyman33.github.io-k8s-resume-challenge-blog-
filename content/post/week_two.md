---
title:       "Week Two"
subtitle:    "Kubernetes Management and scaling"
description: ""
date:        "2024-03-15"
author:      "Charles Vosloo"
image:       ""
tags:        ["tag1", "tag2"]
categories:  ["Tech" ]
---
## Step 3: Set Up Kubernetes on a Public Cloud Provider
Civo cloud offers a managed kubernetes service cncf 'enforsed' based on the k3s distribution which is a light weight distribution, still fully compliant.

civo apikey is linked to kubectl on my wsl laptop

## Step 4: Deploy Your Website to Kubernetes
Kubernetes Deployment:  
Create a website-deployment.yaml defining a Deployment that uses the Docker image created in earlier.  
Ensure the Deployment specifies the necessary environment variables and mounts for the database connection.  
Outcome: The e-commerce web application is running on Kubernetes, with pods managed by the Deployment.

## Step 5: Expose Your Website
website-service.yaml to create a Service of type LoadBalancer.  
 This Service exposes your Deployment to the internet.
Outcome: An accessible URL or IP address for your web application.