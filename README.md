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



<h2>OVERVIEW</h2>

<li><strong>Configure Windows 10 OS to function as a web server.

<li><strong>Install required prerequisite software: MySQL, HeidiSQL, PHP, PHP Manager, Visual C++ Redistributable, and URL Rewrite.

<li><strong>Install osTicket and verify it is accessible as a website hosted on the local web server.

<li><strong>Enable necessary features and set appropriate permissions for osTicket.

<li><strong>Finalize the installation by configuring email settings and connecting to the MySQL database.

<li><strong>Verify that osTicket is accessible via localhost.

<li><strong>Remove or secure files that may present security vulnerabilities.




2. <h2>Install Required Software</h2>

<h2>Installation Steps:</h2>

<h2>-Install PHP Manager</h2>



<img width="640" height="528" alt="Screenshot 2025-10-08 132424" src="https://github.com/user-attachments/assets/f1beeb69-08de-46f3-b3ea-521d0fa15c85" />

<h2>-Install VC Redistributable</h2>



<img width="706" height="437" alt="Screenshot 2025-10-08 133400" src="https://github.com/user-attachments/assets/55f620d9-a1aa-496b-911b-95d17c2a4d2e" />

<h2>-Install URL Rewrite</h2>



<img width="675" height="532" alt="Screenshot 2025-10-08 132556" src="https://github.com/user-attachments/assets/40f10532-5db3-43e8-8840-48fe39801544" />


<h2>-Create the directory C:\PHP.</h2>



<img width="1061" height="602" alt="Screenshot 2025-10-08 132852" src="https://github.com/user-attachments/assets/3a5b8d61-3c8a-4885-adde-44ef284cad98" />

<h2>-Extract PHP files into the C:\PHP folder.</h2>



<img width="1252" height="695" alt="Screenshot 2025-10-08 133129" src="https://github.com/user-attachments/assets/8179086e-55ea-4f16-81fe-00cf4ad7ba4c" />

<h2>-Register PHP within IIS.</h2>



<img width="1311" height="722" alt="Screenshot 2025-10-08 134016" src="https://github.com/user-attachments/assets/2d77f4ba-4088-4fa6-b014-6081bb52a8e2" />

<h2>-Reload IIS (open IIS Manager, stop and start the server).</h2>

<h2>-Choose Typical Setup.</h2>

<h2>-Run the Configuration Wizard → select Standard Configuration.</h2>

<h2>-Set and remember your root password.</h2>

<h2>-Install HeidiSQL:</h2>



<img width="737" height="627" alt="Screenshot 2025-10-08 141243" src="https://github.com/user-attachments/assets/5718e6ea-1f45-418f-a38f-a568213e90da" />

<h2>-Launch HeidiSQL.</h2>

<h2>-Create a new session using credentials root/your_password.</h2>



<img width="897" height="637" alt="Screenshot 2025-10-08 141446" src="https://github.com/user-attachments/assets/7a34618e-cb3e-4649-8cc6-11b6f2a0dc87" />

<h2>-Connect to the session and create a database named osTicket.</h2>



<img width="1266" height="792" alt="Screenshot 2025-10-08 141643" src="https://github.com/user-attachments/assets/b2fc45eb-3177-445a-869b-5180b6480a48" />
-Download osTicket.

<h2>3.Install and Configure osTicket on the Web Server</h2>


-Install osTicket v1.15.8:



-Extract the upload folder and copy it to C:\inetpub\wwwroot.

-Rename the folder from upload to osTicket.

-Reload IIS (stop and start the server again).

-Verify osTicket:

-In IIS, go to Sites → Default Web Site → osTicket.

-Click “Browse *:80” to confirm the installation is accessible.

<h2>4.Enable PHP Features and Set Permissions</h2>
-In PHP Manager, enable the following extensions:

-php_imap.dll
<img width="1087" height="702" alt="Screenshot 2025-10-08 135757" src="https://github.com/user-attachments/assets/aeee9b4d-0a52-4705-8af5-9fb7f5e3d045" />

-php_int<img

-php_opcache.dll

-Rename the configuration file:

-Rename:
From C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To C:\inetpub\wwwroot\osTicket\include\ost-config.php

-Set permissions on ost-config.php:

-Disable inheritance and remove all existing permissions.

-Add new permission: Everyone → Full Control.

<h2>5.Finalize Installation in Browser</h2>
-Continue setup via browser.

-Enter helpdesk name and default support email address.

-Use the following database details:

-Database Name: osTicket

-Username: root

-Password: your_password

-Click “Install Now!”

<h2>6.Test osTicket Accessibility on Localhost</h2>
-Verify the URLs:

-Agent Login: http://localhost/osTicket/scp/login.php

-User Portal: http://localhost/osTicket/

<img width="1500" height="427" alt="Screenshot 2025-10-08 142127" src="https://github.com/user-attachments/assets/aa5956b4-5941-4027-b8c1-5ac582a2540a" />


<img width="1182" height="910" alt="Screenshot 2025-10-08 141935" src="https://github.com/user-attachments/assets/6c0edbed-7a66-451d-9f57-7e56bf1ed875" />



<h2>7. Secure Installation</h2>
-Delete the setup directory: C:\inetpub\wwwroot\osTicket\setup

-Set read-only permission on:
C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
<p>

<h2>Conclusion</h2>

Deploying osTicket on Windows 10 Web Server

Through this project, I successfully transformed a Windows 10 environment into a fully functional web server capable of hosting the osTicket helpdesk system. The setup process involved installing and configuring several essential components, including IIS (Internet Information Services), PHP, MySQL, HeidiSQL, PHP Manager, Visual C++ Redistributable, and IIS URL Rewrite Module.

Once all prerequisites were in place, I deployed osTicket, configured the database connection, and registered the necessary administrator email and credentials. Proper permissions were assigned to ensure osTicket could interact securely with system resources, and IIS features were enabled to support PHP-based web applications.

After completing the installation, I verified that osTicket was accessible locally (via localhost) and fully operational as a web-based support ticket platform. To finalize, I performed security cleanup tasks—removing installation files and sensitive setup scripts to mitigate potential vulnerabilities.

<h2>This project demonstrates my ability to</h2>

- Configure and manage a Windows-based web server environment.

- Install and integrate database-driven web applications.

- Apply security and permission management best practices.

- Troubleshoot and validate web server functionality.

- Overall, this deployment highlights my hands-on experience in system administration, web hosting, and technical support platform implementation.
