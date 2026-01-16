# cl-devwks-1314
### Cisco Live DevNet Workshop 1314
# Automating with Cisco Workflows Introduction

## Learning Objectives
This session is designed to introduce you to Cisco Workflows and give you hands on practice.
* [Getting started and connect to lab environment](#getting-started)
* [Connect Workflows to Meraki](#connect-workflows-to-meraki)
* [Install and run a pre-built workflow](#install-and-run-your-first-workflow)
* [Build a workflow without coding](#create-a-workflow)
* [Side Quest - Use AI to run your workflow](#side-quest)
* [Github and Importing shared work](#github-sharing)

___
## Getting Started
### Lab Access
Cisco Workflows is hosted in the Meraki Dashboard.  Open a browswer and navigate to https://dashboard.meraki.com.    
You'll use the credentials assigned to you by your Lab Admin.  
The current username will be devwksuser+*[Pod #]*@proton.me  
The current password should be C1sco12345  
> [!NOTE]
>  ⭐⭐ Your user should have access to two organizations.  Please ensure you are using the **WKS-1314 Pod*X*** organization and **NOT the zzCLEMEA Bighorn** Organization.  If you don't see the **WKS-1314 Pod*X*** org, please raise your hand.

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
> [!IMPORTANT]
> ⭐⭐ Remember to use the **$${\color{green}WKS-1314}$$ $${\color{green}Pod}$$** Organization ⭐⭐

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

5. Some worklows need information from you specific to your environment before running.  This workflow is asking for the PSK.  Enter a PSK of your liking.  You can also choose to skip this configuration and have it prompt later when running it if desired.  

![details screenshot](/media/7.png)  

6. Click Next and it will begin installing the workflow.  You should get an Installation Succeeded pop-up shortly.  Choose *Maybe later* when asked if you'd like to automate it to proceed.  

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

>[!NOTE]
>You have access to a shared Organization called  **$${\color{green}zzCLEMEA}$$ $${\color{green}Bighorn}$$** that includes a remote server already deployed in an on-premises lab. Within this Organization, there is also a newly configured target called Linux Host (a Unix/Linux endpoint). Access to this target is made through the remote server.
>You are welcome to review the configuration, but **please do not make any changes**-this is a shared environment, and modifications could disrupt the lab for other users.  
  
In this section, you will create a workflow to run commands (such as ping) on the Linux Host. **When naming your workflow, please use a unique name to avoid conflicts with others.**

Now we're ready to get started and build a workflow from a blank canvas!
### Create a workflow from scratch
> [!IMPORTANT]
> ⭐⭐ Remember to switch to the **$${\color{green}zzCLEMEA}$$ $${\color{green}Bighorn}$$** Organization  ⭐⭐

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

11. Your workflow is ready to be validated and run now that the warnings are gone.  Click the Validate and Run buttons to see if it worked.  
> [!NOTE]
> The activity should have a green bar at the top indicating a successful run and the workflow will have $${\color{green}SUCCESS}$$ next to it.
> If it's $${\color{red}FAILED}$$, please raise your hand and we'll help you troubleshoot what went wrong.  

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

22. Now you are ready to Validate and Run it again.  This time, don't click on an activity to see results, but rather scroll down in the Workflow Properties and see that your Ping results are assigned to a variable called *results*

#### Congratulations!  You have successfully built a workflow from scratch and connected to a remote host to run linux commands!

___
## Side Quest 
### Run your automation from AI!
Now comes the fun part!  We can trigger workflow automations from many different sources.  Let's try it from the AI Assistant.  

+ Open up the AI Assistant

+ Type the command:  via automation, pod [X] ping [Y] (where *X* is your pod number and *Y* is your favorite football player)  If this wasn't a shared resource you could use the command ping mbappe via automation and it would work but we should have a lot of these workflows similarly named.  

+ Confirm that it selected your workflow correctly.  

+ Watch the AI assistant run your workflow.  Upon successful completion, the workflow results variable will be displayed and will be available for evaluation and manipulation.  

+ Try typing the command summarize the results of the ping in a table.

 ___
 ## Github Sharing
 ### Crowd sourcing at it's best!
 Workflows are JSON files and can be shared many ways besides the Exchange.  We will explore how easy it is to download a workflow from a shared repository and see how it got there.  

 We are going to go back to your Pod and import a workflow from a GitHub Repo.

> [!IMPORTANT]
> ⭐⭐ Change your org to use the **$${\color{green}WKS-1314}$$ $${\color{green}Pod}$$** Organization ⭐⭐
 
1. Navigate to https://github.com/sorefoot/Cisco-Workflows/ and click on the Meraki SSID Mover folder.

2. This JSON file includes all of the activities configured and setup for you.  You can import the file or the raw JSON.  We're going to copy the raw JSON from the Github repo.

3. Either select all from the raw JSON or click the copy button on the top right.

[!github screenshot](/media/26.png)

The JSON is also found here:  
    '''json
{
  "workflow": {
    "unique_name": "definition_workflow_02RARHLQNIJKC635yr3Jrwr6dvn4Rh0MuRe",
    "name": "Wireless SSID Mover",
    "title": "Wireless SSID Mover",
    "type": "generic.workflow",
    "base_type": "workflow",
    "variables": [
      {
        "schema_id": "datatype.string",
        "properties": {
          "value": "",
          "scope": "input",
          "name": "Source SSID Number",
          "type": "datatype.string",
          "is_required": false,
          "display_on_wizard": false,
          "is_invisible": false,
          "variable_string_format": ""
        },
        "unique_name": "variable_workflow_02RW1YUN3L8GO5Ig15vOrBoWcZHU1FWjbzU",
        "object_type": "variable_workflow"
      },
      {
        "schema_id": "datatype.string",
        "properties": {
          "value": "",
          "scope": "local",
          "name": "OrgID",
          "type": "datatype.string",
          "is_required": false,
          "display_on_wizard": false,
          "is_invisible": false,
          "variable_string_format": ""
        },
        "unique_name": "variable_workflow_02STCIXPIM7DK5O9t9WqvNZoq0FV58sPFWr",
        "object_type": "variable_workflow"
      },
      {
        "schema_id": "datatype.string",
        "properties": {
          "value": "",
          "scope": "input",
          "name": "Network Name",
          "type": "datatype.string",
          "is_required": false,
          "display_on_wizard": false,
          "is_invisible": false,
          "variable_string_format": ""
        },
        "unique_name": "variable_workflow_02RW1XJ5WF6IV7j9HKbGEU2S8wzKwnWvVJr",
        "object_type": "variable_workflow"
      },
      {
        "schema_id": "datatype.string",
        "properties": {
          "value": "",
          "scope": "input",
          "name": "Target SSID Number",
          "type": "datatype.string",
          "is_required": false,
          "display_on_wizard": false,
          "is_invisible": false,
          "variable_string_format": ""
        },
        "unique_name": "variable_workflow_02RW1ZB1A9J4H1M9AwUsb5UylQETQ0GIw1e",
        "object_type": "variable_workflow"
      }
    ],
    "properties": {
      "atomic": {
        "is_atomic": false
      },
      "delete_workflow_instance": false,
      "description": "This moves an SSID from one number to a new number in a Meraki network. \n\nThis is to enable the wifi7 feature of enabling BE on specific number sets.",
      "display_name": "Wireless SSID Mover",
      "runtime_user": {
        "target_default": true
      },
      "target": {
        "target_type": "meraki.endpoint",
        "target_id": "definition_target_02PE0EJ2BUTNS6dK207u9oI4wlTtnIfK18s",
        "execute_on_workflow_target": true
      }
    },
    "object_type": "definition_workflow",
    "actions": [
      {
        "unique_name": "definition_activity_02RW1WW6LFO675BcEhlUE7C192wclJ5aieB",
        "name": "Meraki - Get Network By Name or ID",
        "title": "Meraki - Get Network By Name or ID",
        "type": "workflow.sub_workflow",
        "base_type": "subworkflow",
        "properties": {
          "continue_on_failure": false,
          "description": "Utility workflow to retrieve network information using either Network Name or ID with flexible search criteria including configuration template binding filters. Automatically detects input format and applies appropriate search logic.\n\n**Key Features:**\n- Search by Network Name (exact match, case-sensitive)\n- Search by Network ID (format: N_XXXXXXXXXXXXXXXXX)\n- Filter by configuration template binding status\n- Comprehensive error handling\n- Rich network details output",
          "display_name": "Meraki - Get Network By Name or ID",
          "input": {
            "variable_workflow_02LCRACABYWD40LVa27k00YndGuostARjdp": "$workflow.definition_workflow_02RARHLQNIJKC635yr3Jrwr6dvn4Rh0MuRe.local.variable_workflow_02STCIXPIM7DK5O9t9WqvNZoq0FV58sPFWr$",
            "variable_workflow_02LCRAQ5WICDM3PgxFwKyi19yaeu1bTpVUx": "$workflow.definition_workflow_02RARHLQNIJKC635yr3Jrwr6dvn4Rh0MuRe.input.variable_workflow_02RW1XJ5WF6IV7j9HKbGEU2S8wzKwnWvVJr$",
            "variable_workflow_02LEUF5N782ES5q1O7K4p1AoMBPrkkcxi1E": false,
            "variable_workflow_02Q7QAYO3GMXK1F8eC0UiZ7xRXnHB5k71O7": ""
          },
          "runtime_user": {
            "target_default": true
          },
          "skip_execution": false,
          "target": {
            "target_type": "meraki.endpoint",
            "use_workflow_target": true
          },
          "workflow_id": "definition_workflow_02LCR4UKH38PM6zDR4Bx2b2J165gCF1mhvh",
          "workflow_name": "Meraki - Get Network By Name or ID"
        },
        "object_type": "definition_activity"
      },
      {
        "unique_name": "definition_activity_02SQV80L0AF1O660sjJlLx6rMg9DKc3HzcU",
        "name": "Meraki - Get Network Wireless SSIDv2",
        "title": "Meraki - Get Network Wireless SSIDv2",
        "type": "workflow.atomic_workflow",
        "base_type": "subworkflow",
        "properties": {
          "continue_on_failure": false,
          "description": "Return a single MR SSID",
          "display_name": "Meraki - Get Network Wireless SSIDv2",
          "input": {
            "variable_workflow_02SQUY3NJNKJR3GaaIs7zXIu1wD9sPpkHET": "$activity.definition_activity_02RW1WW6LFO675BcEhlUE7C192wclJ5aieB.output.variable_workflow_02LCRLPN6EZY51pb3GRpQG7QdKWS452YyuL$",
            "variable_workflow_02SQUY3NJP1BF1hWl45jmE1r53vZbocXuL2": "$workflow.definition_workflow_02RARHLQNIJKC635yr3Jrwr6dvn4Rh0MuRe.input.variable_workflow_02RW1YUN3L8GO5Ig15vOrBoWcZHU1FWjbzU$",
            "variable_workflow_02SQUY3NJP7I235HK6v8M4XswEHsAlTaPKO": false
          },
          "runtime_user": {
            "target_default": true
          },
          "skip_execution": false,
          "target": {
            "target_type": "meraki.endpoint",
            "use_workflow_target": true
          },
          "workflow_id": "definition_workflow_02SQUY3MZNCOL7cpGPXsAt2wpyAuGLKbr1s",
          "workflow_name": "Meraki - Get Network Wireless SSIDv2"
        },
        "object_type": "definition_activity"
      },
      {
        "unique_name": "definition_activity_02RXYKTSVB3DL2pTcvBxdHewMSwiPs5Q2sP",
        "name": "Replace String",
        "title": "Replace String",
        "type": "core.replacestring",
        "base_type": "activity",
        "properties": {
          "action_timeout": 180,
          "continue_on_failure": false,
          "description": "Replace String to ensure the data we GET can be PUT into a new network.",
          "display_name": "Replace String",
          "input_string": "$activity.definition_activity_02SQV80L0AF1O660sjJlLx6rMg9DKc3HzcU.output.variable_workflow_02SQUY3NJMI2E2C7HgJ07f811O9hYCqf8f7$",
          "replace_list": [
            {
              "replaced_string": "null",
              "replacement_string": "false"
            },
            {
              "replaced_string": "ssidAdminAccessible",
              "replacement_string": "enabled"
            },
            {
              "replaced_string": "\"name\":\"",
              "replacement_string": "\"name\":\"New -"
            },
            {
              "replaced_string": "number\":$workflow.definition_workflow_02RARHLQNIJKC635yr3Jrwr6dvn4Rh0MuRe.input.variable_workflow_02RW1YUN3L8GO5Ig15vOrBoWcZHU1FWjbzU$",
              "replacement_string": "number\":$workflow.definition_workflow_02RARHLQNIJKC635yr3Jrwr6dvn4Rh0MuRe.input.variable_workflow_02RW1ZB1A9J4H1M9AwUsb5UylQETQ0GIw1e$"
            },
            {
              "replaced_string": "\"openRoamingCertificateId\":false",
              "replacement_string": "\"openRoamingCertificateId\":NULL"
            }
          ],
          "skip_execution": false
        },
        "object_type": "definition_activity"
      },
      {
        "unique_name": "definition_activity_02RXWL3A91I4Y5MDM9uXX9z54f4uWEUolaY",
        "name": "Generic Meraki API Request",
        "title": "Bulk Update Network Wireless SSID",
        "type": "meraki.api_request",
        "base_type": "activity",
        "properties": {
          "action_timeout": 180,
          "api_body": "$activity.definition_activity_02RXYKTSVB3DL2pTcvBxdHewMSwiPs5Q2sP.output.result_string$",
          "api_method": "PUT",
          "api_url": "/api/v1/networks/$activity.definition_activity_02RW1WW6LFO675BcEhlUE7C192wclJ5aieB.output.variable_workflow_02LCRLPN6EZY51pb3GRpQG7QdKWS452YyuL$/wireless/ssids/$workflow.definition_workflow_02RARHLQNIJKC635yr3Jrwr6dvn4Rh0MuRe.input.variable_workflow_02RW1ZB1A9J4H1M9AwUsb5UylQETQ0GIw1e$",
          "continue_on_failure": false,
          "description": "Generic Meraki API Request",
          "display_name": "Bulk Update Network Wireless SSID",
          "runtime_user": {
            "target_default": true
          },
          "skip_execution": false,
          "target": {
            "use_workflow_target": true
          }
        },
        "object_type": "definition_activity"
      },
      {
        "unique_name": "definition_activity_02RXYXVMPRMPU1EPARwNTpJ4Micls5LWQUK",
        "name": "Create Prompt",
        "title": "Ready to swap?",
        "type": "task.prompt_request",
        "base_type": "activity",
        "properties": {
          "assignee_roles": [
            "admin",
            "user"
          ],
          "assignees": [
            "$workflow.definition_workflow_02RARHLQNIJKC635yr3Jrwr6dvn4Rh0MuRe.output.started_by$"
          ],
          "continue_on_failure": false,
          "description": "Create Prompt Request",
          "display_name": "Ready to swap?",
          "expiration_date": {
            "is_relative_time": true,
            "relative_time": {
              "duration": 2,
              "time_units": "mins"
            }
          },
          "form_elements": [
            {
              "allow_multiselect": false,
              "form_element": "checkbox",
              "form_label": "Are you sure you want to move this SSID?  Users will be removed",
              "form_option_label_key": ""
            }
          ],
          "prompt_body": "Please confirm  before proceeding.",
          "prompt_title": "SSID Mover - User Input",
          "skip_execution": false,
          "task_owner": "$workflow.definition_workflow_02RARHLQNIJKC635yr3Jrwr6dvn4Rh0MuRe.output.started_by$",
          "task_requestor": "$workflow.definition_workflow_02RARHLQNIJKC635yr3Jrwr6dvn4Rh0MuRe.output.started_by$",
          "wait_for_prompt_response": true
        },
        "object_type": "definition_activity"
      },
      {
        "unique_name": "definition_activity_02RXZ12LNE6Z43DmJk3daf7k92eXUIZu1f3",
        "name": "Condition Block",
        "title": "Condition Block",
        "type": "logic.if_else",
        "base_type": "activity",
        "properties": {
          "continue_on_failure": false,
          "description": "If-Else condition block",
          "display_name": "Condition Block",
          "skip_execution": false
        },
        "object_type": "definition_activity",
        "blocks": [
          {
            "unique_name": "definition_activity_02RXZ12NB3ABY0BzMptehRE62XlJzck3Kn4",
            "name": "Condition Branch",
            "title": "If Yes!",
            "type": "logic.condition_block",
            "base_type": "activity",
            "properties": {
              "condition": {
                "left_operand": "$activity.definition_activity_02RXYXVMPRMPU1EPARwNTpJ4Micls5LWQUK.output.prompt_response.Are you sure you want to move this SSID?  Users will be removed$",
                "operator": "eq",
                "right_operand": true
              },
              "continue_on_failure": false,
              "display_name": "If Yes!",
              "skip_execution": false
            },
            "object_type": "definition_activity",
            "actions": [
              {
                "unique_name": "definition_activity_02RXZ3KWNPPUN0NZcC6qjOCbxV3BqsZkAyY",
                "name": "Disable and Rename SSID",
                "title": "Disable and Rename SSID",
                "type": "workflow.atomic_workflow",
                "base_type": "subworkflow",
                "properties": {
                  "continue_on_failure": false,
                  "description": "Update the attributes of an MR SSID",
                  "display_name": "Disable and Rename SSID",
                  "input": {
                    "variable_workflow_02LLSA7EOAT0O3JsAWvXnZOfQ7oegTq3Dqt": "$activity.definition_activity_02RW1WW6LFO675BcEhlUE7C192wclJ5aieB.output.variable_workflow_02LCRLPN6EZY51pb3GRpQG7QdKWS452YyuL$",
                    "variable_workflow_02LLSA7EOAVC03lI3PHWwWLNlMOyIMUOUkV": "$workflow.definition_workflow_02RARHLQNIJKC635yr3Jrwr6dvn4Rh0MuRe.input.variable_workflow_02RW1YUN3L8GO5Ig15vOrBoWcZHU1FWjbzU$",
                    "variable_workflow_02LLSA7EOAWVK6IQBul0G7SIKq9OdeYGgjQ": "{}",
                    "variable_workflow_02LLSA7EOAYF46a34jlT8W4usQhSi3LRhn0": "",
                    "variable_workflow_02LLSA7EOB2A05HRjXgWAAfXVLFni9YMmO8": "",
                    "variable_workflow_02LLSA7EOB3TK1oGpHyqaKLXOzYcAF4FA1A": "",
                    "variable_workflow_02LLSA7EOB5D46NOmDKYidugdxqKQSzQd7V": "{}",
                    "variable_workflow_02LLSA7EOB64W0RzsxMhxbJHoCFw6g62FG2": "[]",
                    "variable_workflow_02LLSA7EOB8G8224dXPlAlrtiymHdtMkmyD": "",
                    "variable_workflow_02LLSA7EOB98016aho2yItoWGwMJSCsjZQ8": "",
                    "variable_workflow_02LLSA7EOBBJC6SROrVi9dpa3daPMAlmKUd": "",
                    "variable_workflow_02LLSA7EOBDUO0FcQLgXYXauexvXKdHHaxB": "",
                    "variable_workflow_02LLSA7EOBEMG37hbmFvxsSuqtvk2ivltu0": "[]",
                    "variable_workflow_02LLSA7EOBG6019A2hKy0n36o5MkufCiJPk": "",
                    "variable_workflow_02LLSA7EOBK0W3WrO71mZLNvsGVELTvA6Iw": "",
                    "variable_workflow_02LLSA7EOBKSO7mKcHFOJXrjQpyMIXBM7Co": "",
                    "variable_workflow_02LLSA7EOBMC83iJvJiD7gKq6K21cvzqQR9": "",
                    "variable_workflow_02LLSA7EOBRQO6mt8wC53RVEkZlWHfMYkFh": "[]",
                    "variable_workflow_02LLSA7EOBTA861h5C8mVPLddQyPytKZMqm": "",
                    "variable_workflow_02LLSA7EOBU207EZAkRCfOld4eKGA370EZK": "{}",
                    "variable_workflow_02LLSA7EOBVLK5M94CXLhfL4epG2WcRytnm": [],
                    "variable_workflow_02LLSA7EOBWDC3mFXdv3lAjbBucW5BbX4D1": "",
                    "variable_workflow_02LLSA7EOBXWW5W3C7sU1KVaOTtgVig1exX": "",
                    "variable_workflow_02LLSA7EOC1000NvWNzz0XBSMjnwq00MlzN": "{}",
                    "variable_workflow_02LLSA7EOC3BC0ambpfc4eMlTTFb73kq6a8": "",
                    "variable_workflow_02LLSA7EOC4UW1CDQq0qExg2WH5aTuR68x5": "",
                    "variable_workflow_02LLSA7EOC6EG3TLwhWPhpT3MqwwdPUkYsN": "",
                    "variable_workflow_02LLSA7EOC7Y04tWUVUwm7TOIsrAaFgdSih": "",
                    "variable_workflow_02LLSA7EOC9HK5ABX2FM96YLhtllWZDs2w6": "{}",
                    "variable_workflow_02LLSA7EOCB144d6dL38nYdLrGciVYBamfJ": "",
                    "variable_workflow_02LLSA7EOCCKO07TOCARfB5UQmT1RB4Aut7": "",
                    "variable_workflow_02LLSA7EOCHZ40R6pheLAhOrEos2wLEKzeQ": "",
                    "variable_workflow_02LLSA7EOCJIO7Ce0akC0pWWyQu8wqA280a": "",
                    "variable_workflow_02LLSA7EOCKAG5pHNBVffVzQ3IrXzlVISFv": "",
                    "variable_workflow_02LLSA7EOCLU043PS2KZuVa2gHTEEvwVXxS": "{}",
                    "variable_workflow_02LLSA7EOCMLS74g20AqowIchDa86xV8eKk": "Old - $activity.definition_activity_02SQV80L0AF1O660sjJlLx6rMg9DKc3HzcU.output.variable_workflow_02SQUY3NJJG092qZfY2hgsF4glMONMBAzLq$",
                    "variable_workflow_02LLSA7EOCNDK77rRBpAxEU44pWCy8kYfxh": "false",
                    "variable_workflow_02LLSA7EOCO5C41YWqj702OhSW5Vilmh7XW": "{}",
                    "variable_workflow_02LLSA7EOCPOW1MofCcXS9UMudLy7OJDGgU": [],
                    "variable_workflow_02LLSA7EOCR8G4Xvr7Puq8vbRIKNptvTfh8": "",
                    "variable_workflow_02LLSA7EOCSS01MkjhZ6w4tJ48HGUup4F0d": "",
                    "variable_workflow_02LLSA7EOCUBK0F7TaK6GTdNC0ov4i1nap3": "",
                    "variable_workflow_02LLSA7EODCU87OEHHDU8ybQ0MeAt42W20x": [],
                    "variable_workflow_02LLSA7EODEDS1vuOfcOYIyWFAa1ifCl3Ky": "",
                    "variable_workflow_02LLSA7EODFXC5Bg4qYAzxFJCtCxznNrddO": "",
                    "variable_workflow_02LLSA7EODI8O7dxmSuUUEbdSYzvypAvRgM": "{}",
                    "variable_workflow_02LLSA7EODJ0G6mvfe1VC0tNUId4ECb4hRS": "",
                    "variable_workflow_02LLSA7EODJS82plYRuPjHOAiQlddFWtndI": "",
                    "variable_workflow_02LLSA7EODM3K3wWGERJGkkSk0piU0EgAYs": "",
                    "variable_workflow_02LLSA7EODNN47fIQFLy4rAmzSDK7NaUUNw": "",
                    "variable_workflow_02LLSA7EODP6O4BPDnZnMBIA0OKrDGhGY7b": "",
                    "variable_workflow_02LLSA7EODPYG7kx2tIWni6Z8MwD6ETpGCG": "",
                    "variable_workflow_02LLSA7EODRI07PCeMcfYjRcaux3v1xC4Lz": "",
                    "variable_workflow_02LLSA7EODT1K7AjNuJayNnnJhdEdFje8BC": "",
                    "variable_workflow_02LLSA7EODTTC7jS6OAFCwPiAe2Bqu21LGQ": "{}",
                    "variable_workflow_02LLSA7EODVCW6acq3RkmNTSoqzBbv1NJKC": "",
                    "variable_workflow_02LLSA7EODW4O2tbJws7sJVypRaOJosdpMZ": "{}",
                    "variable_workflow_02LLSA7EODWWG3JuTxmsp4y0xQKKwlbmOG8": "{}",
                    "variable_workflow_02LLSA7EODXO82cJzucZWhFLcIfJwhkCFWG": "",
                    "variable_workflow_02LLY7DN7KHPG0UNDEcCBsKSesazYzkJZGJ": "",
                    "variable_workflow_02LMMSVN0Y25K4v96fIHseh7whARGUKI113": "",
                    "variable_workflow_02LMO11ZE6BUF6fNwsUk45oh3fHzd4vqKkI": ""
                  },
                  "runtime_user": {
                    "target_default": true
                  },
                  "skip_execution": false,
                  "target": {
                    "target_type": "meraki.endpoint",
                    "use_workflow_target": true
                  },
                  "workflow_id": "definition_workflow_02LLSA7EOAQPC2RykedUX9y4UVVWi5yXQQy",
                  "workflow_name": "Meraki - Update Network Wireless SSID"
                },
                "object_type": "definition_activity"
              },
              {
                "unique_name": "definition_activity_02RXZ2IKY0Y394gLVz21BuiJPhwk7raGpKv",
                "name": "Enable and Update SSID",
                "title": "Enable and Update SSID",
                "type": "workflow.atomic_workflow",
                "base_type": "subworkflow",
                "properties": {
                  "continue_on_failure": false,
                  "description": "Update the attributes of an MR SSID",
                  "display_name": "Enable and Update SSID",
                  "input": {
                    "variable_workflow_02LLSA7EOAT0O3JsAWvXnZOfQ7oegTq3Dqt": "$activity.definition_activity_02RW1WW6LFO675BcEhlUE7C192wclJ5aieB.output.variable_workflow_02LCRLPN6EZY51pb3GRpQG7QdKWS452YyuL$",
                    "variable_workflow_02LLSA7EOAVC03lI3PHWwWLNlMOyIMUOUkV": "$workflow.definition_workflow_02RARHLQNIJKC635yr3Jrwr6dvn4Rh0MuRe.input.variable_workflow_02RW1ZB1A9J4H1M9AwUsb5UylQETQ0GIw1e$",
                    "variable_workflow_02LLSA7EOAWVK6IQBul0G7SIKq9OdeYGgjQ": "{}",
                    "variable_workflow_02LLSA7EOAYF46a34jlT8W4usQhSi3LRhn0": "",
                    "variable_workflow_02LLSA7EOB2A05HRjXgWAAfXVLFni9YMmO8": "",
                    "variable_workflow_02LLSA7EOB3TK1oGpHyqaKLXOzYcAF4FA1A": "",
                    "variable_workflow_02LLSA7EOB5D46NOmDKYidugdxqKQSzQd7V": "{}",
                    "variable_workflow_02LLSA7EOB64W0RzsxMhxbJHoCFw6g62FG2": "[]",
                    "variable_workflow_02LLSA7EOB8G8224dXPlAlrtiymHdtMkmyD": "",
                    "variable_workflow_02LLSA7EOB98016aho2yItoWGwMJSCsjZQ8": "",
                    "variable_workflow_02LLSA7EOBBJC6SROrVi9dpa3daPMAlmKUd": "",
                    "variable_workflow_02LLSA7EOBDUO0FcQLgXYXauexvXKdHHaxB": "",
                    "variable_workflow_02LLSA7EOBEMG37hbmFvxsSuqtvk2ivltu0": "[]",
                    "variable_workflow_02LLSA7EOBG6019A2hKy0n36o5MkufCiJPk": "",
                    "variable_workflow_02LLSA7EOBK0W3WrO71mZLNvsGVELTvA6Iw": "",
                    "variable_workflow_02LLSA7EOBKSO7mKcHFOJXrjQpyMIXBM7Co": "",
                    "variable_workflow_02LLSA7EOBMC83iJvJiD7gKq6K21cvzqQR9": "",
                    "variable_workflow_02LLSA7EOBRQO6mt8wC53RVEkZlWHfMYkFh": "[]",
                    "variable_workflow_02LLSA7EOBTA861h5C8mVPLddQyPytKZMqm": "",
                    "variable_workflow_02LLSA7EOBU207EZAkRCfOld4eKGA370EZK": "{}",
                    "variable_workflow_02LLSA7EOBVLK5M94CXLhfL4epG2WcRytnm": [],
                    "variable_workflow_02LLSA7EOBWDC3mFXdv3lAjbBucW5BbX4D1": "",
                    "variable_workflow_02LLSA7EOBXWW5W3C7sU1KVaOTtgVig1exX": "",
                    "variable_workflow_02LLSA7EOC1000NvWNzz0XBSMjnwq00MlzN": "{}",
                    "variable_workflow_02LLSA7EOC3BC0ambpfc4eMlTTFb73kq6a8": "",
                    "variable_workflow_02LLSA7EOC4UW1CDQq0qExg2WH5aTuR68x5": "",
                    "variable_workflow_02LLSA7EOC6EG3TLwhWPhpT3MqwwdPUkYsN": "",
                    "variable_workflow_02LLSA7EOC7Y04tWUVUwm7TOIsrAaFgdSih": "",
                    "variable_workflow_02LLSA7EOC9HK5ABX2FM96YLhtllWZDs2w6": "{}",
                    "variable_workflow_02LLSA7EOCB144d6dL38nYdLrGciVYBamfJ": "",
                    "variable_workflow_02LLSA7EOCCKO07TOCARfB5UQmT1RB4Aut7": "",
                    "variable_workflow_02LLSA7EOCHZ40R6pheLAhOrEos2wLEKzeQ": "",
                    "variable_workflow_02LLSA7EOCJIO7Ce0akC0pWWyQu8wqA280a": "",
                    "variable_workflow_02LLSA7EOCKAG5pHNBVffVzQ3IrXzlVISFv": "",
                    "variable_workflow_02LLSA7EOCLU043PS2KZuVa2gHTEEvwVXxS": "{}",
                    "variable_workflow_02LLSA7EOCMLS74g20AqowIchDa86xV8eKk": "$activity.definition_activity_02SQV80L0AF1O660sjJlLx6rMg9DKc3HzcU.output.variable_workflow_02SQUY3NJJG092qZfY2hgsF4glMONMBAzLq$",
                    "variable_workflow_02LLSA7EOCNDK77rRBpAxEU44pWCy8kYfxh": "true",
                    "variable_workflow_02LLSA7EOCO5C41YWqj702OhSW5Vilmh7XW": "{}",
                    "variable_workflow_02LLSA7EOCPOW1MofCcXS9UMudLy7OJDGgU": [],
                    "variable_workflow_02LLSA7EOCR8G4Xvr7Puq8vbRIKNptvTfh8": "",
                    "variable_workflow_02LLSA7EOCSS01MkjhZ6w4tJ48HGUup4F0d": "",
                    "variable_workflow_02LLSA7EOCUBK0F7TaK6GTdNC0ov4i1nap3": "",
                    "variable_workflow_02LLSA7EODCU87OEHHDU8ybQ0MeAt42W20x": [],
                    "variable_workflow_02LLSA7EODEDS1vuOfcOYIyWFAa1ifCl3Ky": "",
                    "variable_workflow_02LLSA7EODFXC5Bg4qYAzxFJCtCxznNrddO": "",
                    "variable_workflow_02LLSA7EODI8O7dxmSuUUEbdSYzvypAvRgM": "{}",
                    "variable_workflow_02LLSA7EODJ0G6mvfe1VC0tNUId4ECb4hRS": "",
                    "variable_workflow_02LLSA7EODJS82plYRuPjHOAiQlddFWtndI": "",
                    "variable_workflow_02LLSA7EODM3K3wWGERJGkkSk0piU0EgAYs": "",
                    "variable_workflow_02LLSA7EODNN47fIQFLy4rAmzSDK7NaUUNw": "",
                    "variable_workflow_02LLSA7EODP6O4BPDnZnMBIA0OKrDGhGY7b": "",
                    "variable_workflow_02LLSA7EODPYG7kx2tIWni6Z8MwD6ETpGCG": "",
                    "variable_workflow_02LLSA7EODRI07PCeMcfYjRcaux3v1xC4Lz": "",
                    "variable_workflow_02LLSA7EODT1K7AjNuJayNnnJhdEdFje8BC": "",
                    "variable_workflow_02LLSA7EODTTC7jS6OAFCwPiAe2Bqu21LGQ": "{}",
                    "variable_workflow_02LLSA7EODVCW6acq3RkmNTSoqzBbv1NJKC": "",
                    "variable_workflow_02LLSA7EODW4O2tbJws7sJVypRaOJosdpMZ": "{}",
                    "variable_workflow_02LLSA7EODWWG3JuTxmsp4y0xQKKwlbmOG8": "{}",
                    "variable_workflow_02LLSA7EODXO82cJzucZWhFLcIfJwhkCFWG": "",
                    "variable_workflow_02LLY7DN7KHPG0UNDEcCBsKSesazYzkJZGJ": "",
                    "variable_workflow_02LMMSVN0Y25K4v96fIHseh7whARGUKI113": "",
                    "variable_workflow_02LMO11ZE6BUF6fNwsUk45oh3fHzd4vqKkI": ""
                  },
                  "runtime_user": {
                    "target_default": true
                  },
                  "skip_execution": false,
                  "target": {
                    "target_type": "meraki.endpoint",
                    "use_workflow_target": true
                  },
                  "workflow_id": "definition_workflow_02LLSA7EOAQPC2RykedUX9y4UVVWi5yXQQy",
                  "workflow_name": "Meraki - Update Network Wireless SSID"
                },
                "object_type": "definition_activity"
              }
            ]
          }
        ]
      }
    ],
    "categories": [
      "category_02LJAJ25KZEU65PJVRVM48extE20B3tMIiX"
    ]
  },
  "targets": {
    "definition_target_02PE0EJ2BUTNS6dK207u9oI4wlTtnIfK18s": {
      "unique_name": "definition_target_02PE0EJ2BUTNS6dK207u9oI4wlTtnIfK18s",
      "name": "Sorensen Villa",
      "title": "Sorensen Villa",
      "type": "meraki.endpoint",
      "base_type": "target",
      "object_type": "definition_target",
      "properties": {
        "default_runtime_user_id": "definition_runtime_user_02PE0C9DMJODS00pDJakISPAQIQJJrBTnjO",
        "display_name": "Sorensen Villa",
        "host": "api.meraki.com",
        "ignore_proxy": false,
        "is_https_proxy": false,
        "port": 443,
        "protocol": "https"
      }
    }
  },
  "runtime_users": {
    "definition_runtime_user_02PE0C9DMJODS00pDJakISPAQIQJJrBTnjO": {
      "unique_name": "definition_runtime_user_02PE0C9DMJODS00pDJakISPAQIQJJrBTnjO",
      "name": "Clint API Key",
      "title": "Clint API Key",
      "type": "runtime_user.meraki_credentials",
      "base_type": "runtime_user",
      "object_type": "definition_runtime_user",
      "properties": {
        "api_key": "*****",
        "display_name": "Clint API Key"
      }
    }
  },
  "atomic_workflows": [
    "definition_workflow_02SQUY3MZNCOL7cpGPXsAt2wpyAuGLKbr1s",
    "definition_workflow_02LLSA7EOAQPC2RykedUX9y4UVVWi5yXQQy"
  ],
  "dependent_workflows": [
    "definition_workflow_02LCR4UKH38PM6zDR4Bx2b2J165gCF1mhvh",
    "definition_workflow_02SQUY3MZNCOL7cpGPXsAt2wpyAuGLKbr1s",
    "definition_workflow_02LLSA7EOAQPC2RykedUX9y4UVVWi5yXQQy"
  ]
}
    '''

4.  
 
 
 
 
