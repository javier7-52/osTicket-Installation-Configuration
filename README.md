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

<h3>1. Configure Roles, Departments, and Teams</h3>
<h4>Roles: Created a 'Supreme Admin' role with full permissions.</h4>


https://github.com/user-attachments/assets/373bd3b4-3c95-4491-ac29-ab0f696fdeea


<h4>Departments: Configured a 'SysAdmins' department to manage technical escalations.</h4>


https://github.com/user-attachments/assets/f91181a2-683b-49ea-a5c0-86e3fb3565b3


<h4>Teams: Set up an 'Online Banking' team to group agents from different departments for specific tasks.</h4>


https://github.com/user-attachments/assets/11eb7afa-1855-4a54-a5df-50bf0186d43f


<h3>2. User and Agent Setup</h3>
<h4>Agents: Created worker profiles for 'Jean' (SysAdmins) and 'Scott' (Support).</h4>


https://github.com/user-attachments/assets/201626d7-e3a9-473b-b51b-1951be8e9d73


<h4>Users: Simulated customer profiles for 'Jean Grey' and 'Scott Summers' to test ticket creation.</h4>


https://github.com/user-attachments/assets/f6132dd2-de26-4f80-a08b-89c985e413b2


<h3>3. Service Level Agreements (SLA) and Help Topics</h3>
<h4>SLA Plans: Established Sev-A (1 hour), Sev-B (4 hours), and Sev-C (8 hours) response windows.</h4>

<h4>Help Topics: Defined categories like 'Business Critical Outage,' 'Equipment Request,' and 'Password Reset' to streamline ticket routing.</h4>

<h2>Demonstration</h2>
<h3>Ticket Lifecycle Simulation</h3>
This section will demonstrate the full lifecycle of a ticket, from creation to resolution:<br>

<h4>1. Intake: A user (Phoenix) submits a Sev-A ticket regarding an 'Business Critical Outage.'</h4>
<h4>2. Assingment: An agent (Scott) observes the ticket and assings it to the 'SysAdmins' department.</h4>
<h4>3. Resolution: Agent 'Jean' updates the ticket, provides a resolution, and closes the request.</h4>


