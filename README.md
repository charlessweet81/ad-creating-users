<p align="center">
<img src="https://i.imgur.com/pJSsvpx.png" alt=""/>
</p>

<h1>Creating New Active Directory Users via Powershell</h1>
<p>
This tutorial walks you through the process of setting up a Domain Controller (DC) and a Client in Microsoft Azure, showcasing how to configure network connections and test functionality in a controlled virtual environment. By deploying a Windows Server as a Domain Controller (DC-1) and a Windows 10 machine as a client (Client-1), we’ll explore how to configure private networks, assign static IPs, and test connectivity between virtual machines.

Through this step-by-step guide, you’ll gain practical experience in:

- Establishing a domain environment in Azure.
- Configuring DNS settings and testing network connectivity.
- Troubleshooting and ensuring seamless communication between virtual machines.

Let's dive in. 

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory

<h2>Operating Systems Used</h2>

- Windows Server 2022
- Windows 10

<h2>Overview</h2>

- Part I: Set up Remote Desktop for Non-Administrative Users on Client-1
  - Step 1: Log into Client-1 
  - Step 2: Open "Remote Desktop"
  - Step 3: Allow "Domain Users" Access to Remote Desktop
- Part II: Create Additional Users and Attempt Logging into Client-1
  - Step 1: Log into DC-1 
  - Step 2: Open PowerShell ISE as an Administrator
  - Step 3: Create a New File and Paste the Script
  - Step 4: Run the Script and Observe the Accounts Being Created
  - Step 5: Verify Accounts in Active Directory Users and Computers (ADUC)
  - Step 6: Attempt Logging into Client-1 with a New User

<h2>Installation Steps</h2>
<h3>Part I: Set up Remote Desktop for Non-Administrative Users on Client-1</h3>

<h4>Step 1: Log into Client-1</h4>

<img src="https://i.imgur.com/nTMpYVh.png" height="80%" width="80%" alt=""/>

- Open Remote Desktop Connection on your local machine or Azure interface.
- Enter the credentials for mydomain.com\jane_admin (e.g., username: jane_admin, password: [your password]).
- Connect to Client-1.

<h4>Step 2: Open "Remote Desktop"</h4>

<img src="https://i.imgur.com/dc07sEq.png" height="80%" width="80%" alt=""/>

- Right-click on This PC or open Control Panel > System and Security > System.
- Click Advanced system settings in the left-hand menu.
- In the System Properties window, navigate to the Remote tab.
- Check the option Allow Remote Connections to this Computer.

<h4>Step 3: Allow "Domain Users" Access to Remote Desktop</h4>

<img src="https://i.imgur.com/HfQeAYK.png" height="80%" width="80%" alt=""/>

- Click Select Users under the Remote Desktop section.
- In the pop-up, click Add.
- Type domain users, then click Check Names to verify.
- Click OK to add the group and close all open windows.

<h3>Part II: Create Additional Users and Attempt Logging into Client-1</h3> 

<h4>Step 1: Log into DC-1</h4>

<img src="https://i.imgur.com/oMLwL25.png" height="80%" width="80%" alt=""/>

Open Remote Desktop Connection and log into DC-1 using the credentials for jane_admin (e.g., username: jane_admin, password: [your password]).

<h3>Step 2: Open PowerShell ISE as an Administrator</h3>

<img src="https://i.imgur.com/7Gftgic.png" height="80%" width="80%" alt=""/>

- Search for PowerShell ISE in the Start Menu.
- Right-click and choose Run as Administrator.

<h3>Step 4: Create a New File and Paste the Script</h3>

<img src="https://i.imgur.com/MIoTOk8.png" height="80%" width="80%" alt=""/>

- Click Run Script or press F5 to execute the script. [(Here is the script)](https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1)
- Monitor the output in the PowerShell Console to confirm that user accounts are being created without errors.

<h3>Step 5: Verify Accounts in Active Directory Users and Computers (ADUC)</h3>

<img src="https://i.imgur.com/8xBM1qM.png" height="80%" width="80%" alt=""/>

- Open Active Directory Users and Computers (ADUC) on DC-1.
- Navigate to the _EMPLOYEES Organizational Unit.
- Confirm that the new user accounts created by the script appear in this OU.

<h3>Step 6: Attempt Logging into Client-1 with a New User</h3>

<img src="https://i.imgur.com/qdSNO0B.png" height="80%" width="80%" alt=""/>

- Note the default password set in the script for the new accounts.
- Use Remote Desktop to log into Client-1 with one of the new user accounts (e.g., mydomain.com\user1).
- Ensure the login is successful.

