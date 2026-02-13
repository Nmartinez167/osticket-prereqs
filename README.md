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


<h3> Create a resource group within azure portal</h3>
<ol>
  <ul>
<img width="1173" height="817" alt="Screenshot 2025-12-23 085139" src="https://github.com/user-attachments/assets/bbab9dea-0752-4370-8c9d-44c6ecd58c1f" />



<h3> Next we will create a virtual machine within our azure account make sure it is in the appropriate subscription and resource group.</h3>


  
<img width="1004" height="819" alt="Screenshot 2026-01-13 081342" src="https://github.com/user-attachments/assets/efcc6fbc-7d97-4793-b588-61a3777e84f9" />


<h3> Now that we have created the windows virtual machine we take the public ip adress and use remote desktop to connect to it.</h3>

  
<img width="1528" height="432" alt="Screenshot 2026-01-15 090926" src="https://github.com/user-attachments/assets/6108a7ba-bd44-4bb3-8aff-bbe8522593d7" />
<img width="1366" height="544" alt="Screenshot 2026-01-15 092735" src="https://github.com/user-attachments/assets/cf9dab37-40b3-48bd-9e29-b416922dbafa" />

<h3>Next we will Install / Enable IIS in Windows WITH CGI by navigating to the control panel on our windows virtual machine this will allow us to use our virtual machine as a web sever for os-ticket.</h3>
<img width="1032" height="561" alt="Screenshot 2026-01-15 154456" src="https://github.com/user-attachments/assets/2891c3cf-ade6-4821-8bda-f5a651c4e28b" />

<img width="1321" height="572" alt="Screenshot 2026-01-15 155008" src="https://github.com/user-attachments/assets/dc9f59f3-9f8b-475b-b894-56a6c4628397" />

<img width="835" height="571" alt="Screenshot 2026-01-15 155306" src="https://github.com/user-attachments/assets/01652198-1021-4263-929d-43e00240c22b" />


<h3>Next we will install PHP manager</h3>
<img width="1172" height="653" alt="day1" src="https://github.com/user-attachments/assets/40a0af56-b5d1-408d-98a3-ef65ef9fdcc7" />
<img width="1433" height="775" alt="day 2" src="https://github.com/user-attachments/assets/820b9b79-119a-45d8-926e-05459e509aca" />

<h3>Now we will install URL Rewrite Module</h3>

<img width="1427" height="763" alt="day3" src="https://github.com/user-attachments/assets/5567e8c3-d65b-4950-8686-d578cc8d91c8" />

<h3>Next Create the directory PHP on the windowns virtual machines C:Drive like so.</h3>

<img width="1562" height="837" alt="day4" src="https://github.com/user-attachments/assets/782376bb-c813-4a6e-9a4c-6828b0b24284" />
<img width="1460" height="760" alt="DAY5" src="https://github.com/user-attachments/assets/a46e099d-9003-49ef-9711-36f15cabf9db" />

<h3>Now we will extract the php manager files onto the folder named PHP we created earlier on the C:drive of our windows virtual machine.</h3>

<img width="1447" height="768" alt="Day6" src="https://github.com/user-attachments/assets/59af6bfc-825f-42a0-bbb3-df07f802fd25" /> 

<h3>The following step is to install Microsoft vc++</h3>

<img width="1462" height="770" alt="day7" src="https://github.com/user-attachments/assets/74265067-733c-4223-bd97-2c9bbbfa2cdd" />

<h3>Another dependency we need to install is MySQL server</h3>

<img width="1507" height="792" alt="Screenshot 2026-01-29 145223" src="https://github.com/user-attachments/assets/660f5b94-1f5d-4379-bf41-30d4c274016a" />
<img width="980" height="627" alt="Screenshot 2026-01-29 145533" src="https://github.com/user-attachments/assets/3b67c008-74be-4eea-9f2c-0229659f9134" />

<img width="856" height="602" alt="Screenshot 2026-01-29 145854" src="https://github.com/user-attachments/assets/9e1da928-b1dc-4ebb-bbb0-ae388698ff0e" />

