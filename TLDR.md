VPS manager: [Digital Ocean](https://cloud.digitalocean.com/)
OS: [**Ubuntu 18.04.2 LTS**]([http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/))
SIZE: 1CPU, 2GB RAM, 50GB SSD, 2TB data (upsize temporarily to 2CPUs,4GB RAM if installing r_packages_all)  
Datacenter Region: London  
IP: 
hostname:  
ports: 
domain: 
usrname: 
ssh-key: 
grpname: **public**  
public folder: `/usr/local/share/public`
$R$ packages folder: `/usr/local/share/public/R_library`
last updated: *19-Oct-2019*

### Basic Configuration

-   [x] create machine
-   [x] first connection: change root password (if not automatic, run  `passwd`)
-   [ ] check/change timezone
-   [x] update/upgrade/dist-upgrade the system
-   [x] add DO monitoring:  `curl -sSL https://agent.digitalocean.com/install.sh | sh`
-   [x] install missing  _default_  packages:
    
    ```
        apt-get install -y apt-transport-https software-properties-common dos2unix man-db ufw git-core nano libauthen-oath-perl openssh-server
    ```
    
-   [x] add user(s) to system:  `adduser luca`
-   [x] add user(s) to  _sudo_  group:  `usermod -aG sudo luca`  ==> check
-   [x] configure  _git_  for new user(s):
    
    ```
        git config --global user.name "Luca Valnegri"
        git config --global user.email "l.valnegri@datamaps.co.uk"
    ```
    
-   [x] add  _public_  group:  `sudo groupadd public`
-   [x] add user(s) to group:  `sudo usermod -aG public luca`
-   [x] add  _public_  repository
    
    ```
        sudo mkdir -p /usr/local/share/public/
        sudo chgrp -R public /usr/local/share/public/
        sudo chmod -R 2775 /usr/local/share/public/
    ```
    
-   [x] set public repo in  `/etc/environment`  as  **PUB_PATH**
-   [x] reboot:  `sudo reboot`
-   [x] add subfolders  `software`  and  `scripts`  to  `home`  folder
-   [x] add subfolders  `subs`  and  `r_packages`  to  `scripts`  subfolder
-   [x]  `cd subs`  then download from pastebin the files  _916041fv_  as  **public_subs.sh**  and  _zbzDnuHb_  as  **public_subs.lst**:  
    `wget -O public_subs.sh https://pastebin.com/raw/916041fv`  
    `wget -O public_subs.lst https://pastebin.com/raw/zbzDnuHb`
-   [x] convert to UNIX format:  `dos2unix public_subs.lst public_subs.sh`  or simply  `dos2unix *`
-   [x] make  **public_subs.sh**  executable:  `chmod +x public_subs.sh`
-   [x] run  **public_subs.sh**  to add subfolders to  _public_  repo:  `./public_subs.sh`
-   [x] follow the same steps as above to create subfolders in the  _home_  folder:  
    `wget -O home_subs.sh https://pastebin.com/raw/XThRT4u4`  
    `wget -O home_subs.lst https://pastebin.com/raw/Ze6M1snP`
-   [x] deny the  `root`  user direct access via SSH:  `sudo nano /etc/ssh/sshd_config`  (restart SSH + check)
-   [x] change port to SSH:  `sudo nano /etc/ssh/sshd_config`  (restart SSH + check)
-   [x] enable firewall:  `sudo ufw enable`  (check)
-   [x] allow (new) SSH port:  `sudo ufw allow XYYYY`  (check)
-   [x] install webmin / allow port 10000 (check, remember it's only on  `https`)
-   [x] redirect http / change port / allow new port / delete previous port rule (check)
-   [x] add 2FA
-   [x] add a domain name (see  [Freenom](https://www.freenom.com/)  for a  _true_  free domain)
-   [x] take a snapshot:  _webmin_
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDY1Nzg0MTVdfQ==
-->