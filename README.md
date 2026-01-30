# osticket-prereqs<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

<li><strong>MySQL:</strong> Configured and maintained the database backend for osTicket, ensuring efficient data storage and retrieval.



<li><strong>HeidiSQL:</strong> Utilized as a graphical interface to manage and interact with the MySQL database, enabling streamlined administration and query execution.


<li><strong>PHP:</strong> Implemented server-side scripting using PHP to support dynamic content generation and backend logic for osTicket's web interface.


<li><strong>PHP Manager:</strong> Employed PHP Manager within the IIS Management Console to configure and manage PHP settings for improved performance and compatibility.


<li><strong>Visual C++ Redistributable (VC Redist):</strong> Installed and configured necessary runtime components to support PHP and other IIS-related dependencies.


<li><strong>URL Rewrite Module (IIS):</strong> Applied URL rewriting and redirection rules to enhance user navigation and ensure compatibility with osTicket's routing requirements.


<h3>1. Create a resource group within azure portal</h3>
<img width="1173" height="817" alt="Screenshot 2025-12-23 085139" src="https://github.com/user-attachments/assets/bbab9dea-0752-4370-8c9d-44c6ecd58c1f" />

<h3> Next we will create a virtual machine within our azure account make sure it is in the appropriate subscription and resource group.
  
<img width="1004" height="819" alt="Screenshot 2026-01-13 081342" src="https://github.com/user-attachments/assets/efcc6fbc-7d97-4793-b588-61a3777e84f9" />
<h3>1. Now that we have created the windows virtual machine we take the public ip adress and use remote desktop to connect to it.

  
<img width="1528" height="432" alt="Screenshot 2026-01-15 090926" src="https://github.com/user-attachments/assets/6108a7ba-bd44-4bb3-8aff-bbe8522593d7" />
<img width="1366" height="544" alt="Screenshot 2026-01-15 092735" src="https://github.com/user-attachments/assets/cf9dab37-40b3-48bd-9e29-b416922dbafa" />

Next we will Install / Enable IIS in Windows WITH CGI by navigating to the control panel on our windows virtual machine this will allow us to use our virtual machine as a web sever for os-ticket.
<img width="1032" height="561" alt="Screenshot 2026-01-15 154456" src="https://github.com/user-attachments/assets/2891c3cf-ade6-4821-8bda-f5a651c4e28b" />

<img width="1321" height="572" alt="Screenshot 2026-01-15 155008" src="https://github.com/user-attachments/assets/dc9f59f3-9f8b-475b-b894-56a6c4628397" />

<img width="835" height="571" alt="Screenshot 2026-01-15 155306" src="https://github.com/user-attachments/assets/01652198-1021-4263-929d-43e00240c22b" />


Next we will install PHP manager 
<img width="1172" height="653" alt="day1" src="https://github.com/user-attachments/assets/40a0af56-b5d1-408d-98a3-ef65ef9fdcc7" />
<img width="1433" height="775" alt="day 2" src="https://github.com/user-attachments/assets/820b9b79-119a-45d8-926e-05459e509aca" />

Now we will istall URL Rewrite Module

<img width="1427" height="763" alt="day3" src="https://github.com/user-attachments/assets/5567e8c3-d65b-4950-8686-d578cc8d91c8" />

Next Create the directory PHP on the windowns virtual machines C:Drive like so.

<img width="1562" height="837" alt="day4" src="https://github.com/user-attachments/assets/782376bb-c813-4a6e-9a4c-6828b0b24284" />
<img width="1460" height="760" alt="DAY5" src="https://github.com/user-attachments/assets/a46e099d-9003-49ef-9711-36f15cabf9db" />

Now we will extract the php manager files onto the folder named PHP we created earlier on the c:drive of our windows virtual machine.

<img width="1447" height="768" alt="Day6" src="https://github.com/user-attachments/assets/59af6bfc-825f-42a0-bbb3-df07f802fd25" /> 

The following step is to install Microsoft vc++

<img width="1462" height="770" alt="day7" src="https://github.com/user-attachments/assets/74265067-733c-4223-bd97-2c9bbbfa2cdd" />

Another dependancy we need to install is MySQL server 

<img width="1507" height="792" alt="Screenshot 2026-01-29 145223" src="https://github.com/user-attachments/assets/660f5b94-1f5d-4379-bf41-30d4c274016a" />
<img width="980" height="627" alt="Screenshot 2026-01-29 145533" src="https://github.com/user-attachments/assets/3b67c008-74be-4eea-9f2c-0229659f9134" />

<img width="856" height="602" alt="Screenshot 2026-01-29 145854" src="https://github.com/user-attachments/assets/9e1da928-b1dc-4ebb-bbb0-ae388698ff0e" />

<img width="1252" height="852" alt="Screenshot 2026-01-29 150206" src="https://github.com/user-attachments/assets/dc4a570c-ea3f-4f13-a223-69d0ae2a8151" />

<h2>6. Confirm osTicket can be reached by users on LocalHost</h2>
<ol>
  <li>Test link for agents and end-users:</li>
  <ul>
    <li>Agents URL: <a href="http://localhost/osTicket/scp/login.php">http://localhost/osTicket/scp/login.php</a></li>
    <li>End Users URL: <a href="http://localhost/osTicket/">http://localhost/osTicket/</a></li>
  </ul>
</ol>

<h2>7. Clean up files that pose a security risk</h2>
<ol>
  <li>Delete: C:\inetpub\wwwroot\osTicket\setup.</li>
  <li>Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php.</li>
</ol>


