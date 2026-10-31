
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>


# osTicket Help Desk Deployment on Microsoft Azure

## Project Overview

This project documents the deployment and configuration of osTicket, an open-source IT service management and help desk ticketing platform, using a Microsoft Azure Virtual Machine.

The objective was to build a functional help desk environment, configure the required web server and database components, and verify that the application could be accessed through a web browser.

This project demonstrates hands-on experience with Windows administration, cloud infrastructure, web server configuration, database management, and application deployment.

## Technologies Used

- Microsoft Azure – Virtual Machines and Compute
- Windows 11 – Operating System
- Remote Desktop Protocol (RDP) – Remote Administration
- Internet Information Services (IIS) – Web Server
- PHP – Application Runtime
- MySQL – Database Management
- HeidiSQL – Database Administration
- osTicket – Help Desk Ticketing System

## Lab Environment

| Component | Configuration |
|---|---|
| Cloud Provider | Microsoft Azure |
| Virtual Machine | osticket-vm |
| Operating System | Windows 11 21H2 |
| CPU | 4 vCPUs (confirm actual configuration) |
| Web Server | IIS |
| PHP | 7.3.8 |
| Database | MySQL 5.5.62 |
| osTicket | 1.15.8 |
<img width="50%" height="50%" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/9bdfd374-d8aa-4654-b7c8-9beb7670dcb2" />


> **Environment note:** This project uses legacy software versions for educational purposes. These versions are not recommended for production deployments. A production environment should use supported operating systems and application dependencies.

## Prerequisites

- Active Microsoft Azure subscription
- Azure Resource Group
- Windows Virtual Machine
- Remote Desktop Client
- IIS with CGI enabled
- PHP installation files
- MySQL installation files
- osTicket installation package
- HeidiSQL database management software
- URL Rewrite module for IIS

---





## Step 1: Create and Configure the Azure Virtual Machine

1. Sign in to the Microsoft Azure Portal.
2. Navigate to Virtual Machines.
3. Select Create Virtual Machine.
4. Configure the following:
   - Virtual Machine Name: `osticket-vm`
   - Operating System: Windows 11
   - CPU: 4 vCPUs (verify actual VM configuration)
   - Resource Group: Select the appropriate resource group.
   - Subscription: Select your Azure subscription.
5. Configure administrator credentials.
6. Review and deploy the virtual machine.

  
<img width="50%" height="50%" alt="Screenshot 2026-01-13 081342" src="https://github.com/user-attachments/assets/efcc6fbc-7d97-4793-b588-61a3777e84f9" />

<img width="50%" height="50%" alt="Screenshot 2026-10-01 095543" src="https://github.com/user-attachments/assets/b3d3f468-9562-4e2c-a0a2-14104fddd4df" />



  
<img width="50%" height="50%" alt="Screenshot 2026-01-15 090926" src="https://github.com/user-attachments/assets/6108a7ba-bd44-4bb3-8aff-bbe8522593d7" />
<img width="50%" height="50%" alt="Screenshot 2026-01-15 092735" src="https://github.com/user-attachments/assets/cf9dab37-40b3-48bd-9e29-b416922dbafa" />

After deployment, retrieve the VM's public IP address and connect using Remote Desktop.

**Security consideration:** Restrict inbound RDP access to a trusted IP address or use Azure Bastion instead of exposing port 3389 to the entire internet.


## Step 2: Prepare the Virtual Machine

1. Connect to the VM using Remote Desktop.
2. Download the required installation packages.
3. Create a folder on the desktop named:

   `osTicket-Installation-Files`

4. Extract the installation packages into this directory.


<img width="50%" height="50%" alt="Screenshot 2026-10-01 081531" src="https://github.com/user-attachments/assets/ddf2e3b3-a16d-465c-b860-acc649651137" />


<h2>Step 3. Install and Enable IIS with CGI</h2>
## Step 3: Install IIS and Enable CGI