<img width="1252" height="852" alt="Screenshot 2026-01-29 150206" src="https://github.com/user-attachments/assets/dc4a570c-ea3f-4f13-a223-69d0ae2a8151" />
<h3>Now that we have installed MySQL server we will open IIS as as admin on our virtual machine to register PHP Within IIS</h3>
<img width="1451" height="747" alt="qwewert" src="https://github.com/user-attachments/assets/b3fd19d4-5232-4179-b777-ea198223576e" />

<img width="1436" height="747" alt="assddd" src="https://github.com/user-attachments/assets/dfdadd3d-4001-4da8-b4b4-62f2c588fd4b" />
<img width="1032" height="482" alt="v" src="https://github.com/user-attachments/assets/f785de48-b9dc-479c-a4fe-d6466c1bdffc" />
<img width="1037" height="691" alt="r" src="https://github.com/user-attachments/assets/a6aba362-c9eb-43d0-be0c-b20e5c81fbe0" />
<img width="1028" height="637" alt="Screenshot 2026-01-30 153733" src="https://github.com/user-attachments/assets/05c11e74-44f8-49f7-b29f-fdd07bd81678" />


<h3>Now we will restart IIS (Stop and restart the web server)</h3>

<img width="1461" height="764" alt="Screenshot 2026-01-30 155432" src="https://github.com/user-attachments/assets/524fea0e-3071-47f0-8c21-8bce85829898" />

<h3>Now that we have registered PHP within IIS on our windows virtual machine we will begin installing OsTicket (Ticketing software we will be using for end users)</h3>
<img width="1033" height="752" alt="Screenshot 2026-01-30 160300" src="https://github.com/user-attachments/assets/15dad024-bcc3-4935-bd28-bf1fe7bc002b" />


<h3>Next we will take this upload folder that came with Osticket installation files and copy it into c:\inetpub\wwwroot folder</h3>

<img width="1457" height="780" alt="Screenshot 2026-01-30 161457" src="https://github.com/user-attachments/assets/93351bd1-77ad-47ca-b551-b161ab31a223" />

<img width="1442" height="751" alt="Screenshot 2026-01-30 161608" src="https://github.com/user-attachments/assets/cf61823d-fbd2-412f-bd94-2b2eed44bb50" />

<img width="1332" height="711" alt="Screenshot 2026-01-30 162152" src="https://github.com/user-attachments/assets/38f91f6f-5c97-4f61-8e4a-5be20f1008e2" />

<img width="1758" height="792" alt="Screenshot 2026-01-30 162536" src="https://github.com/user-attachments/assets/6093108e-8036-42d9-af61-b5bdfeb6610f" />

<img width="751" height="535" alt="Screenshot 2026-01-30 162706" src="https://github.com/user-attachments/assets/f80926f8-d2d9-40b9-b45c-f42ba8235f38" />


<h3>After copying the upload folder to the "wwwroot" folder we will rename it to osTicket</h3>
<img width="1362" height="721" alt="Screenshot 2026-01-30 163200" src="https://github.com/user-attachments/assets/d3152bc3-4a26-4b6e-b770-638a2e7fd360" />

<h3>Once again we will restart IIS within out Virtual Machine to actualize the few changes we made</h3> 

<img width="1442" height="751" alt="Screenshot 2026-01-30 163758" src="https://github.com/user-attachments/assets/9b499f50-1312-4ac0-892b-ffa091256db2" />

<h3>Now we navigate to the osTicket website by clicking on the tab in the IIS panel like so.</h3> 
<img width="1482" height="748" alt="g1" src="https://github.com/user-attachments/assets/bef74b02-7ba9-440a-8266-992560ae105d" />

<img width="1267" height="1015" alt="g2" src="https://github.com/user-attachments/assets/329f504e-93cc-4bc0-9099-e283f7043179" />

<h3>Notice some extensions arent activated yet so we will activate them by navigating to the PHP manager in the IIS tab under the osTicket folder to be able to use osTicket to its full potential.</h3>


