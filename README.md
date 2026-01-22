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
If you are prompted for 2FA, please raise your hand.
> [!NOTE]
>  ⭐⭐ Your user should have access to two organizations.
>  Please ensure you are using the **DEVWKS-1314 Pod*X*** organization and **NOT the zzCLEMEA Bighorn** organization.
>  If you don't see the **DEVWKS-1314 Pod*X*** org, please raise your hand.

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
> ⭐⭐ Remember to use the **$${\color{green}DEVWKS-1314}$$ $${\color{green}Pod}$$** Organization ⭐⭐

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
   + Organization Name or ID:  DEVWKS-1314 Pod X [X is your pod number]
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

### Find the new Workflow on Github

1. Navigate to https://github.com/sorefoot/Cisco-Workflows/ and click on the [Meraki Create RF Profile](https://github.com/sorefoot/Cisco-Workflows/blob/main/MerakiCreateRFProfile__definition_workflow_02MSGUYUJMKKG2BJUI2JYQ4EBifLWskHnN2) folder.

2. This JSON file includes all of the activities configured and setup for you.  You can import the file or the raw JSON.  We're going to copy the raw JSON from the Github repo.

3. Either select all from the raw JSON or click the copy button on the top right.

[!github screenshot](/media/26.png)

<details> 
   <summary>JSON is also here:  </summary>
   
