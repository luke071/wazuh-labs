# Installing Wazuh

## Ubuntu 22.04 and Debian 12
```bash
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh
sudo bash ./wazuh-install.sh -a
```

Open ports in firewall:
```bash
sudo ufw allow 443/tcp
sudo ufw allow 1514/tcp
sudo ufw allow 1515/tcp

sudo ufw reload
sudo ufw status numbered
```

## Rocky Linux 9
```bash
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
bash wazuh-install.sh

```
Open ports in firewall:
```bash
sudo firewall-cmd --permanent --add-port=443/tcp
sudo firewall-cmd --permanent --add-port=1514/tcp
sudo firewall-cmd --permanent --add-port=1514/udp
sudo firewall-cmd --permanent --add-port=1515/tcp

sudo firewall-cmd --reload
sudo firewall-cmd --list-ports
```

Checking services after installation:
```bash
sudo systemctl status wazuh-manager
sudo systemctl status wazuh-indexer
sudo systemctl status wazuh-dashboard
```

Installation logs:
```bash
cat /var/log/wazuh-install.log
```
Wazuh service logs:
```bash
sudo journalctl -u wazuh-manager
sudo journalctl -u wazuh-indexer
sudo journalctl -u wazuh-dashboard
```
## Wazuh Logs
Live logs:
```bash
sudo journalctl -fu wazuh-manager
```
Last 50 lines:
```bash
sudo journalctl -u wazuh-indexer -n 50
```
Logs from today:
```bash
sudo journalctl -u wazuh-dashboard --since today
```
Only errors:
```bash
sudo journalctl -p err -u wazuh-indexer
```
Security alert log:
```bash
tail -f /var/ossec/logs/alerts/alerts.log
```

The Wazuh web interface is accessible via the address:  
 `https://wazuh-dashboard-ip:443` 

![login1](/assets/image1.png)

Deploying Wazuh agents on Linux endpoints:  
`https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-linux.html`

Agent logs:
```bash
/var/ossec/logs/ossec.log
```

![login1](/assets/image2.png)

Almost clean Rocky Linux 9, without network services for clients with an ssh server passed the test with 56%.
![login1](/assets/image3.png)

 
# Task 1
## Logins and authentication 
Monitor:  
- SSH logins   
- Local logins   
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
- Group changes   

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
- Unusual processes  
- Processes started by root  
- Long-running suspicious processes  

# Task 5
## Network Connections  
Monitor:  
- New outgoing connections  
- Unusual ports  
- Connections to unknown IP addresses  
- Traffic from the server to the Internet 

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
- Firewall  

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

# Task 13
## Performance metrics
Monitor:
- CPU usage
- CPU load
- Memory utilization
- Disk usage

# Task 14
## Docker 
Monitor:
- Container events
- Docker image changes
- Container configuration changes
- Container network events

# Task 15
## Backend Services
Monitor:
- NGINX 
- Apache HTTPD 
- PostgreSQL 
- Node.js 