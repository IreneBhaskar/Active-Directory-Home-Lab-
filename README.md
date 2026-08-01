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

<p align="center"> Step 28: Ping both VMs on the Splunk machine. Connection between the VMs are now successful </p>
<p align="center"> <img src="images/imagestep28.png" height="80%" width="80%"/> </p>




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
