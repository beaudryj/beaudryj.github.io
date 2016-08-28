---
layout: post
title: "Testing the Waters"
excerpt: 
tags: [azure,powershell]
modified: 2016-08-28 3:50:00
date: 2016-08-28 3:50:00
comments: true
image:
 feature: AzurePowershell
 thumb: 
---

# Are you as annoyed with logging into your shell for a quick job as I am ? 

This past week I had been working on some developmental infrastructure in azure that I have not fully automated yet. This process has some speed bumps and annoyances with azure. The biggest one being that when I open my powershell prompt to work with it I have to log into Azure. Which is fine for quick tasks and doing things that I can do fairly mindlessly. But it has gotten to the point where I need 3 or 4 session open to work on what I have or else I have to carry out the tasks in serial. 

So I took a minute and thought about how to make the shell a bit smarter and figure out a way for my session to already be logged in when I open it. 

This will require - 
 - https://github.com/Jaykul/BetterCredentials
 - https://www.powershellgallery.com/packages/AzureRM/2.0.1 (Currently the latest as of writing this)
 - And an active azure subscription 
 - 
 
## Install and Use Better Credentials 

**If you have git installed**

~~~~
cd C:\Documents\WindowsPowerShell\Modules
~~~~



**If you are on powershell version 5**

 



