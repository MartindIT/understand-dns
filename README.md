<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)


<h2>Deployment and Configuration Steps</h2>

![image](https://github.com/MartindIT/understand-dns/assets/151476834/2751ca1d-33f2-4b21-861b-d1dcc6e331f9)

**1.) So firstly we will begin where we left off from the first Active Directory Lab and use Client-1 but log in as "Jane Doe" we will need an admin account. But I will try to Ping "MainFrame" which in this case our local DNS cache and host file doesnt store "Mainframe" which leads the ping to fail.**

![image](https://github.com/MartindIT/understand-dns/assets/151476834/7a143c0d-b9af-4998-969c-88d32cacc1a4)
![image](https://github.com/MartindIT/understand-dns/assets/151476834/4a2ef8fa-3966-44b6-a1ad-275f58bdc3f8)

**2.) Then we will log in to the Domain Server VM and go to DNS on the Server Manager then we will create a DNS A-Record called "Mainframe"** 

![image](https://github.com/MartindIT/understand-dns/assets/151476834/7172fae9-53c8-4ce5-abf2-e00c7407353f)
![image](https://github.com/MartindIT/understand-dns/assets/151476834/26b20966-7902-41f8-af90-daed130eba26)

**3) Now when we go back to client-1 VM it shows Mainframe responding to the replys and is coming from 10.0.0.4 which we manually did within the Domain Controller and now DNS will be in the DNS local cache and not bother the DNS server**

![image](https://github.com/MartindIT/understand-dns/assets/151476834/7a99d997-3217-4628-92e1-3fda6f69305f)
![image](https://github.com/MartindIT/understand-dns/assets/151476834/bf0b9664-02f2-4502-a69d-0ec65b35b5d3)

**4.) We will now go back to Domain Controller and change Mainframe IP Address to "8.8.8.8" then go back to Client-1 VM just to see that it hasnt updated and is still at "10.0.0.4" which why we will now flush dns and ping mainframe again which now pops up to "8.8.8.8" this shows that DNS couldnt find it through its local cache since its been flushed so it had to contact the DNS server to get the updated record.**

![image](https://github.com/MartindIT/understand-dns/assets/151476834/2c9badb6-a7b4-4a48-9555-abd657d88f79)
![image](https://github.com/MartindIT/understand-dns/assets/151476834/8678194d-1505-4087-a18f-4f3c097be90a)
![image](https://github.com/MartindIT/understand-dns/assets/151476834/04d0c6a8-2c07-419e-a52c-a14f8f647d38)

**5.) Additionally, we can do the same thing with CNAME when I type "ping search" nothing happens but when I change the domain name to "Google" it pop up as google and it just shows us that we can map names to other names. Other than that this sums up the DNS project and just emphasize what the purpose of DNS Fush command does in the IT Field and gives you great practice.** 




