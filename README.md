# Walking Dead Image Solutions
## Version: Ubuntu 12.04.3 LTS 
### Rick Grimes password: cyberpatriot

Item | Linux Commands|
---|---
Root password needs to be changed to meet complexity requirements.|`sudo -i passwd`
All users should be added to their appropriate groups and permissions.|`cut -d ":" -f 1 /etc/passwd`
Lock out all zombie accounts.|`sudo passwd -l username`
Do not allow Rick Grime's home directory to be globally readable.|`sudo chmod 700 <directory name(readable for user and root)>`<br>`sudo chmod 0000 <directory name (readable only by root)>`
Look at all accounts to see all users. Any with L that is not a zombie should be secured with a password.|`sudo passwd --status <username>`
All accounts should be secured with a password.|`sudo passwd --status <username>`
Disable SSH access to disabled users.|``
Enable Ubuntu firewall.|`sudo ufw enable`
Open port 8080 in firewall.|`sudo ufw allow 8080`
Close port 22 and 23.|`sudo ufw deny 22`<br>`sudo ufw deny 23`
Download and install all packages.|`sudo apt install <packagename>`
Encrpyt Linux file system completely.|`sudo apt-get install ecryptfs-utils cryptsetup`<br>`sudo ecryptfs-migrate-home -u user`
Apply appropriate lockout policies.|``
Apply password minimum length.<br>Apply password complexity.|`sudo nano /etc/pam.d/common-password`<br>make changes to (minlen) password [success=1 default=ignore] pam_unix.so obscure sha512 minlen=12
Enable auditd to monitor the system.|`service auditd start`
Find all noowner files and delete them.|`find / -nogroup -nouser`
Scan for rootkits.|`sudo chkrootkit`
Change SSH default port 22 to any higher number.|`sudo nano /etc/ssh/sshd_config`<br> change line #Port 22 to Port <port number>
Disable root login access.|`sudo passwd -l root`
View all cron jobs.|`sudo crontab -u <userName> -l`<br>`sudo crontab -l`<br>[more info](https://www.cyberciti.biz/faq/linux-show-what-cron-jobs-are-setup/)
Lockdown cronjobs. |First backup the cron jobs file `crontab -l > my_cron_backup.txt`<br>Then you can empty it:`crontab -r`<br>To restore:`crontab my_cron_backup.txt`<br>
One Step Usewr Cron jobs Removal|`crontab -l`<br>`mv /var/spool/cron  /var/spool/cron_is_disabled`
Line by line cron job removal|`sudo nano crontab -e` then comment out each line you don't want to run with #

