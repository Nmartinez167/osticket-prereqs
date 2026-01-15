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


<h3>Installation Steps</h3>
<ol>
  <li>Install PHP Manager</li>
  <li>Install VC Redist.</li>
  <li>Install Rewrite.</li>
  <li>Install PHP:
    <ul>
      <li>Create the directory C:\PHP.</li>
      <li>Extract PHP files into C:\PHP directory.</li><img width="1252" height="695" alt="Screenshot 2025-10-08 133129" src="https://github.com/user-attachments/assets/5971a8e7-757b-43ff-8c11-9a84b68389f7" />

      
      
      
  <li>Register PHP from within IIS.</li>
      <li>Reload IIS (Open IIS, Stop and Start the server).</li>
    </ul>
  </li>
  <li>Install mySQL:
    <ul>
      <li>Typical Setup -> Launch Configuration Wizard -> Standard Configuration -> (create_secret_password).</li>
    </ul>
  </li>
  <li>Install HeidiSQL:
  <ul>
      <li>Open HeidiSQL.</li>
      <li>Create a new session, root/secret_password.</li><img width="897" height="637" alt="Screenshot 2025-10-08 141446" src="https://github.com/user-attachments/assets/2e7f7366-e9b5-4bdd-801e-be013ded7fd2" />

  <li>Connect to the session.</li>
      <li>Create a database called "osTicket".</li><img width="1266" height="792" alt="Screenshot 2025-10-08 141643" src="https://github.com/user-attachments/assets/e008138b-ebb6-412c-9507-8a195a84c4b9" />

  </li>
</ol>

<h2>3. Install osTicket and configure it as a website running on this web server</h2>
<ol>
  <li>Install osTicket v1.15.8:</li>
  <ul>
    <li>Download osTicket.</li>
    <li>Extract and copy “upload” folder to C:\inetpub\wwwroot.</li>
    <li>Within C:\inetpub\wwwroot, rename “upload” to “osTicket”.</li>
    <li>Reload IIS (Open IIS, Stop and Start the server).</li>
  </ul>
  <li>Confirm osTicket is running through web server:</li>
  <ul>
    <li>Go to Sites -> Default -> osTicket -> “Browse *:80”.</li>
  </ul>
</ol>

<h2>4. Enable Features and assign permissions to osTicket</h2>
<ol>
  <li>Enable Extensions in PHP Manager:</li>
  <ul>
    <li>Enable: php_imap.dll</li><img width="1087" height="702" alt="Screenshot 2025-10-08 135757" src="https://github.com/user-attachments/assets/da45f163-445f-4206-9835-8f0a1c1d3f6b" />
    <li>Enable: php_intl.dll</li>
    <li>Enable: php_opcache.dll</li>
  </ul>
  <li>Rename ost-config.php:</li>
  <ul>
    <li>From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php</li>
    <li>To: C:\inetpub\wwwroot\osTicket\include\ost-config.php</li>
  </ul>
  <li>Assign Permissions: ost-config.php</li>
  <ul>
    <li>Disable inheritance -> Remove All.</li>
    <li>New Permissions -> Everyone -> All.</li>
  </ul>
</ol>

<h2>5. Complete installation by registering email and mySQL database</h2>
<ol>
  <li>Continue setting up osTicket in the browser (click Continue).</li>
  <li>Name Helpdesk.</li>
  <li>Default email (receives email from customers).</li>
  <li>MySQL Database: osTicket.</li>
  <li>MySQL Username: root.</li>
  <li>MySQL Password: (**********).</li>
  <li>Click “Install Now!”.</li>
</ol>

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