1. Open Control Panel.
2. Navigate to Programs > Turn Windows features on or off.
3. Enable Internet Information Services.
4. Expand World Wide Web Services.
5. Expand Application Development Features.
6. Enable CGI.
7. Apply the changes.
<img width="50%" height="50%" alt="Screenshot 2026-01-15 154456" src="https://github.com/user-attachments/assets/2891c3cf-ade6-4821-8bda-f5a651c4e28b" />

<img width="50%" height="50%" alt="Screenshot 2026-01-15 155008" src="https://github.com/user-attachments/assets/dc9f59f3-9f8b-475b-b894-56a6c4628397" />

<img width="50%" height="50%" alt="Screenshot 2026-01-15 155306" src="https://github.com/user-attachments/assets/01652198-1021-4263-929d-43e00240c22b" />


IIS provides the web server functionality required to host osTicket, while CGI enables PHP execution through IIS.

## Step 4: Install PHP Manager and URL Rewrite

1. Install PHP Manager for IIS.
2. Install the IIS URL Rewrite module.
3. Open IIS Manager and verify that the modules are available.

These components help configure PHP processing and URL rewriting within IIS.


<img width="50%" height="50%" alt="day1" src="https://github.com/user-attachments/assets/40a0af56-b5d1-408d-98a3-ef65ef9fdcc7" />
<img width="50%" height="50%" alt="day 2" src="https://github.com/user-attachments/assets/820b9b79-119a-45d8-926e-05459e509aca" />

## Step 5: Install and Configure PHP

1. Create the directory:

   `C:\PHP`

2. Extract the PHP installation package into this directory.
3. Install the required Microsoft Visual C++ Redistributable.
4. Verify that the PHP executable is available.
5. Configure PHP through PHP Manager in IIS.


<img width="50%" height="50%" alt="day3" src="https://github.com/user-attachments/assets/5567e8c3-d65b-4950-8686-d578cc8d91c8" />

<h2>Step 6: Set Up PHP.</h2>
1. Create the directory `C:\PHP`.

2. Extract `PHP 7.3.8` (`php-7.3.8-nts-Win32-VC15-x86.zip`) into the `C:\PHP` folder

3. Install **VC_redist.x86.exe**.


<img width="50%" height="50%" alt="day4" src="https://github.com/user-attachments/assets/782376bb-c813-4a6e-9a4c-6828b0b24284" />
<img width="50%" height="50%" alt="DAY5" src="https://github.com/user-attachments/assets/a46e099d-9003-49ef-9711-36f15cabf9db" />


<img width="50%" height="50%" alt="Day6" src="https://github.com/user-attachments/assets/59af6bfc-825f-42a0-bbb3-df07f802fd25" /> 


<img width="50%" height="50%" alt="day7" src="https://github.com/user-attachments/assets/74265067-733c-4223-bd97-2c9bbbfa2cdd" />



<h2> Step 7 install is MySQL server</h2>
1. Install **MySQL 5.5.62** (`mysql-5.5.62-win32.msi`) with the following configuration:

   - Choose **Typical Setup**.
    
   - Launch the **Configuration Wizard** after installation.
    
   - Select **Standard Configuration**.
    
   - Set MySQL credentials:
     
     - Username: `root`
      
     - Password: `root`

<img width="50%" height="50%" alt="Screenshot 2026-01-29 145223" src="https://github.com/user-attachments/assets/660f5b94-1f5d-4379-bf41-30d4c274016a" />
<img width="50%" height="50%" alt="Screenshot 2026-01-29 145533" src="https://github.com/user-attachments/assets/3b67c008-74be-4eea-9f2c-0229659f9134" />

<img width="50%" height="50%" alt="Screenshot 2026-01-29 145854" src="https://github.com/user-attachments/assets/9e1da928-b1dc-4ebb-bbb0-ae388698ff0e" />

<img width="50%" height="50%" alt="Screenshot 2026-01-29 150206" src="https://github.com/user-attachments/assets/dc4a570c-ea3f-4f13-a223-69d0ae2a8151" />
<h3> Step 8 </h3> . Configure IIS
1. Open IIS as an Administrator.

