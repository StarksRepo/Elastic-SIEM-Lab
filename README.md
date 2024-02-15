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
