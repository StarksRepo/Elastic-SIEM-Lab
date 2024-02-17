# Elastic-SIEM-Lab
## Description
In this lab, I’ll be walking through steps on how to set up a home lab for Elastic Stack Security Information and Event Management (SIEM) using the Elastic Web Portal and a Kali Linux VM. 
That way we can learn how to generate security events on the Kali VM, set up an agent to forward data to the SIEM, query and analyze the logs in the SIEM.
## Utilities Used
* VirtualBox or VMware
* Kali Linux (basic knowledge needed.)
* Elastic SIEM
## Objectives
1. Set up a free Elastic account.
2. Install the Kali VM.
3. Configure the Elastic Agent on the Kali Linux VM to collect the logs and forward it to the SIEM.
4. Generate security events on the Kali VM.
5. Query to find the security events in the Elastic SIEM.
6. Create a Dashboard to visualize security events.
7. Create alerts for security events.

## Step 1: Set up your Elastic Account
We will need to create a free account to set up a cloud Elastic instance that we can run the SIEM on. They do offer a 14 day trail. To do that, follow these steps:

1. Sign up for the free trail Elastic Cloud account at https://cloud.elastic.co/registration
2. Once your free account is created, please log into it.
3. Click on "Create Deployment" and select "ElasticSearch" as the deployment type.
4. Choose your region and the deployment size that fits your needs and click on "Create Deployment".
5. Wait for the configuration to complete and once it is complete, click "continue".

## Step 2: Setting up the Linux VM
Now, we need to set up the Linux VM. I used Kali Linux and Oracle VirtualBox.

1. Download the Kali Linux VM from the official Kali website at https://www.kali.org/get-kali/#kali-virtual-machines.
2. Create a new VM with the Kali VM file in your preferred virtualization platform.
3. Start the VM and follow the on-screen prompts to install Kali.
4. Once the installation is complete, log in to the Kali VM using the credentials “kali” for both the username and password.

## Step 3: Setting up Agent to Collect Logs
An agent is a software program that is installed on a device to collect and send data to a centralized system for analysis and monitoring. In the context of Elastic SIEM, an agent is used to collect and forward security-related events from your endpoints to your Elastic SIEM instance.

Follow these steps to set up the agent to collect logs from your Kali VM and forward them to the Elastic SIEM.
1. In to your Elastic SIEM instance navigate to the Integrations page by: clicking on the hamburger menu bar at the top left, then selecting “Integrations” at the bottom.

<img src="https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/e2f93f43-b6ab-49e5-a3c1-d0f36b0f1fd0" width=200>

2. Search for "Elastic Defend" and click on it so that opens the integration page.

<img src="https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/e6e663b7-8ae5-4cf5-b253-a800031a1f7f" width=800>

3. Click on “Install Elastic Defend” and follow the instructions provided on the integration page to install the agent on your Kali VM.
   
<img src="https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/da520604-84e4-47c2-9849-f01ab7ee1f96" width=500>

<img src="https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/6f5b71ab-8ff8-40de-aacd-098ccb792569" width=500>

4. Paste that command into the Kali terminal.

<img src="https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/14ff02be-ebcb-4ceb-8d92-3ef3616b1374" width=400>

5. Once the agent is installed, which will take a few minutes, you’ll see a message that says “Elastic Agent has been successfully installed.” It will automatically start collecting and forwarding logs to your Elastic SIEM instance, allow a few minutes for the logs to appear in the SIEM.
   
<img src="https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/056bf322-6966-44ae-bf0b-eb63c1ce94bf">

## Step 4: Generate Security Events on the Kali VM
To verify that the agent is working correctly, we will generate some security related events on the VM. We will use Nmap to verify this, which comes preinstalled on Kali.

1. Run a scan on Kali machine by running ths command: "sudo nmap <vm-ip>".

<img src="https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/30a2a198-e15d-4ee1-9ac2-a6f95a3adbb2">

2. This scan can generate several security events, such as the detection of open ports and the identification of services running on those ports. Run a few more Nmap scans such as, “nmap -sS <ip address>”, “nmap -sT <ip address>”, “nmap -p- <ip address>” and so on..

![nmap -sS](https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/b89987c9-6db7-4c3a-b095-c9ee36d5a390)

## Step 5: Querying for Security Events in the Elastic SIEM
Now that we have forwarded data from the Kali VM to the SIEM, we can start querying and analyzing the logs in the SIEM.

