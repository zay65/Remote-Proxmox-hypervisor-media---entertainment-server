# Remote-Proxmox-hypervisor-media-entertainment-server
Designed and managed a remote Proxmox-based homelab environment featuring Linux and Windows virtualized infrastructure, NAS file sharing (Samba), media streaming (Jellyfin), secure remote access (Tailscale/SSH), and enterprise-style Active Directory administration.

<h2> Initial install and config process </h2>

- <b2> Downloaded latest iso version of proxmox </b2>
- <b2> Flashed iso to usb drive with balena etcher </b2>
- <b2> Plugged in, booted from, & installed proxmox onto HP Prodesk g4 mini with usb, & configured proxmox settings </b2>

 <p align="center">
    <img src="https://github.com/zay65/Proxmox-Azure-SCCM-Intune-homelab/blob/0c3ff57b3c7e7ffe1a330520cdb137858bae454d/Proxmox%20Balena%20flash.png" alt="Sample Image"/>
  </p>

 <h2> DHCP reservation & SSH login </h2>

 - <b2> After Proxmox Virtual Environment (PVE) server is installed, I reserve the IP address in my router's DHCP settings so that it remains static.</b2> 

 <p align="center">
    <img src="https://github.com/zay65/Ubuntu-remote-storage-media-entertainment-server/blob/1c96b082cbd909a656e0515c4db41876f51ac6a2/Reserved%20IP%20address%20in%20AT%26T%20router%20DHCP%20settings.png" alt="Sample Image"/>
  </p>


<h2> Remote server access with Tailscale & SSH login </h2>

- <b2> Within the shell of my Proxmox Virtual Environment (PVE) node, I entered and edited the SSH config files to permit root login access, allowing me to securely operate network services, log into remote machines, and execute commands over an unsecured network </b2>
- <b2> Installed "curl" in my PVE, allowing me to download, use, and send and receive a variety of files and protocols to and from the internet </b2>
- <b2> Installed tailscale, which acts as a client-to client VPN, allowing me to remotely access any device running the Tailscale client (called a node) and communicating directly with any other node in my private network (tailnet).</b2>

 <p align="center">
    <img src="https://github.com/zay65/Proxmox-Azure-SCCM-Intune-homelab/blob/c96d93bb36b3e72da5ebe95d57bb5af91e16b351/Remote%20server%20access%20with%20Tailscale.png" alt="Sample Image"/>
  </p>   

- <b2> I then SSH into my server via my windows laptop. </b2>

 <p align="center">
    <img src="https://github.com/zay65/Ubuntu-remote-storage-media-entertainment-server/blob/1c96b082cbd909a656e0515c4db41876f51ac6a2/SSH'd%20into%20linux%20server.png" alt="Sample Image"/>
  </p>
  
 <p align="center">
    <img src="https://github.com/zay65/Ubuntu-remote-storage-media-entertainment-server/blob/1c96b082cbd909a656e0515c4db41876f51ac6a2/Lin%20Serv%20Login%20Succ.png" alt="Sample Image"/>
  </p>



 



<h2> File sharing with Windows machines using Samba </h2>

 - <b2> Install Samba, create and assign directory for files, and name it something easy to remember like "myfiles". </b2>

 <p align="center">
    <img src="https://github.com/zay65/Ubuntu-remote-storage-media-entertainment-server/blob/eaed17513f30934b3cd701f09b45acf77a0856e0/Samba%20Install.png" alt="Sample Image" width="50%" height="50%">
  </p>

 <p align="center">
    <img src="https://github.com/zay65/Ubuntu-remote-storage-media-entertainment-server/blob/eaed17513f30934b3cd701f09b45acf77a0856e0/Samba%20Installed%20with%20directory%20config.png" alt="Sample Image" width="50%" height="50%">
  </p>

- <b2> Map network drive on windows computer to Linux Server for Network Attached Storage (NAS).</b2>

<p align="center">
    <img src="https://github.com/zay65/Ubuntu-remote-storage-media-entertainment-server/blob/1c96b082cbd909a656e0515c4db41876f51ac6a2/Net%20Drive%20map%20to%20serv.png" alt="Sample Image" width="30%" height="30%">
  </p>

<h2> Organize, manage, and stream media (movies, TV, music, photos) to various devices using Jellyfin </h2>

- <b2> Install Jellyfin </b2>
 
<p align="center">
    <img src="https://github.com/zay65/Ubuntu-remote-storage-media-entertainment-server/blob/a5f39abf85574507dbad9ed40c450a4f3d1bd0ff/Jellyfin%20Installing.png" alt="Sample Image" width="70%" height="70%">
  </p>

  <p align="center">
    <img src="https://github.com/zay65/Ubuntu-remote-storage-media-entertainment-server/blob/1c96b082cbd909a656e0515c4db41876f51ac6a2/JF%20installed.png" alt="Sample Image" >
  </p>

- <b2>  Upload movies and shows in MP4 format to the mapped network drive from any of my devices (windows, mac, etc), configure & map my jellyfin media access directory to "myfiles" and create user account(s). </b2>


 <p align="center">
    <img src="https://github.com/zay65/Ubuntu-remote-storage-media-entertainment-server/blob/3ab67961ee5eb134dfa3b6ea298969bf5db1bed9/Jellyfin%20home%20UI.png" alt="Sample Image" >
  </p>

- <b2> Jellyfin only allows devices on the local network to access the server, meaning I'd have to be at home to watch my movies which defeats the purpose of this being a fully fledged remote server. So I configure Tailscale to recognize my IT server as the main host and Tailscale creates a secure tunnel for me to watch my media from anywhere in the world via VPN  </b2>

 <p align="center">
    <img src="https://github.com/zay65/Ubuntu-remote-storage-media-entertainment-server/blob/a0fd2aa4187a1fd0cdcb08f09c98b7c9c87169ef/Jellyfin%20Home%20UI%20with%20Tailscale%20connected.png" alt="Sample Image" >
  </p>