```json
{
  "workflow": {
    "unique_name": "definition_workflow_02MSGUYUJMKKG2BJUI2JYQ4EBifLWskHnN2",
    "name": "Meraki - Create RF Profile",
    "title": "Meraki - Create RF Profile",
    "type": "generic.workflow",
    "base_type": "workflow",
    "variables": [
      {
        "schema_id": "datatype.string",
        "properties": {
          "value": "",
          "scope": "input",
          "name": "Network Name",
          "type": "datatype.string",
          "is_required": true,
          "display_on_wizard": false,
          "is_invisible": false,
          "variable_string_format": "text"
        },
        "unique_name": "variable_workflow_02MSGUYVPN67B25aW3f4XDLZMayHEs3SLTU",
        "object_type": "variable_workflow"
      },
      {
        "schema_id": "datatype.string",
        "properties": {
          "value": "",
          "scope": "input",
          "name": "Org Name/ID",
          "type": "datatype.string",
          "is_required": true,
          "display_on_wizard": true,
          "is_invisible": false,
          "variable_string_format": "text"
        },
        "unique_name": "variable_workflow_02MSGUYVPFZ2J4oWU4Edqs8qSG3TIidS4EA",
        "object_type": "variable_workflow"
      },
      {
        "schema_id": "datatype.string",
        "properties": {
          "value": "",
          "scope": "input",
          "name": "6gHz Channel Width",
          "type": "datatype.string",
          "description": "\"20\", \"40\", \"80\", \"160\", \"auto\"",
          "is_required": false,
          "display_on_wizard": false,
          "is_invisible": false,
          "variable_string_format": ""
        },
        "unique_name": "variable_workflow_02STG2XH3XB4V7VEbZacl1CiiW2K1higoCt",
        "object_type": "variable_workflow"
      },
      {
        "schema_id": "datatype.string",
        "properties": {
          "value": "",
          "scope": "input",
          "name": "RF Profile Name",
          "type": "datatype.string",
          "is_required": true,
          "display_on_wizard": false,
          "is_invisible": false,
          "variable_string_format": ""
        },
        "unique_name": "variable_workflow_02STFZLZQHP617iLOMJ1qB7tC13uCqNKRtK",
        "object_type": "variable_workflow"
      },
      {
        "schema_id": "datatype.string",
        "properties": {
          "value": "",
          "scope": "input",
          "name": "5gHz Channel Width",
          "type": "datatype.string",
          "description": "\"20\", \"40\", \"80\", \"160\", \"auto\"",
          "is_required": false,
          "display_on_wizard": false,
          "is_invisible": false,
          "variable_string_format": ""
        },
        "unique_name": "variable_workflow_02STG1W31X6QK6qNTTJLwGfSw69t7Ajwt1r",
        "object_type": "variable_workflow"
      }
    ],
    "properties": {
      "atomic": {
        "is_atomic": false
      },
      "automation_rules": {
        "type": []
      },
      "delete_workflow_instance": false,
      "display_name": "Meraki - Create RF Profile",
      "runtime_user": {
        "override_target_runtime_user": false,
        "specify_on_workflow_start": false,
        "target_default": true
      },
      "target": {
        "target_type": "meraki.endpoint",
        "target_id": "definition_target_02SRTK7QOKI315CVE4rU6G6ZJcTAuL0DbbO",
        "execute_on_workflow_target": true
      }
    },
    "object_type": "definition_workflow",
    "actions": [
      {
        "unique_name": "definition_activity_02SYAZ8PDQK5W639URel5mnAcpwGM4LqsEm",
        "name": "Meraki - Get Network By Name or ID",
        "title": "Meraki - Get Network By Name or ID",
        "type": "workflow.sub_workflow",
        "base_type": "subworkflow",
        "properties": {
          "continue_on_failure": false,
          "description": "Utility workflow to retrieve network information using either Network Name or ID with flexible search criteria including configuration template binding filters. Automatically detects input format and applies appropriate search logic.\n\n**Key Features:**\n- Search by Network Name (exact match, case-sensitive)\n- Search by Network ID (format: N_XXXXXXXXXXXXXXXXX)\n- Filter by configuration template binding status\n- Rich network details output",
          "display_name": "Meraki - Get Network By Name or ID",
          "input": {
            "variable_workflow_02LCRACABYWD40LVa27k00YndGuostARjdp": "$workflow.definition_workflow_02MSGUYUJMKKG2BJUI2JYQ4EBifLWskHnN2.input.variable_workflow_02MSGUYVPFZ2J4oWU4Edqs8qSG3TIidS4EA$",
            "variable_workflow_02LCRAQ5WICDM3PgxFwKyi19yaeu1bTpVUx": "$workflow.definition_workflow_02MSGUYUJMKKG2BJUI2JYQ4EBifLWskHnN2.input.variable_workflow_02MSGUYVPN67B25aW3f4XDLZMayHEs3SLTU$",
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
        "unique_name": "definition_activity_02STFQZKJFZCV4tW53I5DjUVCtuBCTU6JDP",
        "name": "Meraki - Get Network Wireless RF Profiles",
        "title": "Meraki - Get Network Wireless RF Profiles",
        "type": "workflow.atomic_workflow",
        "base_type": "subworkflow",
        "properties": {
          "continue_on_failure": false,
          "description": "**Cisco Meraki - Wireless - Get Network Wireless RF Profiles**\n\nRetrieve a list of RF (Radio Frequency) profiles configured within a specific network\n\n**Target:** A Meraki Endpoint using HTTPS \"api.meraki.com\" port 443 and no path.\n\n**Account Key:** Meraki User API Key. API Key can be generated from Meraki Dashboard -> User Profile -> API Access.\n\nMore information about this API: https://developer.cisco.com/meraki/api-v1/get-network-wireless-rf-profiles/",
          "display_name": "Meraki - Get Network Wireless RF Profiles",
          "input": {
            "variable_workflow_02LYIYA7ZSNZS4PQsPFGAyqYqvqxUl92rdL": "$activity.definition_activity_02SYAZ8PDQK5W639URel5mnAcpwGM4LqsEm.output.variable_workflow_02LCRLPN6EZY51pb3GRpQG7QdKWS452YyuL$",
            "variable_workflow_02LYSJ7ZFW70J5S6jm7sWh2aJfzDtG7RdGD": ""
          },
          "runtime_user": {
            "target_default": true
          },
          "skip_execution": false,
          "target": {
            "target_type": "meraki.endpoint",
            "use_workflow_target": true
          },
          "workflow_id": "definition_workflow_02LYIYA7ZSHTK5KTFu2OI2MEwvVE87Ppx5e",
          "workflow_name": "Meraki - Get Network Wireless RF Profiles"
        },
        "object_type": "definition_activity"
      },
      {
        "unique_name": "definition_activity_02MSIBT7C9SUV1Fh2Xo727YtWiMt8VAw5pk",
        "name": "Create Network Wireless RF Profile",
        "title": "Create Network Wireless RF Profile",
        "type": "workflow.atomic_workflow",
        "base_type": "subworkflow",
        "properties": {
          "continue_on_failure": false,
          "display_name": "Create Network Wireless RF Profile",
          "input": {
            "variable_workflow_02LXP1U04P8JC6qyDyJGYQMvmJifZz97ndJ": "$activity.definition_activity_02SYAZ8PDQK5W639URel5mnAcpwGM4LqsEm.output.variable_workflow_02LCRLPN6EZY51pb3GRpQG7QdKWS452YyuL$",
            "variable_workflow_02LXP1U04PA2W4PwCNBZwn878C5waREhRIk": true,
            "variable_workflow_02LXP1U04PBMG1bReDf14a3Ykp3sBOiOEMP": "{}",
            "variable_workflow_02LXP1U04PD605hShXJ8cLMKkj83PjXTxHC": "false",
            "variable_workflow_02LXP1U04PDXS1bvgvoOOTThiDC7b0fXQnD": "{\n  \"maxPower\": 30,\n  \"minPower\": 8,\n  \"minBitrate\": 12,\n  \"validAutoChannels\": [\n    1,\n    5,\n    9,\n    13,\n    17,\n    21,\n    25,\n    29,\n    33,\n    37,\n    41,\n    45,\n    49,\n    53,\n    57,\n    61,\n    65,\n    69,\n    73,\n    77,\n    81,\n    85,\n    89,\n    93,\n    97,\n    101,\n    105,\n    109,\n    113,\n    117,\n    121,\n    125,\n    129,\n    133,\n    137,\n    141,\n    145,\n    149,\n    153,\n    157,\n    161,\n    165,\n    169,\n    173,\n    177,\n    181,\n    185,\n    189,\n    193,\n    197,\n    201,\n    205,\n    209,\n    213,\n    217,\n    221,\n    225,\n    229,\n    233\n  ],\n  \"channelWidth\": \"$workflow.definition_workflow_02MSGUYUJMKKG2BJUI2JYQ4EBifLWskHnN2.input.variable_workflow_02STG2XH3XB4V7VEbZacl1CiiW2K1higoCt$\",\n  \"afcEnabled\": true,\n  \"channelPuncturing\": {\n    \"enabled\": true\n  }\n}",
            "variable_workflow_02LXP1U04PFHC08n7cI1COhRjHZJlU7ofcg": "ap",
            "variable_workflow_02LXP1U04PH0W4QVttaNe6lClb9OLkHiaOT": "{\n  \"bandOperationMode\": \"multi\",\n  \"bands\": {\n    \"enabled\": [\n      \"2.4\",\n      \"5\",\n      \"6\"\n    ]\n  }\n}",
            "variable_workflow_02LXP1U04PHSO5Q5u7UuSWH7zJGZXuOrXWL": "{\n  \"maxPower\": 30,\n  \"minPower\": 5,\n  \"minBitrate\": 11,\n  \"validAutoChannels\": [\n    1,\n    6,\n    11\n  ],\n  \"axEnabled\": true\n}",
            "variable_workflow_02LXP1U04PK402VU8Ynk9d8A3NP5roNr5mB": "{\n  \"maxPower\": 30,\n  \"minPower\": 8,\n  \"minBitrate\": 12,\n  \"validAutoChannels\": [\n    36,\n    40,\n    44,\n    48,\n    52,\n    56,\n    60,\n    64,\n    100,\n    104,\n    108,\n    112,\n    116,\n    120,\n    124,\n    128,\n    132,\n    136,\n    140,\n    144,\n    149,\n    153,\n    157,\n    161,\n    165\n  ],\n  \"channelWidth\": \"$workflow.definition_workflow_02MSGUYUJMKKG2BJUI2JYQ4EBifLWskHnN2.input.variable_workflow_02STG1W31X6QK6qNTTJLwGfSw69t7Ajwt1r$\",\n  \"channelPuncturing\": {\n    \"enabled\": false\n  }\n}",
            "variable_workflow_02LXP1U04PKVS2j6kKYUoewUxuF1uwGagqO": "{\"enabled\": true}",
            "variable_workflow_02LXP1U04PMFC5gnuqTnjM7MjrT6ZdOSKJ6": "{}",
            "variable_workflow_02LXP1U04PN741TGE6H36Cv1wcsWwShikTO": "$workflow.definition_workflow_02MSGUYUJMKKG2BJUI2JYQ4EBifLWskHnN2.input.variable_workflow_02STFZLZQHP617iLOMJ1qB7tC13uCqNKRtK$",
            "variable_workflow_02LXP1U04POQO6XIJUTZUsLKtEnGtpdXmRa": "band"
          },
          "runtime_user": {
            "target_default": true
          },
          "skip_execution": false,
          "target": {
            "target_type": "meraki.endpoint",
            "use_workflow_target": true
          },
          "workflow_id": "definition_workflow_02LXP1U04P34W5aT7szGiPDmZTMs3uLAuIs",
          "workflow_name": "Meraki - Create Network Wireless RF Profile"
        },
        "object_type": "definition_activity"
      },
      {
        "unique_name": "definition_activity_02MT3JJL0DEUP2wZTmYEuGJ6meyoQQsF5UX",
        "name": "JSONPath Query",
        "title": "JSONPath Query - RF Profile ID",
        "type": "corejava.jsonpathquery",
        "base_type": "activity",
        "properties": {
          "action_timeout": 180,
          "continue_on_failure": false,
          "display_name": "JSONPath Query - RF Profile ID",
          "input_json": "$activity.definition_activity_02MSIBT7C9SUV1Fh2Xo727YtWiMt8VAw5pk.output.variable_workflow_02LXP1U04QGIO51w6PKWSy0FyuJAiPdRdJL$",
          "jsonpath_queries": [
            {
              "jsonpath_query": "$.[?(@.name=='$workflow.definition_workflow_02MSGUYUJMKKG2BJUI2JYQ4EBifLWskHnN2.input.variable_workflow_02STFZLZQHP617iLOMJ1qB7tC13uCqNKRtK$')].id",
              "jsonpath_query_name": "rfProfileId",
              "jsonpath_query_type": "string",
              "set_default_value": false,
              "zdate_type_format": "yyyy-MM-dd'T'HH:mm:ssZ"
            }
          ],
          "skip_execution": false
        },
        "object_type": "definition_activity"
      },
      {
        "unique_name": "definition_activity_02MT4QYGWGDGM4Y7uk4rKPJmkcw8D0CThwX",
        "name": "Update Network Wireless RF Profile",
        "title": "Update Network Wireless RF Profile",
        "type": "workflow.atomic_workflow",
        "base_type": "subworkflow",
        "properties": {
          "continue_on_failure": false,
          "display_name": "Update Network Wireless RF Profile",
          "input": {
            "variable_workflow_02LYMDAF81L085XVGwQfO1NbeCUvpm1FSSI": "$activity.definition_activity_02SYAZ8PDQK5W639URel5mnAcpwGM4LqsEm.output.variable_workflow_02LCRLPN6EZY51pb3GRpQG7QdKWS452YyuL$",
            "variable_workflow_02LYMDAF81MJS2Podxezdl8sXMr81USxHsd": "$activity.definition_activity_02MT3JJL0DEUP2wZTmYEuGJ6meyoQQsF5UX.output.jsonpath_queries.rfProfileId$",
            "variable_workflow_02LYMDAF81O3C54SpaJoVsFGqyFsucXxTXN": "",
            "variable_workflow_02LYMDAF81QEO6HCjIKmGPTqtsCeP2CxSrL": "true",
            "variable_workflow_02LYMDAF81RY84nTVBlcri0WFV6kGcaVA1n": "{}",
            "variable_workflow_02LYMDAF81SQ03nOyFQgs6CIkPQQqhuwwcH": "{}",
            "variable_workflow_02LYMDAF81U9K6Y9bU3KCaD0aMY8lcQG24Y": "{}",
            "variable_workflow_02LYMDAF81VT429Mqw3ju1oUaKRy5RBxEto": "{}",
            "variable_workflow_02LYMDAF81XCO2fmomf6xZbkmC31vVkifBE": "false",
            "variable_workflow_02LYMDAF81YW86U2yMynoWTPKDQP28wPcrR": "false",
            "variable_workflow_02LYMDAF81ZO04KWWEoCQ2f3PlvJAGeYYan": "{}",
            "variable_workflow_02LYMDAF8217K2KrsOjBpdD2LSo9kdnhZeD": "{}",
            "variable_workflow_02LYMDAF822R44aptFxbKioXjM2oBa0Vdud": "",
            "variable_workflow_02LYMDAF824AO0iBJ1wuENycXYiXJKWqXay": "false",
            "variable_workflow_02LYMDAF825U837HukbfDd69L9HyvX9ds0d": "",
            "variable_workflow_02LYMDAF826M026ubeIFplpu8zPDXHdEaM0": "{}"
          },
          "runtime_user": {
            "target_default": true
          },
          "skip_execution": true,
          "target": {
            "target_type": "meraki.endpoint",
            "use_workflow_target": true
          },
          "workflow_id": "definition_workflow_02LYMDAF81BQW2i1rZIloMZHZjAJJ4h3n2G",
          "workflow_name": "Meraki - Update Network Wireless RF Profile"
        },
        "object_type": "definition_activity"
      }
    ],
    "categories": [
      "category_1BMfMXSnJMyt5Ihqi7rWJr5N8cf"
    ]
  },
  "targets": {
    "definition_target_02SRTK7QOKI315CVE4rU6G6ZJcTAuL0DbbO": {
      "unique_name": "definition_target_02SRTK7QOKI315CVE4rU6G6ZJcTAuL0DbbO",
      "name": "Meraki-DEVWKS1314-1",
      "title": "Meraki-DEVWKS1314-1",
      "type": "meraki.endpoint",
      "base_type": "target",
      "object_type": "definition_target",
      "properties": {
        "default_runtime_user_id": "definition_runtime_user_02SRTJR4FIS4W4GXKvMWaeqjnLX1mwOQlBM",
        "display_name": "Meraki-DEVWKS1314-1",
        "host": "api.meraki.com",
        "ignore_proxy": false,
        "is_https_proxy": false,
        "is_integration_target": false,
        "port": 443,
        "protocol": "https"
      }
    }
  },
  "runtime_users": {
    "definition_runtime_user_02SRTJR4FIS4W4GXKvMWaeqjnLX1mwOQlBM": {
      "unique_name": "definition_runtime_user_02SRTJR4FIS4W4GXKvMWaeqjnLX1mwOQlBM",
      "name": "Meraki API",
      "title": "Meraki API",
      "type": "runtime_user.meraki_credentials",
      "base_type": "runtime_user",
      "object_type": "definition_runtime_user",
      "properties": {
        "api_key": "*****",
        "display_name": "Meraki API"
      }
    }
  },
  "atomic_workflows": [
    "definition_workflow_02LYIYA7ZSHTK5KTFu2OI2MEwvVE87Ppx5e",
    "definition_workflow_02LXP1U04P34W5aT7szGiPDmZTMs3uLAuIs",
    "definition_workflow_02LYMDAF81BQW2i1rZIloMZHZjAJJ4h3n2G"
  ],
  "dependent_workflows": [
    "definition_workflow_02LCR4UKH38PM6zDR4Bx2b2J165gCF1mhvh",
    "definition_workflow_02LYIYA7ZSHTK5KTFu2OI2MEwvVE87Ppx5e",
    "definition_workflow_02LXP1U04P34W5aT7szGiPDmZTMs3uLAuIs",
    "definition_workflow_02LYMDAF81BQW2i1rZIloMZHZjAJJ4h3n2G"
  ]
}
```
</details>  

 ## Let's import the workflow into your Pod.

> [!IMPORTANT]
> ⭐⭐ Change your org to use the **$${\color{green}DEVWKS-1314}$$ $${\color{green}Pod}$$** Organization ⭐⭐
1.  Under the Automation menu, select Workspace to get back to your workflows.

2.  Click on the Actions button and select Import Workflow.
 
 [!import screenshot](/media/27.png)

3.  Paste the json into the window and select Import.

[!github import screenshot](/media/28.png)

4.  Once the import is successful, we'll need to edit the workflow and connect it to our environment.  Select Edit Workflow.

[! edit workflow screenshot](/media/29.png)

5.  In the workflow properties (right column), change the target to your environment.

[! target screenshot](/media/30.png)

6.  Now you can Validate and Run the workflow.

7.  You'll need to input the following values:
    +  Organization name:  DEVWKS-1314 Pod X [X is your pod number]
    +  Network name:  Copenhagen
    +  RF Profile name:  WIFI 7 RF Profile
    +  5GHz channel width:  40
    +  6GHz channel width:  auto

8.  Run your workflow and validate that the profile is created.

9.  Excelent work!  Now you can go forth and expand your new found abilities!

10. Here is a great resource after Cisco Live to learn even more:  https://cs.co/WorkflowsSelfLearning  
 
