# Active Directory Home Lab

## Table of Contents
- [Purpose](#purpose)
- [Utilities Used](#utilities-used)
- [Project Walkthrough](#project-walkthrough)
- [Findings](#findings)
- [Conclusion](#conclusion)

## Purpose
To set up an active directory environment and:
- Detect unauthorised logins with Splunk
- Automate responses using Shuffle (a SOAR platform)

## Utilities Used
   
**VULTR** - description
- bullet point
   
**Splunk** - description

**Shuffle** - description

**Slack** - description

## Project Walkthrough

<p align="center"> Step 1: Create a plan for the project on draw.io </p>
<p align="center"> <img src="images\imagestep1.png" height="80%" width="80%"/> </p>

<p align="center"> Step 2: Create the Domain Controller: Deploy a server on Vultr and configure its specifications </p>
<p align="center"> <img src="images\imagestep2.png" height="80%" width="80%"/> </p>

<p align="center"> Step 3: Select the Windows Standard 2022 x64 Operating System </p>
<p align="center"> <img src="images\imagestep3.png" height="80%" width="80%"/> </p>

<p align="center"> Step 4: Input server hostname and leave all other settings at its default </p>
<p align="center"> <img src="images\imagestep4.png" height="80%" width="80%"/> </p>

<p align="center"> Step 5: Create the Test Machine: Deploy another server on Vultr and configure its specifications </p>
<p align="center"> <img src="images\imagestep5.png" height="80%" width="80%"/> </p>

<p align="center"> Step 6: Input server hostname and deploy the test machine </p>
<p align="center"> <img src="images\imagestep6.png" height="80%" width="80%"/> </p>

<p align="center"> Step 7: Create the Splunk Machine: Deploy another server on Vultr and configure its specifications </p>
<p align="center"> <img src="images\imagestep7.png" height="80%" width="80%"/> </p>

<p align="center"> Step 8: Select the Ubuntu 22.04 LTS x64 Operating System </p>
<p align="center"> <img src="images\imagestep8.png" height="80%" width="80%"/> </p>

<p align="center"> Step 9: Input the server hostname and deploy the Splunk machine </p>
<p align="center"> <img src="images\imagestep9.png" height="80%" width="80%"/> </p>

<p align="center"> Step 10: All the virtual machines created can be seen in the Instances page </p>
<p align="center"> <img src="images\imagestep10.png" height="80%" width="80%"/> </p>

<p align="center"> Step 11: Add a Firewall Group (under the Network dropdown) </p>
<p align="center"> <img src="images\imagestep11.png" height="80%" width="80%"/> </p>

<p align="center"> Step 12: Add two inbound firewall rules: allow TCP port 22 (SSH) and TCP port 3389 (MS RDP) only from my public IP address. </p>
<p align="center"> <img src="images\imagestep12.png" height="80%" width="80%"/> </p>

<p align="center"> Step 13: Connect to the Domain Controller VM using Remote Desktop Connection </p>
<p align="center"> <img src="images/imagestep13.png" height="80%" width="80%"/> </p>

<p align="center"> Step 14: Log in using the credentials specified in Vultr ("administrator") </p>
<p align="center"> <img src="images/imagestep14.png" height="80%" width="80%"/> </p>

<p align="center"> Step 15: Check the domain controller VM's IP address using ipconfig in Command Prompt </p>
<p align="center"> <img src="images/imagestep15.png" height="80%" width="80%"/> </p>

<p align="center"> Step 16: Add the Firewall previously created to all the VMs to cut off access to others </p>
<p align="center"> <img src="images/imagestep16.png" height="80%" width="80%"/> </p>

<p align="center"> Step 17: Try out Vultr's console feature by opening the test machine VM </p>
<p align="center"> <img src="images/imagestep17.png" height="80%" width="80%"/> </p>

<p align="center"> Step 18: Enable VPC (virtual private cloud) on the domain controller </p>
<p align="center"> <img src="images/imagestep18.png" height="80%" width="80%"/> </p>

<p align="center"> Step 19: Enable VPC on the test machine. With a private IP, the VMs can now communicate with each other internally </p>
<p align="center"> <img src="images/imagestep19.png" height="80%" width="80%"/> </p>

<p align="center"> Step 20: Using Windows PowerShell, SSH directly into the Splunk machine using Vultr's given credentials </p>
<p align="center"> <img src="images/imagestep20.png" height="80%" width="80%"/> </p>

<p align="center"> Step 21: Check the Splunk machine's IP address using 'ip a' </p>
<p align="center"> <img src="images/imagestep21.png" height="80%" width="80%"/> </p>

<p align="center"> Step 22: Enable VPC on the Splunk machine </p>
<p align="center"> <img src="images/imagestep22.png" height="80%" width="80%"/> </p>

<p align="center"> Step 23: When pinging the other domain controller and test machine, both destination hosts are said to be unreachable </p>
<p align="center"> <img src="images/imagestep23.png" height="80%" width="80%"/> </p>

<p align="center"> Step 24: Upon inspection, it appears that the private IP and subnet mask of the VMs do not match what was shown in Vultr </p>
<p align="center"> <img src="images/imagestep24.png" height="80%" width="80%"/> </p>

<p align="center"> Step 25: Change the Test Machine's IP and Subnet Mask into its Vultr configuration </p>
<p align="center"> <img src="images/imagestep25.png" height="80%" width="80%"/> </p>

<p align="center"> Step 26: Check the Test Machine's updated IP with ipconfig </p>
<p align="center"> <img src="images/imagestep26.png" height="80%" width="80%"/> </p>

<p align="center"> Step 27: Update the Domain Controller's IP and Subnet Mask as well </p>
<p align="center"> <img src="images/imagestep27.png" height="80%" width="80%"/> </p>

<p align="center"> Step 28: Ping both VMs on the Splunk machine. Connections between the VMs are now successful </p>
<p align="center"> <img src="images/imagestep28.png" height="80%" width="80%"/> </p>

<p align="center"> Step 29: Open up the Server Manager on the Domain Controller Machine. Click 'Add roles and features' </p>
<p align="center"> <img src="images/imagestep29.png" height="80%" width="80%"/> </p>

<p align="center"> Step 30: Select 'Active Directory Domain Services' to install active directory </p>
<p align="center"> <img src="images/imagestep30.png" height="80%" width="80%"/> </p>

<p align="center"> Step 31: Click Install </p>
<p align="center"> <img src="images/imagestep31.png" height="80%" width="80%"/> </p>

<p align="center"> Step 32: Click on the warning icon and 'promote this server to a domain controller' </p>
<p align="center"> <img src="images/imagestep32.png" height="80%" width="80%"/> </p>

<p align="center"> Step 33: Select 'Add a new forest' and name the root domain </p>
<p align="center"> <img src="images/imagestep33.png" height="80%" width="80%"/> </p>

<p align="center"> Step 34: Enter a password for the domain controller </p>
<p align="center"> <img src="images/imagestep34.png" height="80%" width="80%"/> </p>

<p align="center"> Step 35: When all prerequisite checks are passed, click install </p>
<p align="center"> <img src="images/imagestep35.png" height="80%" width="80%"/> </p>

<p align="center"> Step 36: Wait for the server to restart </p>
<p align="center"> <img src="images/imagestep36.png" height="80%" width="80%"/> </p>

<p align="center"> Step 37: Create a new user </p>
<p align="center"> <img src="images/imagestep37.png" height="80%" width="80%"/> </p>

<p align="center"> Step 38: Enter the details of the new user </p>
<p align="center"> <img src="images/imagestep38.png" height="80%" width="80%"/> </p>

<p align="center"> Step 39: Enter a password for the new user </p>
<p align="center"> <img src="images/imagestep39.png" height="80%" width="80%"/> </p>

<p align="center"> Step 40: On the test machine, change its domain from Workgroup to the domain previously created </p>
<p align="center"> <img src="images/imagestep40.png" height="80%" width="80%"/> </p>

<p align="center"> Step 41: Enter the credentials of the domain controller machine </p>
<p align="center"> <img src="images/imagestep41.png" height="80%" width="80%"/> </p>

<p align="center"> Step 42: An error thrown suggests a DNS issue </p>
<p align="center"> <img src="images/imagestep42.png" height="80%" width="80%"/> </p>

<p align="center"> Step 43: Fix the DNS issue by entering the IP address of the domain controller into 'preferred DNS server' </p>
<p align="center"> <img src="images/imagestep43.png" height="80%" width="80%"/> </p>

<p align="center"> Step 44: Try changing the test machine's domain again </p>
<p align="center"> <img src="images/imagestep44.png" height="80%" width="80%"/> </p>

<p align="center"> Step 45: Enter the credentials of the domain controller </p>
<p align="center"> <img src="images/imagestep45.png" height="80%" width="80%"/> </p>

<p align="center"> Step 46: The test machine's domain is now successfully changed </p>
<p align="center"> <img src="images/imagestep46.png" height="80%" width="80%"/> </p>

<p align="center"> Step 47: After restarting the test machine, click 'Other user' and enter the credentials of the newly created user </p>
<p align="center"> <img src="images/imagestep47.png" height="80%" width="80%"/> </p>

<p align="center"> Step 48: The user log on is successfully authenticated </p>
<p align="center"> <img src="images/imagestep48.png" height="80%" width="80%"/> </p>

<p align="center"> Step 49: Try to RDP (remotely access) into the test machine by entering its public IP </p>
<p align="center"> <img src="images/imagestep49.png" height="80%" width="80%"/> </p>

<p align="center"> Step 50: An error states that remote access to the user account is unauthorised </p>
<p align="center"> <img src="images/imagestep50.png" height="80%" width="80%"/> </p>

<p align="center"> Step 51: Fix this error by heading to the remote desktop settings </p>
<p align="center"> <img src="images/imagestep51.png" height="80%" width="80%"/> </p>

<p align="center"> Step 52: Add the new user as a 'Remote Desktop User' </p>
<p align="center"> <img src="images/imagestep52.png" height="80%" width="80%"/> </p>

<p align="center">Step 53: Try to RDP into the test machine again </p>
<p align="center"> <img src="images/imagestep53.png" height="80%" width="80%"/> </p>

<p align="center"> Step 54: The new user's account can now be accessed remotely </p>
<p align="center"> <img src="images/imagestep54.png" height="80%" width="80%"/> </p>

<p align="center"> Step 55: Open PowerShell and SSH into the Splunk Machine </p>
<p align="center"> <img src="images/imagestep55.png" height="80%" width="80%"/> </p>

<p align="center"> Step 56: Update all the repositories on the Splunk machine </p>
<p align="center"> <img src="images/imagestep56.png" height="80%" width="80%"/> </p>

<p align="center"> Step 57: Download Splunk: select the .deb file under Linux </p>
<p align="center"> <img src="images/imagestep57.png" height="80%" width="80%"/> </p>

<p align="center"> Step 58: Check if the file was installed using 'ls' </p>
<p align="center"> <img src="images/imagestep58.png" height="80%" width="80%"/> </p>

<p align="center"> Step 59: Install Splunk </p>
<p align="center"> <img src="images/imagestep59.png" height="80%" width="80%"/> </p>

<p align="center"> Step 60: Navigate into the Splunk directory </p>
<p align="center"> <img src="images/imagestep60.png" height="80%" width="80%"/> </p>

<p align="center"> Step 61: Navigate into the 'bin' directory </p>
<p align="center"> <img src="images/imagestep61.png" height="80%" width="80%"/> </p>

<p align="center"> Step 62: Run the Splunk binary </p>
<p align="center"> <img src="images/imagestep62.png" height="80%" width="80%"/> </p>

<p align="center"> Step 63: Enter an administrator username and password </p>
<p align="center"> <img src="images/imagestep63.png" height="80%" width="80%"/> </p>

<p align="center"> Step 64: Add an inbound firewall rule on Vultr: allow TCP port 8000 only from my public IP address </p>
<p align="center"> <img src="images/imagestep64.png" height="80%" width="80%"/> </p>

<p align="center"> Step 65: Allow port 8000 on the Splunk machine </p>
<p align="center"> <img src="images/imagestep65.png" height="80%" width="80%"/> </p>

<p align="center"> Step 66: Visit the test machine's public IP on a web browser and enter the administrator credentials </p>
<p align="center"> <img src="images/imagestep66.png" height="80%" width="80%"/> </p>

<p align="center"> Step 67: Install the Splunk Add-on for Microsoft Windows </p>
<p align="center"> <img src="images/imagestep67.png" height="80%" width="80%"/> </p>

<p align="center"> Step 68: Create a new index on Splunk </p>
<p align="center"> <img src="images/imagestep68.png" height="80%" width="80%"/> </p>

<p align="center"> Step 69: Add a new receiving port on port 9997 </p>
<p align="center"> <img src="images/imagestep69.png" height="80%" width="80%"/> </p>

<p align="center"> Step 70: Download the Splunk Universal Forwarder for Windows </p>
<p align="center"> <img src="images/imagestep70.png" height="80%" width="80%"/> </p>

<p align="center"> Step 71: Copy the download into the test machine. Complete the Universal Forwarder Setup on the test machine </p>
<p align="center"> <img src="images/imagestep71.png" height="80%" width="80%"/> </p>

<p align="center"> Step 72: Enter in the private IP of the Splunk machine as the receiving indexer </p>
<p align="center"> <img src="images/imagestep72.png" height="80%" width="80%"/> </p>

<p align="center"> Step 73: Copy the inputs.conf file from the 'default' directory into the 'local' directory </p>
<p align="center"> <img src="images/imagestep73.png" height="80%" width="80%"/> </p>

<p align="center"> Step 74: Run Notepad as administrator and add the following into inputs.conf </p>
<p align="center"> <img src="images/imagestep74.png" height="80%" width="80%"/> </p>

<p align="center"> Step 75: Change the SplunkForwarder Properties to log on as the Local System account instead of the Splunk Forwarder account. Restart SplunkForwarder to apply the changes </p>
<p align="center"> <img src="images/imagestep75.png" height="80%" width="80%"/> </p>

<p align="center"> Step 76: Allow port 9997 on the Splunk machine </p>
<p align="center"> <img src="images/imagestep76.png" height="80%" width="80%"/> </p>

<p align="center"> Step 77: Test for telemetry in Splunk by searching up the index previously created </p>
<p align="center"> <img src="images/imagestep77.png" height="80%" width="80%"/> </p>

<p align="center"> Step 78: Repeat steps 71 - 75 on the domain controller machine </p>
<p align="center"> <img src="images/imagestep78.png" height="80%" width="80%"/> </p>

<p align="center"> Step 79: The 'host' field on Splunk now reports two values, one for the test machine and the other for the domain controller </p>
<p align="center"> <img src="images/imagestep79.png" height="80%" width="80%"/> </p>

<p align="center"> Step 80: Add the event code 4624 to the Splunk search </p>
<p align="center"> <img src="images/imagestep80.png" height="80%" width="80%"/> </p>
<p align="center"> *Event Code 4624 = An account was successfully logged on </p>

<p align="center"> Step 81: Modify query to specifically look for logon type 7 or 10 </p>
<p align="center"> <img src="images/imagestep81.png" height="80%" width="80%"/> </p>
<p align="center"> *Logon Type 7 = Unlock, ie. unattended workstation with password protected screen saver </p>
<p align="center"> *Logon Type 10 = RemoteInteractive, ie. terminal services, remote desktop, remote assistance </p>

<p align="center"> Step 82: Inspect the details of these logins (time, account name, source network address, etc...) </p>
<p align="center"> <img src="images/imagestep82.png" height="80%" width="80%"/> </p>

<p align="center"> Step 83: Modify the query to exclude events which IP addresses are not specified </p>
<p align="center"> <img src="images/imagestep83.png" height="80%" width="80%"/> </p>

<p align="center"> Step 84: Assuming that the IP address of a workplace starts with 100, exclude IP addresses that start with 100 </p>
<p align="center"> <img src="images/imagestep84.png" height="80%" width="80%"/> </p>

<p align="center"> Step 85: Create an alert that triggers with when an event occurs in this query </p>
<p align="center"> <img src="images/imagestep85.png" height="80%" width="80%"/> </p>

<p align="center"> Step 86: Check if an alert was successfully triggered </p>
<p align="center"> <img src="images/imagestep86.png" height="80%" width="80%"/> </p>



## Findings
XXX

## Conclusion
XXX

<!-- 
number_of_steps = 20  # Change this to the number of repetitions

output = ""

for i in range(1, number_of_steps + 1):
    output += f"""
<p align="center">Step {i}: description</p>
<p align="center"> <img src="images/imagestep{i}.png" height="80%" width="80%"/> </p>
"""

print(output)
-->
