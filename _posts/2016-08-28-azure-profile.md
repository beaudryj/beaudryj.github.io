---
layout: post
title: "Using Credentials in your Profile"
excerpt: 
tags: [azure,powershell]
modified: 2016-08-28 00:44:00
date: 2016-08-28 00:44:00
comments: true
image:
 feature: AzurePowershell.png
 thumb: AzurePowershell.png
---

# Do you find logging into azure powershell as annoying as I do? 

Recently I have been getting annoyed with the constant need to log in to an Azure Subscription on my powershell sessions, so I decided to solve this but tweaking my profile with a module that allows me to grab from the Windows Credential Manager.

I took a minute and thought about how to make the shell a bit smarter and figure out a way for my session to already be logged in to AzureRM when I open it. 

This will require:

 *   https://github.com/Jaykul/BetterCredentials
 *   https://www.powershellgallery.com/packages/AzureRM/2.0.1 (Currently the latest as of writing this)
 *   And an active azure subscription 


 
## Install and Use Better Credentials 

### Install Module 

**If you have git installed**

```
cd C:\Users\%youruser%\Documents\WindowsPowerShell\Modules
git clone https://github.com/Jaykul/BetterCredentials
```

  
**If no git**

Download the module from the git repo and extract it to 

```
C:\Users\%youruser%\Documents\WindowsPowerShell\Modules
```

  

**If you are on powershell version 5**

```
Install-Module BetterCredentials
```


### Using Module 

Now you need to create the credential in your credential manager. 

```
#Use this line to store your credentials to a variable to pass to the command to add to the windows credential manager
$Creds = Get-Credential 
#Used to store the credentials 
BetterCredentials\Get-Credential -Credential $Creds -Store
```

Once Stored, you are now able to run

`$AzureCreds = BetterCredentials\Get-Credential -username "yourUsername"`

And this will allow you to easily/quickly pull your credentials from the Windows Credential Manager


## Bringing it together 

Now that you have the initial pieces in place you can modify your profile to configure the auto login.
*this can be found here* -  `C:\Users\%yourUser%\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1`

```
Import-Module BetterCredentials
$AzureCreds = BetterCredentials\Get-Credential -username "yourUsername"
Login-AzureRmAccount -SubscriptionName "your desired default subscription" -Credential $AzureCreds
```

## Closing 

This is just my simple usecase for this, but this use of BetterCredentials and its ability to store and grab from the Credential manager can offer you some other solutions: 

 *   Other Modules requiring Credentials you want Stored
 *   Light automation where you don't want to pass in plaintext passwords
 *   Scheduled tasks 
  
Hopefully this helps you out and you come up with some other things to share. 



 



