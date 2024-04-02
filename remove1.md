---WARNING. READ BEFORE RUNNING STEP 1--- First step could cause more problems and you'll probably get a bunch of errors more.

NOTE: I rebooted many times, maybe rebooting it after every step could help

1 . My first step was to find where cloudpanel was located and then I removed /tmp/cloudpanel and /usr/share/doc/cloudpanel
```
dpkg -L cloudpanel
sudo rm -rf /tmp/cloudpanel
sudo rm -rf /usr/share/doc/cloudpanel
```
After that I remember I tried to run sudo apt remove cloudpanel but that just caused more problems and I don't really think this helped me at all but I add this step here just to let you know all what I did.

2 . I moved to /home and remove every possible folder created by cloudpanel
```
sudo rm -rf /home/clp 
sudo rm -rf /home/mysql
```
3 . After rebooting I deleted the user created by cloudpanel.
```
sudo userdel clp
```
In the case that you are not able to delete the user try rebooting again and/or killing all processes by clp.
```
sudo killall --user clp && sudo userdel clp
```
4 . Remove cloudpanel from sudoers
```
sudo rm -rf /etc/sudoers.d/cloudpanel
```
Delete cloudpanel's info from dpkg and configure dpkg
```
sudo rm -rf /var/lib/dpkg/info/cloudpanel sudo dpkg --configure -a
```
Now you should be able to uninstall cloudpanel
```
sudo apt remove cloudpanel sudo apt autoremove
```
I don't know what exactly did it and I don't really think sped 1 is required.

Hope it helps!