2. Register PHP:
 
   - Open **PHP Manager** in IIS.
   - Register `C:\PHP\php-cgi.exe`.
3. Reload IIS:
 
   - Open IIS.
   - Stop and Start the server.

<img width="50%" height="50%" alt="qwewert" src="https://github.com/user-attachments/assets/b3fd19d4-5232-4179-b777-ea198223576e" />

<img width="50%" height="50%" alt="assddd" src="https://github.com/user-attachments/assets/dfdadd3d-4001-4da8-b4b4-62f2c588fd4b" />
<img width="50%" height="50%" alt="v" src="https://github.com/user-attachments/assets/f785de48-b9dc-479c-a4fe-d6466c1bdffc" />
<img width="50%" height="50%" alt="r" src="https://github.com/user-attachments/assets/a6aba362-c9eb-43d0-be0c-b20e5c81fbe0" />
<img width="50%" height="50%" alt="Screenshot 2026-01-30 153733" src="https://github.com/user-attachments/assets/05c11e74-44f8-49f7-b29f-fdd07bd81678" />
<h2>Step 9. Install osTicket</h2>


1. Extract `osTicket v1.15.8` (`osTicket-v1.15.8.zip`) from the `osTicket-Installation-Files` folder.
2. Copy the `upload` folder to `C:\inetpub\wwwroot`.
3. Rename the folder from `upload` to `osTicket`.
4. Reload IIS.
5. In IIS:
   - Navigate to **Sites** -> **Default** -> **osTicket**.
   - On the right-hand side, click **Browse *:80**.
6. Address missing extensions:
   - Navigate to **PHP Manager** in IIS.
   - Enable the following extensions:
     - `php_imap.dll`
     - `php_intl.dll`
     - `php_opcache.dll`
<h2>Refresh the osTicket site in your browser.</h2>

<img width="50%" height="50%" alt="Screenshot 2026-01-30 161608" src="https://github.com/user-attachments/assets/cf61823d-fbd2-412f-bd94-2b2eed44bb50" />

<img width="50%" height="50%" alt="Screenshot 2026-01-30 162152" src="https://github.com/user-attachments/assets/38f91f6f-5c97-4f61-8e4a-5be20f1008e2" />

<img width="50%" height="50%" alt="Screenshot 2026-01-30 162536" src="https://github.com/user-attachments/assets/6093108e-8036-42d9-af61-b5bdfeb6610f" />

<img width="50%" height="50%" alt="Screenshot 2026-01-30 162706" src="https://github.com/user-attachments/assets/f80926f8-d2d9-40b9-b45c-f42ba8235f38" />

<img width="50%" height="50%" alt="Screenshot 2026-01-30 163758" src="https://github.com/user-attachments/assets/9b499f50-1312-4ac0-892b-ffa091256db2" />




<img width="50%" height="50%" alt="g1" src="https://github.com/user-attachments/assets/bef74b02-7ba9-440a-8266-992560ae105d" />

<img width="50%" height="50%" alt="g2" src="https://github.com/user-attachments/assets/329f504e-93cc-4bc0-9099-e283f7043179" />


<img width="50%" height="50%" alt="g3" src="https://github.com/user-attachments/assets/af5cf434-9d9a-4c55-a441-6dc92145c9c0" />

<img width="50%" height="50%" alt="g4" src="https://github.com/user-attachments/assets/cd6fe3a6-4adb-44ef-8453-6626e29c6f5f" />

<img width="50%" height="50%" alt="g6" src="https://github.com/user-attachments/assets/654f4dac-793e-412a-85a8-d2fe44c48350" />

 Now if we refresh the osTicket installation landing page we can see the changes were made.

 
<img width="50%" height="50%" alt="G7" src="https://github.com/user-attachments/assets/1707671a-9898-43e6-84d6-dce86a47d72f" />

 <h2>10. Configure osTicket</h2>
 
 
 Rename `ost-config.php`:
 
   - From: `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
   
   - To: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`
 Assign permissions to `ost-config.php`:
   - Disable inheritance -> Remove all permissions.
   - Add new permissions: `Everyone -> Full Control`.
 Continue setup in the browser:
   - Name your help desk.
   - Set a default email for receiving customer emails.

