<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>End-to-End IT Service Management (ITSM) Implementation: osTicket on Azure</h1>
I built the server, configured the business logic, and then validated the system with a live simulation.

<h2>Enviroments, Languages, and Technologies Used</h2>

- [Microsoft Azure](https://azure.microsoft.com/): Virtual Machines
- Windows 10: Operating System
- [Internet Information Services](https://www.iis.net/) (IIS): Web Server
- [PHP 8.5.5](https://www.php.net/): Scripting Language
- [MySQL 5.5.62](https://www.mysql.com/): Database Management
- [HeidiSQL](https://www.heidisql.com/): Database Client
- [osTicket](https://osticket.com/): Ticketing Software

<h2>Phase 1: Infrastructure & Enviroment Setup</h2>

<h3>1.1 Azure Virtual Network & IP Configuration<br></h3>
To ensure the help desk server maintains a consistent address for the database and web traffic, I configured a static private IP. 

- Task: Assing a static internal IP address
- Action: Navigated to **Network Settings** > **Network interface / IP configuration** > **ipconfig1** > **Allocation** > Check "Static"
- Result: VM is now anchored to (`10.0.0.4`), preventing DNS or database connection failures upon system reboots.

<details>
  
  <summary><b>Watch: Configuring Static IP in Azure</b> (Click to Expand)</summary>


  https://github.com/user-attachments/assets/43547d92-4cde-4ccc-97d7-2528f33ed6e3


</details>

<h3>1.2 Web Server (IIS) Implementation<br></h3>
I prepared the Windows enviroment to host a web application by enabling **Internet Information Services** (ISS) and the necessary gateway modules.

- Task: Install and configure the web server role.
- Action: Launched the **Turn Windows features on or off** wizard; Open _Control Panel > Programs_. Enabled **Internet Information Services** and specifically selected **CGI** under _World Wide Web Services > Application Development Features_.
- Why: CGI (Common Gateway Interface) is required to allow the IIS web server to process the PHP scripts that power osTicket.
  
<details>
  <summary><b>Watch: Enabling IIS and CGI Components</b> (Click to Expand)</summary>
  

https://github.com/user-attachments/assets/0979f044-db9b-4ecc-bd43-917c973d3f0d


</details>

<h3>1.3 PHP Environment & Scripting Support</h3>
To allow the Windows server to execute the osTicket source code, I installed the necessary PHP binaries and management tools from the project's installation media.

- Task: Register the PHP engine with the IIS Web Server.
- Action:
  1. Installed the Visual C++ Redistributable (`VC_redist.x86.exe`) to provide the necessary runtime libraries.
  2. Extracted the **PHP 7.3.8** binaries to `C:\PHP`.
  3. Extracted the **PHP Manager for IIS** (`PHPManagerForIIS_V1.5.0`) to register the `php-cgi.exe` handler.
  4. Installed the **URL Rewrite Module** (`rewrite_amd64_en-US.msi`) to ensure osTicket can handle clean permalinks and routing.
- Technical Detail: Confirmed the installation by checking the "PHP Info" page within the IIS console to verify the version and active extensions.

1.4 Database Configuration: Used HeidiSQL to create a dedicated 'osTicket' database and connected the application during the browser-based setup.

<h2>Configuration Steps</h2>

<h3>1. Configure Roles, Departments, and Teams</h3>
<h4>Roles: Created a 'Supreme Admin' role with full permissions.</h4>
<details>
  <summary><b>Watch: Role Configuration</b> (Click to Expand)</summary>

  https://github.com/user-attachments/assets/373bd3b4-3c95-4491-ac29-ab0f696fdeea

</details>

<h4>Departments: Configured a 'SysAdmins' department to manage technical escalations.</h4>
<details>
  <summary><b>Watch: Department Configuration</b> (Click to Expand)</summary>

  https://github.com/user-attachments/assets/f91181a2-683b-49ea-a5c0-86e3fb3565b3
</details>

<h4>Teams: Set up an 'Online Banking' team to group agents from different departments for specific tasks.</h4>
<details>
  <summary><b>Watch: Team Configuration</b> (Click to Expand)</summary>

  https://github.com/user-attachments/assets/11eb7afa-1855-4a54-a5df-50bf0186d43f

</details>

<h3>2. User and Agent Setup</h3>
<h4>Agents: Created worker profiles for 'Jean' (SysAdmins) and 'Scott' (Support).</h4>
<details>
  <summary><b>Watch: Worker/Agent Configuration</b> (Click to Expand)</summary>

  https://github.com/user-attachments/assets/201626d7-e3a9-473b-b51b-1951be8e9d73

</details>

<h4>Users: Simulated customer profiles for 'Jean Grey' and 'Scott Summers' to test ticket creation.</h4>
<details>
  <summary><b>Watch: Client/User Configuration</b> (Click to Expand)</summary>

  https://github.com/user-attachments/assets/f6132dd2-de26-4f80-a08b-89c985e413b2

</details>

<h3>3. Service Level Agreements (SLA) and Help Topics</h3>
<h4>SLA Plans: Established Sev-A (1 hour), Sev-B (4 hours), and Sev-C (8 hours) response windows.</h4>
<details>
  <summary><b>Watch: SLA Configuration</b> (Click to Expand)</summary>

  https://github.com/user-attachments/assets/a08616c4-59f5-436d-a006-27102bc56a1f

</details>

<h4>Help Topics: Defined categories like 'Business Critical Outage,' 'Equipment Request,' and 'Password Reset' to streamline ticket routing.</h4>
<details>
  <summary><b>Watch: Help Topic Configuration</b> (Click to Expand)</summary>

  https://github.com/user-attachments/assets/ea6f0d3d-d734-46ed-aef0-31cd81f99e29

</details>

<h2>Demonstration</h2>
<h3>Ticket Lifecycle Simulation</h3>
This section will demonstrate the full lifecycle of a ticket, from creation to resolution:<br>

<h4>1. Intake: A user (Jean) submits a ticket regarding "Business Critical Outage" (Help Topic).</h4>
<details>
  <summary><b>Watch: Create Ticket</b> (Click to Expand)</summary>

  https://github.com/user-attachments/assets/c3d7fca9-73eb-4ce7-871d-aeaf342691e2

</details>

<h4>2. Assignment: An agent (Scott) observes the ticket, sets it to "Emergency," and assigns it to the "SysAdmins" department.</h4>
<details>
  <summary><b>Watch: Ticket Reassignment</b> (Click to Expand)</summary>

  https://github.com/user-attachments/assets/7519fdc6-2806-44b4-a463-dfd3a6c67835

</details>

<h4>3. SLA Trigger: Because it is "Emergency," the Sev-A (1 hour) SLA is applied.</h4>
<details>
  <summary><b>Watch: SLA Trigger</b> (Click to Expand)</summary>

  https://github.com/user-attachments/assets/714d7c9f-99f2-4090-9ca2-926ebaecb240

</details>

<h4>4. Resolution: Agent 'Jean' updates the ticket, provides a resolution, and closes the request.</h4>
<details>
  <summary><b>Watch: Ticket Resolution</b> (Click to Expand)</summary>

  https://github.com/user-attachments/assets/714d7c9f-99f2-4090-9ca2-926ebaecb240

</details>

**Key Takeaways**
 - Gained hands-on experience with the LAMP/WIMP stack (Windows, IIS, MySQL, PHP)
 - Learned to translate business requirements (SLA windows, department routing) into technical configurations.
 - Developed a deep understanding of the **Ticketing Lifecycle**, a core component of IT Support and System Admin.
