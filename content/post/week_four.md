---
title:       "Week Four"
subtitle:    "Extra Credit"
description: ""
date:        "2024-03-25"
author:      "Charles Vosloo"
image:       ""
tags:        ["tag1", "tag2"]
categories:  ["Tech" ]
---
### Extra Credit
##### Three tasks were sugggested here:    
     
     

1. Package Everything in Helm
2. Implement Persistent Storage
3. Implement Basic CI/CD Pipeline  
4. <span style="color:green;">**Make use of Serverless**</span> 

I completed the second option, implementing Persistant storage, with the release of ecom-web:v2 image. 
The fourth option, Deploy Serverless options, I have added. In the previous version of this challange one of the steps was to add a visitor counter to the website using the cloud provider's serverless function which would be AWS Lambda, Google Cloud Functions or Azure functions. I chose to do something similar **using non proprietary solutions.** On our ecommerce site additional features like email notifications, image procesing, payment processing, inventory managemnet or any kind of analytics could probably more easily be carried out using serverless or rather functions as a service.



How can one implement opensource Severless on civo cloud?
1. OpenFunction
2. OpenFaas

OpenFunction uses Knative, a comprehensive more complex solution that requires a control plain  kubernetes cluster with a minimum of 2 nodes, 4CPU and 8GB memory plus Istio running. 

Civo is a dedicated kubernetes (k3s) cloud provider which embraces popular opensource CNCF products like OpenFaaS:  

 a Function as a Service serverless framework that deploys event-driven functions and microservices to Kubernetes in the form of containers. 

  'Serverless' requires a server. It's only called serverless because when the function is called, from the perspective of the user, where and how the task is carried out is is unnoticed. So, how do we set up and manage an OpenFaas server which we control and own?

There are two ways to run OpenFaas:
1. faas-netes (on a kubernetes cluster)
![faas-netes](/img/of-workflow.png)
OpenFaas makes use of the PLONK stack. While the LAMP stack (linux, apache, mysql, php) is used by our ecommerce site, The JAM stack (javascript, API, markup) is used by this hugo blog, the PLONK stack is comprised of:  
>>Prometheus - metrics and time-series  
>>Linkerd - service mesh   
>>OpenFaaS - management and auto-scaling of compute - PaaS/FaaS   
>>NATS - asynchronous message bus / queue   
>>Kubernetes - declarative, extensible, scale-out, self-healing clustering    

The second option, which I have chosen, is a scaled down version of the above: the kubernetes cluster is scraped in favour of contaierd containers running each function. Easier and more accessible. The downside: loose built in kubernetes features like High Availability.

2. faasd (on a VM running containerd)  
![faasd](/img/faasd-wf.png)

Instead of runnning it on a VM I chose to run the faasd server On Prem, on a raspberry pi. Faasd, a light weight version of OpenFaas, uses Containerd instead of kubernetes which results in it running faster.  This is procedure is explained by the creator, Alex Ellis in his book, [Serverless for everyone else](https://openfaas.gumroad.com/l/serverless-for-everyone-else)

  
The downside: This setup has a single point of failure, but it works, there are no cloud fees, and the raspberry pi address running on my local LAN, is routable externally thanks to the installation of inlets. The other problem particular to South Africa are daily scheduled power outages. After about a day without power my backup system will fail and then the cell phone towers follow (the internet !), taking the pi faasd server out of the game. So if you try my day night switch [ civo public ip address ] and it doesn't work, that is my excuse.

![laptop_pic](/img/half_page_8.5-5.5.png)          
      








the raspberry pi address running on my local LAN, is routable externally thanks to the installation of inlets: 
![inlets](/img/inlets-concept.png)






