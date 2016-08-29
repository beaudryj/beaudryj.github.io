---
layout: post
title: "Testing the Waters"
excerpt: 
tags: [azure,powershell]
modified: 2016-08-28 00:44:00
date: 2016-08-28 00:44:00
comments: true
image:
 feature: AzurePowershell
---

# Are you as annoyed with logging into your shell for a quick job as I am ? 

This past week I had been working on some developmental infrastructure in azure that I have not fully automated yet. This process has some speed bumps and annoyances with azure. The biggest one being that when I open my powershell prompt to work with it I have to log into Azure. Which is fine for quick tasks and doing things that I can do fairly mindlessly. But it has gotten to the point where I need 3 or 4 session open to work on what I have or else I have to carry out the tasks in serial. 

So I took a minute and thought about how to make the shell a bit smarter and figure out a way for my session to already be logged in when I open it. 

This will require - 
 - https://github.com/Jaykul/BetterCredentials
 - https://www.powershellgallery.com/packages/AzureRM/2.0.1 (Currently the latest as of writing this)
 - And an active azure subscription 
 
## Install and Use Better Credentials 

### Install Module 

**If you have git installed**

~~~~
cd C:\Users\%youruser%\Documents\WindowsPowerShell\Modules
git clone https://github.com/Jaykul/BetterCredentials
~~~~

**If no git**
Download the module from the git repo and extract it to 
C:\Users\%youruser%\Documents\WindowsPowerShell\Modules

**If you are on powershell version 5**

~~~~
Install-Module BetterCredentials
~~~~


### Using Module 

Now you need to create the credential in your credential manager. 

~~~~
#Use this line to store your credentials to a variable to pass to the command to add to the windows credential manager
$Creds = Get-Credential 
#Used to store the credentials 
BetterCredentials\Get-Credential -Credential $Creds -Store
~~~~ 

Once Stored, you are now able to run: 
~~~~
$AzureCreds = BetterCredentials\Get-Credential -username "yourUsername"
~~~~
And this will allow you to easily/quickly pull your credentials from the Windows Credential Manager


## Bringing it together 

Now that you have the initial pieces in place you can modify your profile to configure the auto login.
*this can be found here* -  **C:\Users\%yourUser%\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1**

~~~~
Import-Module BetterCredentials
$AzureCreds = BetterCredentials\Get-Credential -username "yourUsername"
Login-AzureRmAccount -SubscriptionName "your desired default subscription" -Credential $AzureCreds
~~~~

## Closing 

This is just my simple usecase for this, but this use of BetterCredentials and its ability to store and grab from the Credential manager can offer you some other solutions: 
  - Other Modules requiring Credentials you want Stored
  - Light automation where you don't want to pass in plaintext passwords
  - Scheduled tasks 
  
Hopefully this helps you out and you come up with some other things to share. 



 



