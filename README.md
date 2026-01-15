# cl-devwks-1314
### Cisco Live DevNet Workshop 1314
# Automating with Cisco Workflows Introduction

## Learning Objectives
This session is designed to introduce you to Cisco Workflows and give you hands on practice.
* [Getting started and connect to lab environment](#getting-started)
* [Connect Workflows to Meraki](#connect-workflows-to-meraki)
* [Install and run a pre-built workflow](#install-and-run-your-first-workflow)
* [Build a workflow without coding](#create-a-workflow)
* [Bonus - Use AI to run your workflow](#bonus-content)

___
## Getting Started
### Lab Access
Cisco Worklfows is hosted in the Meraki Dashboard.  Open a browswer and navigate to https://dashboard.meraki.com.    
You'll use the credentials assigned to you by your Lab Admin.  
The current username will be devwksuser+*[Pod #]*@proton.me  
The current password should be C1sco12345  
> ⭐⭐ Youruser should have access to two organizations.  Please ensure you are using the WKS-1314 Pod*X* organization and **NOT the zzCLEMEA Bighorn** Organization.  If you don't see the WKS-1314 Pod*x* org, please contact the lab proctor.

### Generate an API Key
You'll need to create an API Key if one isn't provided.  API keys are per user and are found here:
1. Click on the Organization Menu
2. Under *Configuration*, select *API & Webhooks*
3. At the top, select the section called *API keys and access*
4. Click on the blue *Generate API Key* button
![Menu screenshot](/media/1.png)
5. Copy the API key and save it to a text file on the desktop
6. Check the box stating you've safely stored your API key and click the Done button.
![API screenshot](/media/2.png)

___
## Connect Workflows to Meraki
### We'll need to connect Workflows to your lab environments.

Workflows offer pre-built automations (activities) for solutions such as Meraki, Catalyst
Center, Catalyst SD-WAN, Cisco ISE, ServiceNow, and more. In this lab, we will walk you
through key components of Workflows and demonstrate a pre-built Meraki workflow
ready for use.

#### First we'll create a connection to the Meraki environment via API.
> ⭐⭐ $${\color{orange}Remember}$$ $${\color{orange}to}$$ $${\color{orange}use}$$ $${\color{orange}the}$$ **$${\color{green}WKS-1314}$$ $${\color{green}Pod}$$** $${\color{orange}Organization}$$ ⭐⭐
1. Under the Automation menu, select Targets.
2. Click the box + New target
![Target screenshot](/media/3.png)
3. Select Target Type:  Meraki Endpoint
4. Display Name: Meraki-DEVWKS1314-*[Pod #]*
5. Select the Account Key.  If one exists, choose it.  If not, Add new.
6. To add/edit an Account Key, Add the name Meraki API and paste the API Key generated in the last section.
![account key screenshot](/media/4.png)
7. Hit save and check that the Status of your Target is blue and says Valid.

#### Congratulations!  You connected your first target to Workflows and can now begin automating Meraki solutions!

___
## Install and run your first Workflow
### Now that we've connected Meraki, let's start setting up your networks.  

The Exchange allows you to install workflows that are created and supported by Cisco and others to facilitate your journey of automation with zero to minimal coding experience.  Let's start with a pre-built workflow to setup wireless.
### Let's install your first workflow from the Exchange
1. Under the Automation menu, select Exchange.
2. Find the workflow called *Create Wireless SSID with PSK Authentication* and click the Install button.
![exchange screenshot](/media/5.png)
3. This will describe all the pieces included with this workflow and what it does.  Click Install.
![workflow screenshot](/media/6.png)
4. Some worklows need information from you specific to your environment before running.  This workflow is asking for the PSK.  Enter a PSK of your liking.  You can also choose to skip this configuration and have it prompt later when running it if desired.
![details screenshot](/media/7.png)
5. Click Next and it will begin installing the workflow.  You should get an Installation Succeeded pop-up shortly.  Choose *Maybe later* when asked if you'd like to automate it to proceed.
![install success screenshot](/media/8.png)

### Now let's run that workflow
1. Under the Automation menu, select Workspace.
2. You should see your new Worklow installed at the top.  Click on the ellipsus/meatball menu button and select Run.
![run workflow screenshot](/media/9.png)
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
![form screenshot](/media/10.png)
4. Click Run and watch your workflow begin.  Blue boxes are "running".  Green boxes are completed successfullly.  Red boxes completed with errors.  If you have any red boxes, please raise your hand and we'll come help you figure out what happened.
![running workflow screenshot](/media/11.png)
5. You can view the results of workflows previously ran under the *Run Monitoring* menu option as well.

Verify under the Copenhagen network that the wireless settings are configured successfully.

___
## Create a workflow 
### Remote Targets
Remote Targets is a virtual appliance that enables your workflows to communicate with resources inside your network that do not have access to the internet. Because many user-deployed devices are not exposed to the internet, Remote Targets bridges the gap between those devices and the cloud so that they can be incorporated into your workflows. [Link to docs](https://documentation.meraki.com/Platform_Management/Workflows/Targets/Automation_Remote)

You have access to a shared Organization called *zzCLEMEA Bighorn* that includes a remote server already deployed in an on-premises lab. Within this Organization, there is also a newly configured target called Linux Host (a Unix/Linux endpoint). Access to this target is made through the remote server.  
  
You are welcome to review the configuration, but **please do not make any changes**-this is a shared environment, and modifications could disrupt the lab for other users.  
  
In this section, you will create a workflow to run commands (such as ping) on the Linux Host. **When naming your workflow, please use a unique name to avoid conflicts with others.**

Now we're ready to get started and build a workflow from a blank canvas!
### Create a workflow from scratch
> ⭐⭐ $${\color{orange}Remember}$$ $${\color{orange}to}$$ $${\color{orange}switch}$$ $${\color{orange}to}$$ $${\color{orange}the}$$ **$${\color{green}zzCLEMEA}$$ $${\color{green}Bighorn}$$** $${\color{orange}Organization}$$  ⭐⭐
1. Under the Automation menu, select Workspace.
2. On the top right, select the blue *+ Create* button.
![create workflow screenshot](/media/12.png)
3. The intent of the workflow is to make a Blank Custom Workflow.  We'll talk about automation rules another time.
![blank workflow screenshot](/media/13.png)
4. Name your workflow: Pod*X* - Ping *Y* [X is your pod number and Y is your favorite football player]
![name screenshot](/media/14.png)
5. You now have a blank workflow canvas ready for you to begin creating.  On the right side Workflow Properties section, click on the General drop down.  Add a Category of "Cisco Live Lab".
![workflow category screenshot](/media/15.png)
6. Scroll down to the Target section and select *Execute on this target*.  Choose *Unix/Linux Endpoint* for the Target Type and *Linux Host* as the Target.  This is the target referenced earlier.  Now your workflow is prepared for activities.  
![workflow target screenshot](/media/16.png)
7. On the left side in the Activities column, type *linux* in the search bar.  You should see activities associated with a linux servers.  We are going to use the activity *Execute Linux/Unix SSH Command. 
![activity linux screenshot](/media/17.png)
8. Drag the box from the Activities column into the center workflow canvas area.  You now have an activity designed to run an SSH command on a Linux host.  Note that the properties menu on the right has changed from Workflow properties to the Activity properties you selected.
![linux properties screenshot](/media/18.png)
9. We will be changing the name of the activity and the Input Command.  Let's test our VM host to see if it's up and running.  I'm going to test by pinging the server.  Since pings on linux servers don't have a predetermined count, we will add the count to ensure that the command is successfully completed.  Under the Unix/Linux section, enter the Input Command of *ping 192.168.10.15 -c5*
![command screenshot](/media/19.png)
10. Scroll up and change the Display name to the same command you put in the input field to help understand what the activity is.  Finally click the workflow canvas area and notice that the yellow warnings are gone.
11. Your workflow is ready to be validated and run now that the warnings are gone.  Click the Validate and Run buttons to see if it worked.  The activity should have a green bar at the top indicating a successful run and the workflow will have $${\color{green}SUCCESS}$$ next to it.  If it's $${\color{red}FAILED}$$, please raise your hand and we'll help you troubleshoot what went wrong.
12. Success or fail, click on the activity to see the results.  This will help us see what is happening and how we can fix it.  On the right column, scroll down until you see the results of the activity.  The Output is displayed nicely in a readable format as well as a JSON format. Note the Response body section.  It will have the results of your command.
![results screenshot](/media/20.png)
13. Now that we know what the results are, let's use them.  We can use them in a following activity and in this case, we're going to assign them to an Output variable that we can use outside this workflow.  Let's get back into your workflow.  Click the *Modify* button in the top right to bring us back into the workflow editor.
14. On the Workflow Properties, scroll down to the Variables Section and create a new variable.
15. Name the variable Results and change the scope to Output.  Click Save.
![result varialbe screenshot](/media/21.png)
16. We are now going to use an activity to assign the results of the ping action into the variable we just created.  On the Activities column search for *variable*.  Grab the *Set Variables* activity and drag it below the Ping activity.
![set variable screenshot](/media/22.png)
17. On the Set Variables properties column, add a variable to set.  First click on the *(X)* icon in the *Variable to update* box to browse for a variable.  A new window should appear with the variables available.
![vb screenshot](/media/23.png)
18. We need to use the new variable we created in the Workflow --> Output --> results.  Click Save.
![vb screenshot](/media/24.png)
19. Now we need to update it with the results of the Ping activity.  To do so, click on the *(X)* icon again under the New Value box to browse for a variable.
20. This time, we need to get the results from the Activities --> Ping 192.168.10.15 --> Response Body.  Click Save.
![vb screenshot](/media/25.png)
21. Now you are ready to Validate and Run it again.  This time, don't click on an activity to see results, but rather scroll down in the Workflow Properties and see that your Ping results are assigned to a variable called *results*

#### Congratulations!  You have successfully built a workflow from scratch and connected to a remote host to run linux commands!

___
## Bonus Content 
### Run your automation from AI!
Now comes the fun part!  We can trigger workflow automations from many different sources.  Let's try it from the AI Assistant.  
+ Open up the AI Assistant
+ Type the command:  via automation, pod [X] ping [Y] (where *X* is your pod number and *Y* is your favorite football player)  If this wasn't a shared resource you could use the command ping mbappe via automation and it would work but we should have a lot of these workflows similarly named.
+ Confirm that it selected your workflow correctly.
+ Watch the AI assistant run your workflow.  Upon successful completion, the workflow results variable will be displayed and will be available for evaluation and manipulation.
+ Try typing the command summarize the results of the ping in a table.

 
