# cl-devwks-1314
Cisco Live DevNet Workshop 1314
# Automating with Cisco Workflows Introduction

## Learning Objectives
This session is designed to introduce you to Cisco Workflows and give you hands on practice.
* Setup connects to external environments
* Install and run a pre-built workflow
* Build a workflow without coding
* Bonus - Use AI to run your workflow

## Getting Started
#### Lab Access
Cisco Worklfows is hosted in the Meraki Dashboard.  Open a browswer and navigate to https://dashboard.meraki.com.  
You'll use the credentials assigned to you by your Lab Admin.
The current username will be devwksuser+*[Pod #]*@gmail.com
The current password should be C1sco12345.

#### Generate an API Key
You'll need to create an API Key if one isn't provided.  API keys are per user and are found here:
1. Click on the Organization Menu
2. Under *Configuration*, select *API & Webhooks*
3. At the top, select the section called *API keys and access*
4. Click on the blue *Generate API Key* button
5. Copy the API key and save it to the Scratch pad text file on the desktop
6. Check the box stating you've safely stored your API key and click the Done button.

## Connect your accounts
#### We'll need to connect Workflows to your lab environments.

Workflows offer pre-built automations (activities) for solutions such as Meraki, Catalyst
Center, Catalyst SD-WAN, Cisco ISE, ServiceNow, and more. In this lab, we will walk you
through key components of Workflows and demonstrate a pre-built Meraki workflow
ready for use.

##### First we'll create a connection to the Meraki environment via API.
1. Under the Automation menu, select Targets.
2. Click the box + New target
3. Select Target Type:  Meraki Endpoint
4. Display Name: Meraki-DEVWKS1314-*[Pod #]*
5. Select the Account Key.  If one exists, choose it.  If not, Add new.
6. To add/edit an Account Key, Add the name Meraki API and add the API Key generated in the last section.
7. Hit save and check that the Status of your Target is blue and says Valid.

Congratulations!  You connected your first target to Workflows and can now begin automating Meraki solutions!

## Install and Run your first Workflow
#### Now that we've connected Meraki, let's start setting up your networks.  

The Exchange allows you to install workflows that are created and supported by Cisco and others to facilitate your journey of automation with zero to minimal coding experience.  Let's start with a pre-built workflow to setup wireless.
#### Let's install your first workflow from the Exchange
1. Under the Automation menu, select Exchange.
2. Find the workflow called *Create Wireless SSID with PSK Authentication* and click the Install button.
3. This will describe all the pieces included with this workflow and what it does.  Click Install.
4. Some worklows need information from you specific to your environment before running.  This workflow is asking for the PSK.  Enter a PSK of your liking.  You can also choose to skip this configuration and have it prompt later when running it if desired.
5. Click Next and it will begin installing the workflow.  You should get an Installation Succeeded pop-up shortly.  Choose *Maybe later* when asked if you'd like to automate it to proceed.

#### Now let's run that workflow
1. Under the Automation menu, select Workspace.
2. You should see your new Worklow installed at the top.  Click on the ellipsus/meatball menu button and select Run.
3. The workflow is created with case sensitive input variables.  You will be prompted to fill out the information needed to setup wireless in this network.  Use the following info:
   + Target: Select your target created earlier Meraki-DEVWKS1314-X
   + PSK Password:  Should be filled out when installing the workflow.
   + Encryption Mode:  wpa
   + SSID Number: 0
   + Wireless SSID Name:  Cisco Live Wireless
   + Organization Name or ID:  Pod - X [X is your pod number]
   + Network Name:  Copenhagen
   + Enable SSID: True
   + WPA Encryption Mode:  WPA2 only
4. Click Run and watch your workflow begin.  Blue boxes are "running".  Green boxes are completed successfullly.  Red boxes completed with errors.  If you have any red boxes, please raise your hand and we'll come help you figure out what happened.
5. You can view the results of workflows previously ran under the *Run Monitoring* menu option as well.

Verify under the Copenhagen network that the wireless settings are configured successfully.
