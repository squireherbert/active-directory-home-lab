<h1>Active Directory Setup Guide </h1>

<h2>Project</h2>
This project focuses on setting up and managing an Active Directory environment to simulate a real world enterprise network. Using virtual machines, I will deploy Windows Server as a Domain Controller, with roles like DNS, DHCP, and Group Policy Management configured. Workstations will be joined to the domain to test user authentication, access control, and network management tasks. This lab offers hands on experience in managing Active Directory infrastructure and strengthens skills in system administration.
<br />

<br />Madakor's Guide: https://www.youtube.com/watch?v=MHsI8hJmggI


<h2>Environments Used </h2>

- <b>Windows 10, Oracle VirtualBox, Windows Server 2019</b>

<h2>Walk-through:</h2>

<p align="center">
Prepare your enviroment <br />
  
  1. Download & Install VirtualBox and ISO's for Windows 10 OS / Windows Server 2019.
     ![download virtualbox](https://github.com/user-attachments/assets/4f6acdb0-5cb6-4fc2-b4d7-01acde2755c3)
     ![download windows server](https://github.com/user-attachments/assets/7f3ddf2e-229d-4bab-917e-9cba5c7c65d4)

  2. Create a Virtual Machine for the Domain Controller.
     - Allocate 4GB RAM if your system can handle it. This will help ensure smooth performance.
     ![4](https://github.com/user-attachments/assets/4863d410-46e8-4be0-80e0-6ef5a8c1639f)

  3. Configure Network Settings in VirtualBox.
     - Go to the Network tab in Settings. Enable Adapter 2 and set it to “Internal Network.” This will allow you to set up two network interface cards, one for internet access and the other for the internal server network.
     ![5](https://github.com/user-attachments/assets/c82f1d21-ce43-4578-8fa2-a228c8f573c7)

  4. Install Windows Server on the Domain Controller VM.
     - Select Windows Server Standard (Desktop Experience).
     - Choose an administrator password.
     ![7](https://github.com/user-attachments/assets/7a56520a-b128-451f-82d7-e34e19c180e9)
     ![8](https://github.com/user-attachments/assets/87903bf9-c11a-439b-91a3-ac6aac7642ad)
  
  5. Install VirtualBox Guest Additions for Smoother Operation.
     - This helps with better integration and performance of the VM. The system will reboot for the changes to take effect.
     ![9](https://github.com/user-attachments/assets/c59d6328-d273-4864-b246-662bd0f764cd)

  6. Open Server Manager.
      - After the reboot, Server Manager should open automatically. If not, click the Windows button and open it from the menu.
     ![10](https://github.com/user-attachments/assets/7640cacf-4b57-4232-90a4-e701bc4c2752)

  7. Configure Network Adapter Settings.
      - Click on “Change adapter settings” to access the network configuration.
      - Rename the adapters for easier identification.
     ![11](https://github.com/user-attachments/assets/52d4dfe8-00e1-434d-a6a7-d426f7427f23)
     ![12](https://github.com/user-attachments/assets/3f9f0942-999d-4438-9330-d3b40b830221)
      - Rename the PC for easy identification.
     ![rename pc](https://github.com/user-attachments/assets/e94ca829-58b1-45ac-8ba9-c590846d1496)


  8. Configure Static IP for the Internal Network Adapter.
     - Right click on the internal network adapter and select “Properties.” Click on Internet Protocol Version 4 (TCP/IPv4) and then “Properties.”
     - Choose Use the following IP address and enter the IP address, subnet mask, and preferred DNS server.
      ![16](https://github.com/user-attachments/assets/0f128a47-97d0-470e-a204-b2b79a3b9aec)
      ![17](https://github.com/user-attachments/assets/935f1c5e-462d-4b62-be4f-9de477c2e2fa)

  9. Add Roles and Features for Active Directory.
      - Open Server Manager, click Add roles and features, and proceed through the wizard. Select Active Directory Domain Services (AD DS) and install.
      ![18](https://github.com/user-attachments/assets/138931b7-0f84-44e9-9306-7c00bd0b2040)

  10. Post Deployment Configuration.
      - Click Promote this server to a domain controller.
      - Choose Add a new forest and provide a domain name.
      ![new forest](https://github.com/user-attachments/assets/6aac5201-284c-4b1d-96f4-b8f5ce885d7e)

  11. Create a Dedicated Domain Admin Account.
      - After the setup, create a new user in Active Directory and assign them domain admin privileges.
      ![herbsdomain](https://github.com/user-attachments/assets/5d312246-42ea-4e3b-94a0-92fadcbea285)
      - Navigate to Active Directory Users and Computers and create an OU for organizing users and computers.
      - Right-click the new OU and create a user. Assign them necessary privileges.
      ![usr creation](https://github.com/user-attachments/assets/40ddc23c-89e7-43a6-a39a-3862fde71533)
      - Assign domain admin roles to the dedicated admin account
      ![admin role assigned](https://github.com/user-attachments/assets/b729e15d-504d-424d-aace-4a43af591ed1)

  12. Routing and Remote Access.
      - Enable routing and remote access on the server. This will allow network address translation and routing services.
        ![ras install](https://github.com/user-attachments/assets/c64c0144-f90b-4462-82b3-1dab9ce91b69)
        ![ras2](https://github.com/user-attachments/assets/22c5c2bd-ea8c-4286-909b-b1f71979636d)
        ![ras3](https://github.com/user-attachments/assets/d68d1791-a60c-4353-891f-a2a5f1a13a5f)
        ![server dash](https://github.com/user-attachments/assets/e1c2328f-7d9e-47a9-ae7f-1901ca86a392)
        
  13. Install the DHCP Server role in Server Manager.
        ![dhcp install](https://github.com/user-attachments/assets/62662c50-d8fa-4233-9529-71b8e0cce552)
      - Define a new scope, set lease duration, and configure IP range.
        ![dhcp scope 1](https://github.com/user-attachments/assets/4d060b36-5b0e-4e0e-be9e-e560c04f2be9)
      - Add options like router (gateway) address, DNS servers, and other settings for client machines.
      - Configure the router’s address to match your internal network setup.
        ![dhcp scope 2](https://github.com/user-attachments/assets/2928fe13-59f6-43d2-ad8b-78913f6fed2c)
        ![dhcp complete](https://github.com/user-attachments/assets/458102c4-c05d-498c-b17c-5b7dcf8b5d10)

  14. Use Powershell script for automation of user accounts and configurations.
      - Add created account with admin priviliges to users list.
        ![pws script 1](https://github.com/user-attachments/assets/d6a41b9b-615c-45fc-9a95-6cbab5ee89ac)
        ![pws script 2](https://github.com/user-attachments/assets/a5b61f5e-ecb2-4430-b8ec-735bac37c91f)
        ![pws script 3](https://github.com/user-attachments/assets/b1fc22e7-2c27-415a-bb93-b6b2e7099663)

  15. Install Windows 10 Virtual Machine in VirtualBox.
      - Follow similar steps to set up a Windows 10 VM and configure it to connect to the domain.
      - Rename the PC for easier identification. 
      - After setup join the Windows 10 VM to the domain by navigating to System Properties and adding it to the domain.
        ![joining](https://github.com/user-attachments/assets/23ace573-fec3-4ba9-9516-2fef380535e0)
        ![joining2](https://github.com/user-attachments/assets/c413d12e-2ba6-4b7e-8d45-6ed3df8a274b)

  16. Use DHCP Manager to monitor address leases and ensure clients are obtaining IPs correctly.
        ![dhcp manager](https://github.com/user-attachments/assets/5645410d-bf31-47ee-b2a8-caac16212d66)

      - Use active directory users and computers management to view, edit, and manage users, computers, and OUs.
        ![aduacm](https://github.com/user-attachments/assets/aecc3707-1e1a-422b-8551-b2436bff5f39)


In this lab, I successfully set up a functional Active Directory environment, which simulated a real world enterprise network. 
This project provided practical experience in system administration, deepening my understanding of Active Directory services, network configuration, and access control.

Key Takeaways
- Gained hands on experience in setting up and managing a Windows Server as a Domain Controller.
- Learned to configure essential services like DNS, DHCP, and Group Policy.
- Practiced adding and managing user accounts, groups, and organizational units.
- Developed skills in troubleshooting network and server issues within a controlled environment.

