---
layout: post
title: "Loadbalancing your Web Application in Azure"
excerpt: 
tags: [azure,powershell,networking]
modified: 2016-09-02
date: 2016-09-02
comments: true
image:
 feature: AzurePowershell.png
 thumb: AzurePowershell.png
---

# In search of the perfect solution for loadbalancing your application in Azure?  

This year I have spent a lot of time moving our physical disaster recovery site over to Azure. One of the biggest hurdles to overcome was transitioning our physical loadbalancer over to a software based solution. Granted we are not doing any heavy loadbalancing, just simple right of slash rules and SSL termination. 

The solution we ended up deciding on was the [Azure Application Gateway](https://azure.microsoft.com/en-us/services/application-gateway/) this offered us a simple and scalable solution for an affordable rate. This also offered us an easy path for loadbalancing our to be built Azure PaaS (Platform as a Solution) pieces. 



## It's an Intricate Beast... 