1. Inside your Elastic Deployment, click on the hamburger icon at the top-left and then click on the “Logs” tab under “Observability” to view the logs from the Kali VM.

![logs](https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/74355fd4-af19-469a-97be-3460242036a2)

2. In the search bar, enter a search query to filter the logs. For example, to search for all logs related to Nmap scans, enter the query: event.action: “nmap_scan” or process.args: “sudo”.

4. Click on the “Search” button to execute the search query.

*Please be aware that it can sometimes take a while for the events to populate and show up on the SIEM, so this query might not work right away give it time if needed.*

4. The results of the search query will be displayed in the table below. You can click on the three dots next to each event to view more details.

![nmap command ran details](https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/ab259524-5379-4dc1-be1c-c010141f3987)

By generating and analyzing different types of security events in Elastic SIEM like the one above, or generating authentication failures by typing in the wrong password or attempting SSH logins with a incorrect password, you can gain a better understanding of how security incidents are detected, investigated, and responded to in the real-world.

## Step 6: Creating a Dashboard to Vizualize such Events.
You can use the visualizations and dashboards in the SIEM app to analyze the logs and identify patterns or anomalies in the data. For example, you can create a simple dashboard that shows a count of security events over time.

1. Navigate to the Elastic web portal at https://cloud.elastic.co/.
2. Click on the menu icon on the top-left, then under “Analytics,” click on “Dashboards.”

![dashboard creation](https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/9b5f56a7-525f-440c-b740-60ea2edf46a1)

3.  Click on the “Create dashboard” button on the top right to create a new dashboard.
4. Click on the “Create Visualization” button to add a new visualization to the dashboard.
5. Select “Area” or “Line” as the visualization type, depending on your preference. This will create a chart that shows the count of events over time.

![area dashboard](https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/7ef501ce-8416-4009-b22f-475ad7f7a478)

6. In the “Metrics” section of the visualization editor on the right, select “Count” as the vertical field type and “Timestamp” for the horizontal field. This will show the count of events over time.

![dashboard metrics](https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/ee5eed56-2ebb-435f-b184-f2fdd11fe93f)

7. Click on the “Save” button to save the visualization and then complete the rest of the settings.

## Final Step: Creating an Alert
Alerts are a crucial feature in a SIEM for detecting security incidents and responding to them in a timely manner. Alerts are created based on predefined rules or custom queries, and can be configured to trigger specific actions when certain conditions are met.

1. Click on the hamburger menu icon on the top-left, then under "Security", click on "Alerts".
2. Click on "Manage rules" at the top right.

![setup alerts](https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/44eb426d-372b-439d-8764-231323c9c748)

3. Click on the “Create new rule” button at the top right.
4. Under the “Define rule” section, select the “Custom query” option from the dropdown menu.
5. Under “Custom query,” set the conditions for the rule. You can use the following query to detect Nmap scan events.

![custom query](https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/311255f2-dc52-4be5-87dc-be65f8b7560d)

This query will match all events with the action “nmap_scan.” Then click “Continue.”
6. Under the “About rule” section, give your rule a name and a description (Nmap Scan Detection).
7. Set the severity level for the alert, which can help you prioritize alerts based on their importance. Keep all the other default settings under “Schedule rule” and click “Continue.”

![rule creation](https://github.com/StarksRepo/Elastic-SIEM-Lab/assets/155681117/59dc2877-ac69-4ced-8054-376879bd793e)

8.  In the “Actions” section, select the action you want to take when the rule is triggered. You can choose to send an email notification, create a Slack message, or trigger it to open a ticket in Jira.
9. Finally, click the “Create and enable rule” button and your alert is created to your liking.
Once you’ve created your alert, it will then monitor your logs for any Nmap scan events. If an Nmap scan event is detected, the alert will be triggered and your selected action will be taken.

## Conclusion
In this lab, we have set up a Elastic SIEM and a Kali VM. We have forwarded the data from the Kali VM to the SIEM using the Elastic Beats agent, also have generated security events on the Kali VM using Nmap, and queried and analyzed the logs in the SIEM using the Elastic web interface.
This home lab has provided a valuable environment for learning and practicing the skills necessary for effective security monitoring and incident response using Elastic SIEM. Thank you for taking time to check it out! 
