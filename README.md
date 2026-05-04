# Installing Wazuh

```bash
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
bash wazuh-install.sh

```
Open port in firewall on RHEL 9:
```bash
firewall-cmd --permanent --add-port=443/tcp
sudo firewall-cmd --permanent --add-port=1514/tcp
sudo firewall-cmd --permanent --add-port=1514/udp
sudo firewall-cmd --permanent --add-port=1515/tcp
sudo firewall-cmd --reload
```
The Wazuh web interface is accessible via the address:  
 `https://wazuh-dashboard-ip:443` 

![login1](/assets/image1.png)

Deploying Wazuh agents on Linux endpoints:  
`https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-linux.html`

![login1](/assets/image2.png)

# Task 1
## Key elements of Linux monitoring in Wazuh  
Monitor:  
- SSH logins (successful and unsuccessful)  
- Local logins (console)  
- Brute-force attempts  
- Root logins  
- Sudo and su usage  

# Task 2 
## Administrative activity (root/sudo)  
Monitor:  
- All commands executed as root  
- Sudo usage  
- Privilege escalations  
- User creation/change  
- Group changes (e.g., adding to sudoers)  

# Task 3 
## File System Integrity (FIM)  
Monitor:  
- /etc/passwd, /etc/shadow  
- /etc/sudoers  
- /etc/ssh/sshd_config  
- Service configuration files  
- System directories (/bin, /usr/bin, /lib)  

# Task 4 
## Processes and running applications  
Monitor:  
- New system processes  
- Unusual processes (e.g., mining, reverse shell)  
- Processes started by root  
- Long-running suspicious processes  

# Task 5
## Network Connections  
Monitor:  
- New outgoing connections  
- Unusual ports  
- Connections to unknown IP addresses  
- Traffic from the server to the Internet (data exfiltration)  

# Task 6 
## Package Installation and Modification  
Monitor:  
- Apt install/remove  
- Repository changes  
- System updates  
- Installation of unknown packages  

# Task 7
## System and Service Logs  
Monitor:  
- /var/log/auth.log (authorization)  
- /var/log/syslog  
- Service logs (Apache, Nginx, SSH, DB)  
- System and kernel errors  

# Task 8 
## System Configuration Changes  
Monitor:  
- /etc/hosts  
- /etc/crontab and cron users  
- Network configuration  
- Firewall (nftables)  

# Task 9 
## Changing the schedule (cron jobs)  
Monitor:  
- New cron entries  
- Modifications to existing jobs  
- Running system scripts  

# Task 10 
## User integrity and permissions  
Monitor:  
- Creation of new accounts  
- UID 0 changes  
- Modifications to administrative groups  

# Task 11 
## DNS and Unusual Communication  
Monitor:  
- DNS queries to unusual domains  
- DNS tunneling  
- Communication with C2 (command & control)  

# Task 12 
## Kernel Security Events  
Monitor:  
- Kernel panic errors  
- Kernel module loading  
- Suspicious modules (insmod, modprobe)  


Task solutions coming soon 😃