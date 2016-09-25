---
layout: post
title: "Automating your cloud"
excerpt: 
tags: [azure,powershell]
modified: 2016-08-28 00:44:00
date: 2016-08-28 00:44:00
comments: true
image:
 feature: AzurePowershell.png
 thumb: AzurePowershell.png
---

# Do you want to centralize your scripts for your cloud? 

Over the last few months I have been working on bringing together my scripts for common activities in the cloud to an orchestration tool, for my team to access and manage our cloud based disaster recovery. Usually my go to orchestrator in our environment is [Jenkins](http://jenkins.io), however the members of the team I am currently working with have no experience or interest in jenkins. So I started down the path of [Azure Automation](https://azure.microsoft.com/en-us/services/automation/) which allows for a lot of simple and useful features out of the box, while staying in the environment we are in.

Azure Automation brings together a lot of useful functions into one single pane. 

    * DSC Authoring 
    * DSC Managing / Monitoring (In Azure or OnPrem)
    * Scheduled Script Runs 
    * Powershell Authoring 
    * Powershell Graphical Runbooks 
    * Hybrid Run Books 

This allowed me to start building out some simple yet powerful pieces for my environment, and allowed me to quickly set things up and give me a path for simple knowledge transfer to my co-workers. 
