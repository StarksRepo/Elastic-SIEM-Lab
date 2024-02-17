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
3. Configure the Elastic Agent on the Linux VM to collect the logs and forward it to the SIEM.
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
Now, we need to set up the Linux VM. You can use any Linux OS and virtualization software for this, but I used Kali Linux and Oracle VirtualBox.

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

3.  Click on “Install Elastic Defend” and follow the instructions provided on the integration page to install the agent on your Kali VM.
   
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

Please note that it can sometimes take a while for the events to populate and show up on the SIEM, so this query might not work right away give it time if needed.

4. The results of the search query will be displayed in the table below. You can click on the three dots next to each event to view more details.
