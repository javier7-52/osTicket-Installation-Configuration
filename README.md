<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket Installation and Configuration</h1>
A start-to-finish outline of a popular open-source help desk ticketing system.

<h2>Enviroments, Languages, and Technologies Used</h2>

- [Microsoft Azure](https://azure.microsoft.com/): Virtual Machines
- Windows 10: Operating System
- [Internet Information Services](https://www.iis.net/) (IIS): Web Server
- [PHP 8.5.5](https://www.php.net/): Scripting Language
- [MySQL 5.5.62](https://www.mysql.com/): Database Management
- [HeidiSQL](https://www.heidisql.com/): Database Client
- [osTicket](https://osticket.com/): Ticketing Software

<h2>Installation Steps</h2>

1. Server Preparation: Create an Azure VM and enable IIS with CGI support.<br>
Inside the VM, opened Control Panel -> Programs -> Turn Windows features on or off (on the left) <br>
Followed: Internet Information Services -> World Wide Web Services -> Application Development Features -> CGI and check it  (Check each box before expanding each folder)

2. PHP & Database Setup: Installed PHP 8.5.5 and MySQL 5.5.62.<br>
Configured IIS to use the PHP manager for handling script execution. 

3. osTicket Deployment: Downloaded and extracted latest [osTicket](https://osticket.com/download/) files into the web root (`c:\inetpub\wwwroot`)

4. Database Configuration: Used HeidiSQL to create a dedicated 'osTicket' database and connected the application during the browser-based setup.

<h2>Configuration Steps</h2>

##Insert an Admin Panel image here##

1. Configure Roles, Departments, and Teams<br>
Roles: Created a 'Supreme Admin' role with full permissions.<br>
Departments: Configured a 'SysAdmins' department to manage technical escalations.<br>
Teams: Set up an 'Online Banking' team to group agents from different departments for specific tasks.
https://github.com/user-attachments/assets/11eb7afa-1855-4a54-a5df-50bf0186d43f



3. User and Agent Setup<br>
Agents: Created worker profiles for 'Jean' (SysAdmins) and 'Scott' (Support).<br>
Users: Simulated customer profiles for 'Phoenix' and 'Cyclops' to test ticket creation.<br>

4. Service Level Agreements (SLA) and Help Topics<br>
SLA Plans: Established Sev-A (1 hour), Sev-B (4 hours), and Sev-C (8 hours) response windows.<br>
Help Topics: Defined categories like 'Business Critical Outage,' 'Equipment Request,' and 'Password Reset' to streamline ticket routing.<br>

<h2>Demonstration</h2>
<h3>Ticket Lifecycle Simulation</h3>
This section will demonstrate the full lifecycle of a ticket, from creation to resolution:<br>

1. Intake: A user (Phoenix) submits a Sev-A ticket regarding an 'Business Critical Outage.'
2. Assingment: An agent (Scott) observes the ticket and assings it to the 'SysAdmins' department.
3. Resolution: Agent 'Jean' updates the ticket, provides a resolution, and closes the request.

##Insert tickets being created Sscreenshots##
