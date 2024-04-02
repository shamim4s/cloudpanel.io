Step 1: Backup Your Data
Before making any significant changes to your server, it’s crucial to backup all essential data. This ensures that you can restore your system to its previous state if something goes wrong.

Backup your web directories.
Export databases to safe locations.
Make a copy of any configuration files you’ve customized.
Step 2: Stop All CloudPanel Services
Before uninstalling, ensure that all CloudPanel-related services are stopped.
```
sudo systemctl stop cloudpanel
```
Step 3: Remove CloudPanel Packages
Use the package manager to remove CloudPanel and its dependencies.
```
sudo apt-get purge cloudpanel
```
Step 4: Remove CloudPanel Directories
After uninstalling the packages, manually remove any leftover directories related to CloudPanel.
```
sudo rm -rf /etc/cloudpanel
sudo rm -rf /var/www/cloudpanel
```
Step 5: Cleanup the Database
If you’re not planning to reinstall CloudPanel or use its database, you might want to remove its database and user.

See also  How to Uninstall Caddy Server on Ubuntu
Login to MySQL:
```
mysql -u root -p
```
Drop the CloudPanel database:

DROP DATABASE cloudpanel;
Remove the CloudPanel user:
```
DROP USER 'cloudpanel'@'localhost';
```
Exit MySQL:

exit
Step 6: Revert System Configurations
CloudPanel might have made changes to your system configurations, such as firewall rules or PHP settings. Ensure you revert these changes to avoid potential conflicts with other software.

Commands Mentioned
```
sudo systemctl stop cloudpanel – Stops the CloudPanel service.
sudo apt-get purge cloudpanel – Removes CloudPanel packages.
sudo rm -rf /etc/cloudpanel – Deletes CloudPanel configuration directory.
mysql -u root -p – Logs into MySQL.
```
