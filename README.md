<h1>Active Directory Home Lab Setup </h1>


<h2>Project</h2>
This project is dedicated to setting up and managing an Active Directory environment to simulate a real world enterprise network. Using virtual machines, I will deploy a Windows Server as a Domain Controller and configure various roles such as DNS, DHCP, and Group Policy Management. Workstations will be joined to the domain to test user authentication, access control, and network management tasks. This lab provides hands-on experience in managing an Active Directory infrastructure and enhances skills in system administration.
<br />

<br /> Guide

<h2>Languages and Utilities Used</h2>

- <b></b> 


<h2>Environments Used </h2>

- <b>Windows 10, Oracle VirtualBox, Windows Server 2019</b>

<h2>Project walk-through:</h2>

<p align="center">
Prepare your enviroment <br />
  
  1. Download VirtualBox, then download ISO's for Windows 10 OS and Windows Server 2019.
     ![download virtualbox](https://github.com/user-attachments/assets/4f6acdb0-5cb6-4fc2-b4d7-01acde2755c3)
     ![download windows server](https://github.com/user-attachments/assets/7f3ddf2e-229d-4bab-917e-9cba5c7c65d4)
  
  2. Install VirtualBox.
     ![install virtualbox](https://github.com/user-attachments/assets/350cd08d-2723-4049-a8d3-17702be16cc6)

  3. Next create a virtual machine to be used as the Domain Controller. Utilize the Windows server ISO of your choice. I used Windows Server 2019.
     Depending on your host specs, try to allocate a good amount of memory in order for the VM to run smoothly. Preferable 4GBS of RAM, as long as your system can handle it. 
     ![4](https://github.com/user-attachments/assets/4863d410-46e8-4be0-80e0-6ef5a8c1639f)

  4. On the Network tab in Settings, configure Adapter 2. Enable it and attach it to the internal network.
     You want to have 2 NICs, one for internet and the other for the internal server.
     ![5](https://github.com/user-attachments/assets/c82f1d21-ce43-4578-8fa2-a228c8f573c7)

  5. Now install Windows Server on the DC machine. 
     ![6](https://github.com/user-attachments/assets/bdeb8367-3047-47dd-b087-13506fd12f44)
             --      Select Windows Server Standard (Desktop Experience)     --
     ![7](https://github.com/user-attachments/assets/7a56520a-b128-451f-82d7-e34e19c180e9)
                   --              Chosee Admin Password          --
     ![8](https://github.com/user-attachments/assets/87903bf9-c11a-439b-91a3-ac6aac7642ad)
  
  7. For smoother operations on the VM, install VirtualBox Guest Additions. The system will reboot before changes take effect.
     ![9](https://github.com/user-attachments/assets/c59d6328-d273-4864-b246-662bd0f764cd)

  8. After boot up Server Manager should open. If it doesn't, click the windows button and you should be able to open from there.
     ![10](https://github.com/user-attachments/assets/7640cacf-4b57-4232-90a4-e701bc4c2752)

  9. From the Network configurations settings, click change adapter settings. Rename the adapters for easier identification.  
     ![11](https://github.com/user-attachments/assets/52d4dfe8-00e1-434d-a6a7-d426f7427f23)
     ![12](https://github.com/user-attachments/assets/3f9f0942-999d-4438-9330-d3b40b830221)
     After renaming, configure the adapter for the internal network according to the network diagram.

  10. Right click on the internal network adapter and click properties. Click on IPv4, then select properties.
      ![16](https://github.com/user-attachments/assets/0f128a47-97d0-470e-a204-b2b79a3b9aec)

      Select "Use the following IP address" then input the ip address, subnet mask, and preferred DNS  server.
      ![17](https://github.com/user-attachments/assets/935f1c5e-462d-4b62-be4f-9de477c2e2fa)

  11. Add roles and features
      ![18](https://github.com/user-attachments/assets/138931b7-0f84-44e9-9306-7c00bd0b2040)




     














