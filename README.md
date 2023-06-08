# Walking Dead Image Solutions
## Version: Ubuntu 12.04.3 LTS 
### Rick Grimes password: cyberpatriot
[A web page to explain shell commands for Linux and Unix](https://explainshell.com/)

Item | Linux Commands|
---|---
Root password needs to be changed to meet complexity requirements.|`sudo -i passwd`  
All users should be added to their appropriate groups and permissions.<br> cut removes from each line|`cut -d ":" -f 1 /etc/passwd`  
Lock out all zombie accounts.|`sudo passwd -l username`  
Navigate to the directory that contains all user home directories for the next line|`cd ..`  
Make sure the Zombies home directories are only accessible by root|`sudo chmod 0000 <zombie home directory name>`  
Do not allow Rick Grime's home directory to be globally readable.|`sudo chmod 700 <directory name(readable for user and root)>`  
Look at all accounts to see all users. <br>Any with L that is not a zombie should be secured with a password.|`sudo passwd --status -a`  
All accounts should be secured with a password.<br>Make a generic password for all non-zombies|`sudo passwd <username>`  
Expire their password to force them to reset on next login|`sudo passwd -e <username>`
Disable SSH access to disabled users. |`sudo nano /etc/ssh/sshd_config`  
Enable Ubuntu firewall.|`sudo ufw enable`
Open port 8080 in firewall.|`sudo ufw allow 8080`  
Close port 22 and 23.|`sudo ufw deny 22`<br>`sudo ufw deny 23`  
Download and install any packages required in the readme file.|`sudo apt install <packagename>`
Encrypt Linux file system completely.|`sudo apt-get install ecryptfs-utils cryptsetup`<br>`sudo ecryptfs-migrate-home -u user`
Apply appropriate lockout policies.| [Check out these commands to learn more](https://websistent.com/linux-password-lockout-policy/)
Apply password minimum length.<br>Apply password complexity.|`sudo nano /etc/pam.d/common-password`<br>make changes to (minlen) password [success=1 default=ignore] pam_unix.so obscure sha512 minlen=12
Enable auditd to monitor the system.|`service auditd start`
Find all noowner files and delete them.|`find / -nogroup -nouser`
Scan for rootkits.|`sudo chkrootkit`
Change SSH default port 22 to any higher number.|`sudo nano /etc/ssh/sshd_config`<br> change line #Port 22 to Port <port number>
Disable root login access.|`sudo passwd -l root`
One Step User Cron jobs Removal|`crontab -l`<br>`mv /var/spool/cron  /var/spool/cron_is_disabled`
Line by line cron job removal|`sudo nano crontab -e` then comment out each line you don't want to run with #
View all cron jobs.|`sudo crontab -u <userName> -l`<br>`sudo crontab -l`<br>[more info](https://www.cyberciti.biz/faq/linux-show-what-cron-jobs-are-setup/)
Lockdown cronjobs. |First backup the cron jobs file `crontab -l > my_cron_backup.txt`<br>Then you can empty it:`crontab -r`<br>To restore:`crontab my_cron_backup.txt`<br>