<img width="50%" height="50%" alt="back2it" src="https://github.com/user-attachments/assets/95cf7d6a-f246-492e-ab19-37dc08bc99e5" /> 


<img width="50%" height="50%" alt="ber" src="https://github.com/user-attachments/assets/1edbe768-b14b-461b-90fb-d1225a356aab" />


<img width="50%" height="50%" alt="mmm" src="https://github.com/user-attachments/assets/3c3a3652-406f-4dff-be7c-34fcd43ad421" />


<img width="50%" height="50%" alt="treee" src="https://github.com/user-attachments/assets/082c9b94-1d13-4bb4-bf49-a40b2f653d66" />


<img width="50%" height="50%" alt="nnnnnnn" src="https://github.com/user-attachments/assets/4e89a436-98ab-4bfa-ac4b-6dbe608d0672" />


<img width="50%" height="50%" alt="vvvvv" src="https://github.com/user-attachments/assets/55935644-2a21-4ee5-974a-4de9c3d35ae6" />

<h3>We gave everyone full access which is not recommended to do but for this tutorial we will give everyone full access and later set restrictions between roles,teams, etc.</h3>


<img width="50%" height="50%" alt="llllllllll" src="https://github.com/user-attachments/assets/148fac7d-3ade-4a9c-bf72-007d292dff2c" />


 
<img width="50%" height="50%" alt="bbbbbb" src="https://github.com/user-attachments/assets/c6413fdf-d929-4db3-b40e-3070d1701b1b" />

 
## Step 11: Configure the MySQL Database

1. Install and open HeidiSQL.
2. Create a new MySQL session.
3. Connect using the MySQL administrator credentials.
4. Create a database named:

   `osTicket`

5. Create a dedicated database user for the application.
6. Grant the application account the privileges required on the osTicket database.
7. Return to the osTicket installation page.
8. Enter the database connection information:
   - Database Name: osTicket
   - Database Username: Dedicated application account
   - Database Password: Securely configured password
   - Database Host: localhost
9. Select Install Now.


<img width="50%" height="50%" alt="kkkkkk" src="https://github.com/user-attachments/assets/0ee1be17-bf4a-4543-969e-fa5668e8fa7a" />


<img width="50%" height="50%" alt="fffffff" src="https://github.com/user-attachments/assets/40000d11-4b4b-4707-b811-025a57068a3e" />


<img width="50%" height="50%" alt="eeeeeeeeeeeee" src="https://github.com/user-attachments/assets/de13495b-80bb-4a43-931f-d8add5548d0a" />

<h3>Now we go back to our osTicket installation page and enter the database name, username and the password as well.</h3>

<img width="50%" height="50%" alt="cccccc" src="https://github.com/user-attachments/assets/8dca788e-35de-4361-89d6-b288f3fa66a4" />


<img width="50%" height="50%" alt="!!!!" src="https://github.com/user-attachments/assets/5321322b-f245-4dad-8a4c-c0f7bbd06a0e" />

<h3>Success! we have installed osTicket we are ready to start using our ticketing system!</h3>


<img width="50%" height="50%" alt="!!!!" src="https://github.com/user-attachments/assets/79e6c897-3c7e-40b0-b791-1d072c3f00bf" />


<h2> Confirm osTicket can be reached by users on LocalHost</h2>
<ol>
  <li>Test link for agents and end-users:</li>
  <ul>
    <li>Agents URL: <a href="http://localhost/osTicket/scp/login.php">http://localhost/osTicket/scp/login.php</a></li>
    <li>End Users URL: <a href="http://localhost/osTicket/">http://localhost/osTicket/</a></li>
  </ul>
</ol>

<img width="50%" height="50%" alt="hpn" src="https://github.com/user-attachments/assets/5b719abd-3fe6-4289-b311-b73528628bcc" />





