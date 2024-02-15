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

## Task 1: Set up your Elastic Account
We will need to create a free account to set up a cloud Elastic instance that we can run the SIEM on. They do offer a 14 day trail. To do that, follow these steps:

1. Sign up for the free trail Elastic Cloud account at https://cloud.elastic.co/registration
2. Once your free account is created, please log into it.
3. Click on "Create Deployment" and select "ElasticSearch" as the deployment type.
4. Choose your region and the deployment size that fits your needs and click on "Create Deployment".
5. Wait for the configuration to complete and once it is complete, click "continue".

## Task 2: Setting up the Linux VM
Now, we need to set up the Linux VM. You can use any Linux OS and virtualization software for this, but I used Kali Linux and Oracle VirtualBox.

1. Download the Kali Linux VM from the official Kali website at https://www.kali.org/get-kali/#kali-virtual-machines.
2. Create a new VM with the Kali VM file in your preferred virtualization platform.
3. Start the VM and follow the on-screen prompts to install Kali.
4. Once the installation is complete, log in to the Kali VM using the credentials “kali” for both the username and password.
