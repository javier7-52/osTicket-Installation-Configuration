<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket Installation and Configuration</h1>
A start-to-finish outline of a popular open-source help desk ticketing system.

<h2>Enviroments, Languages, and Technologies Used</h2>

- Microsoft Azure: Virtual Machines
- Windows 10: Operating System
- Internet Information Services (IIS): Web Server
- PHP: Scripting Language
- MySQL: Database Management
- [osTicket](https://osticket.com/download): Ticketing Software

<h2>Installation Steps</h2>

1. Server Preparation: Create an Azure VM and enable IIS with CGI support.<br>
After opening the VM, opened Control Panel -> Programs -> Turn Windows features on or off (on the left) <br>
Follow: Internet Information Services -> World Wide Web Services -> Application Development Features -> CGI and check it  (Check each box before expanding each folder)

2. PHP & Database Setup: Installed PHP and MySQL.<br>
Configured IIS to use the PHP manager for handling script execution. 
