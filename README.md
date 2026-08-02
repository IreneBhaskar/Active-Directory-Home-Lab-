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

<p align="center">Step 29: description</p>
<p align="center"> <img src="images/imagestep29.png" height="80%" width="80%"/> </p>

<p align="center">Step 30: description</p>
<p align="center"> <img src="images/imagestep30.png" height="80%" width="80%"/> </p>

<p align="center">Step 31: description</p>
<p align="center"> <img src="images/imagestep31.png" height="80%" width="80%"/> </p>

<p align="center">Step 32: description</p>
<p align="center"> <img src="images/imagestep32.png" height="80%" width="80%"/> </p>

<p align="center">Step 33: description</p>
<p align="center"> <img src="images/imagestep33.png" height="80%" width="80%"/> </p>

<p align="center">Step 34: description</p>
<p align="center"> <img src="images/imagestep34.png" height="80%" width="80%"/> </p>

<p align="center">Step 35: description</p>
<p align="center"> <img src="images/imagestep35.png" height="80%" width="80%"/> </p>

<p align="center">Step 36: description</p>
<p align="center"> <img src="images/imagestep36.png" height="80%" width="80%"/> </p>

<p align="center">Step 37: description</p>
<p align="center"> <img src="images/imagestep37.png" height="80%" width="80%"/> </p>

<p align="center">Step 38: description</p>
<p align="center"> <img src="images/imagestep38.png" height="80%" width="80%"/> </p>

<p align="center">Step 39: description</p>
<p align="center"> <img src="images/imagestep39.png" height="80%" width="80%"/> </p>

<p align="center">Step 40: description</p>
<p align="center"> <img src="images/imagestep40.png" height="80%" width="80%"/> </p>

<p align="center">Step 41: description</p>
<p align="center"> <img src="images/imagestep41.png" height="80%" width="80%"/> </p>

<p align="center">Step 42: description</p>
<p align="center"> <img src="images/imagestep42.png" height="80%" width="80%"/> </p>

<p align="center">Step 43: description</p>
<p align="center"> <img src="images/imagestep43.png" height="80%" width="80%"/> </p>

<p align="center">Step 44: description</p>
<p align="center"> <img src="images/imagestep44.png" height="80%" width="80%"/> </p>

<p align="center">Step 45: description</p>
<p align="center"> <img src="images/imagestep45.png" height="80%" width="80%"/> </p>

<p align="center">Step 46: description</p>
<p align="center"> <img src="images/imagestep46.png" height="80%" width="80%"/> </p>

<p align="center">Step 47: description</p>
<p align="center"> <img src="images/imagestep47.png" height="80%" width="80%"/> </p>

<p align="center">Step 48: description</p>
<p align="center"> <img src="images/imagestep48.png" height="80%" width="80%"/> </p>

<p align="center">Step 49: description</p>
<p align="center"> <img src="images/imagestep49.png" height="80%" width="80%"/> </p>

<p align="center">Step 50: description</p>
<p align="center"> <img src="images/imagestep50.png" height="80%" width="80%"/> </p>

<p align="center">Step 51: description</p>
<p align="center"> <img src="images/imagestep51.png" height="80%" width="80%"/> </p>

<p align="center">Step 52: description</p>
<p align="center"> <img src="images/imagestep52.png" height="80%" width="80%"/> </p>

<p align="center">Step 53: description</p>
<p align="center"> <img src="images/imagestep53.png" height="80%" width="80%"/> </p>

<p align="center">Step 54: description</p>
<p align="center"> <img src="images/imagestep54.png" height="80%" width="80%"/> </p>




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