<img width="1483" height="761" alt="g3" src="https://github.com/user-attachments/assets/af5cf434-9d9a-4c55-a441-6dc92145c9c0" />

<img width="1465" height="757" alt="g4" src="https://github.com/user-attachments/assets/cd6fe3a6-4adb-44ef-8453-6626e29c6f5f" />

<h3>Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll</h3>
 
<img width="1490" height="747" alt="g6" src="https://github.com/user-attachments/assets/654f4dac-793e-412a-85a8-d2fe44c48350" />

 <h3>Now if we refresh the osTicket installation landing page we can see the changes were made.</h3>

 
<img width="1215" height="892" alt="G7" src="https://github.com/user-attachments/assets/1707671a-9898-43e6-84d6-dce86a47d72f" />

 <h3>Now that we have enabled those extensions we go to in file explorer to C drive> osTicket> include> ost-sampleconfig.php and remove the "sample" from the name.</h3>


<img width="1457" height="792" alt="back2it" src="https://github.com/user-attachments/assets/95cf7d6a-f246-492e-ab19-37dc08bc99e5" /> 

<h3>Next we will enable permissions to be able to create anywhere from supreme admin users to regular employees users as well.</h3>

<img width="1368" height="913" alt="ber" src="https://github.com/user-attachments/assets/1edbe768-b14b-461b-90fb-d1225a356aab" />


<img width="1218" height="717" alt="mmm" src="https://github.com/user-attachments/assets/3c3a3652-406f-4dff-be7c-34fcd43ad421" />


<img width="1287" height="761" alt="treee" src="https://github.com/user-attachments/assets/082c9b94-1d13-4bb4-bf49-a40b2f653d66" />


<img width="1398" height="781" alt="nnnnnnn" src="https://github.com/user-attachments/assets/4e89a436-98ab-4bfa-ac4b-6dbe608d0672" />


<img width="1152" height="675" alt="vvvvv" src="https://github.com/user-attachments/assets/55935644-2a21-4ee5-974a-4de9c3d35ae6" />

<h3>We gave everyone full access which is not recommended to do but for this tutorial we will give everyone full acess and later set restrictions between roles,teams, etc.</h3>

<h3>Now we go back to the osTicket landing page and continue our installation.</h3>

<img width="1278" height="1040" alt="llllllllll" src="https://github.com/user-attachments/assets/148fac7d-3ade-4a9c-bf72-007d292dff2c" />

 <h3>Once you have filled out all the information for your helpdesk we will go back to our osTicket installation files and install Heidi Sql to be able to connect our database for osTicket</h3>

 
<img width="976" height="857" alt="bbbbbb" src="https://github.com/user-attachments/assets/c6413fdf-d929-4db3-b40e-3070d1701b1b" />


<img width="752" height="576" alt="kkkkkk" src="https://github.com/user-attachments/assets/0ee1be17-bf4a-4543-969e-fa5668e8fa7a" />

<h3>With heidi sql we will be able to make a connection between our database for osTicket.</h3>


<img width="1017" height="690" alt="fffffff" src="https://github.com/user-attachments/assets/40000d11-4b4b-4707-b811-025a57068a3e" />

<h3>Now that we created a new session we will create a new database called osTicket make sure it is spelled correctly.</h3>

<img width="1267" height="773" alt="eeeeeeeeeeeee" src="https://github.com/user-attachments/assets/de13495b-80bb-4a43-931f-d8add5548d0a" />

<h3>Now we go back to our osTicket installation page and enter the database name, username and the paswword as well.</h3>

<img width="1317" height="1018" alt="cccccc" src="https://github.com/user-attachments/assets/8dca788e-35de-4361-89d6-b288f3fa66a4" />


<img width="1332" height="997" alt="!!!!" src="https://github.com/user-attachments/assets/5321322b-f245-4dad-8a4c-c0f7bbd06a0e" />

<h3>Success! we have installed osTicket we are ready to start using our ticketing system!</h3>


<img width="1332" height="997" alt="!!!!" src="https://github.com/user-attachments/assets/79e6c897-3c7e-40b0-b791-1d072c3f00bf" />


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


