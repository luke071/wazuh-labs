# Running Wazuh on Euro Linux 9

```bash
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh
curl -sO https://packages.wazuh.com/4.14/config.yml
```
Wazuh consists of three components: an indexer, a server, and a dashboard. It edits the config.yml file and provides the IP address in three places.

```yml
  # Wazuh indexer nodes
  indexer:
    - name: node-1
      ip: "192.168.0.150"
    #- name: node-2
    #  ip: "<indexer-node-ip>"
    #- name: node-3
    #  ip: "<indexer-node-ip>"

  # Wazuh server nodes
  # If there is more than one Wazuh server
  # node, each one must have a node_type
  server:
    - name: wazuh-1
      ip: "192.168.0.150"
    #  node_type: master
    #- name: wazuh-2
    #  ip: "<wazuh-manager-ip>"
    #  node_type: worker
    #- name: wazuh-3
    #  ip: "<wazuh-manager-ip>"
    #  node_type: worker

  # Wazuh dashboard nodes
  dashboard:
    - name: dashboard
      ip: "192.168.0.150"
```
Run the Wazuh installation:
```bash
bash wazuh-install.sh --generate-config-files
```
Run the Wazuh installation assistant:
```bash
bash wazuh-install.sh --wazuh-indexer node-1
```
Run the Wazuh installation:
```bash
bash wazuh-install.sh --start-cluster
```
Testing the cluster installation:
```bash
tar -axf wazuh-install-files.tar wazuh-install-files/wazuh-passwords.txt -O | grep -P "\'admin\'" -A 1
```
Download the Wazuh installation assistan:
```bash
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh
```
Run the Wazuh installation assistant:
```bash
bash wazuh-install.sh --wazuh-server wazuh-1
```
Wazuh dashboard installation"
```bash
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh
```
Run the Wazuh installation assistant:
```bash
bash wazuh-install.sh --wazuh-dashboard dashboard
```
Open port in firewall:
```bash
firewall-cmd --add-port=443/tcp permanent
firewall-cmd --reload
```

# Task 1 Key elements of Linux monitoring in Wazuh
Monitor:  
- SSH logins (successful and unsuccessful)  
- Local logins (console)  
- Brute-force attempts  
- Root logins  
- Sudo and su usage  

# Task 2 Administrative activity (root/sudo)
Monitor:  
- All commands executed as root  
- Sudo usage  
- Privilege escalations  
- User creation/change  
- Group changes (e.g., adding to sudoers)  

# Task 3 File System Integrity (FIM)
Monitor:  
- /etc/passwd, /etc/shadow  
- /etc/sudoers  
- /etc/ssh/sshd_config  
- Service configuration files  
- System directories (/bin, /usr/bin, /lib)  

# Task 4 Processes and running applications
Monitor:  
- New system processes  
- Unusual processes (e.g., mining, reverse shell)  
- Processes started by root  
- Long-running suspicious processes  

# Task 5 Network Connections
Monitor:  
- New outgoing connections  
- Unusual ports  
- Connections to unknown IP addresses  
- Traffic from the server to the Internet (data exfiltration)  

# Task 6 Package Installation and Modification
Monitor:  
- Apt install/remove  
- Repository changes  
- System updates  
- Installation of unknown packages  

# Task 7 System and Service Logs
Monitor:  
- /var/log/auth.log (authorization)  
- /var/log/syslog  
- Service logs (Apache, Nginx, SSH, DB)  
- System and kernel errors  

# Task 8 System Configuration Changes
Monitor:  
- /etc/hosts  
- /etc/crontab and cron users  
- Network configuration  
- Firewall (nftables)  

# Task 9 Changing the schedule (cron jobs)
Monitor:  
- New cron entries  
- Modifications to existing jobs  
- Running system scripts  

# Task 10 User integrity and permissions
Monitor:  
- Creation of new accounts  
- UID 0 changes  
- Modifications to administrative groups  

# Task 11 DNS and Unusual Communication
Monitor:  
- DNS queries to unusual domains  
- DNS tunneling  
- Communication with C2 (command & control)  

# Task 12 Kernel Security Events
Monitor:  
- Kernel panic errors  
- Kernel module loading  
- Suspicious modules (insmod, modprobe)  


Task solutions coming soon 😃