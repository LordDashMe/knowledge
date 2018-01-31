# Linux Basic Commands

#### FOLDER AND FILE PERMISSION SETUP  
- Change mode all with group write.
```chmod -R g+w /path```

- Change mode folder permission to drwxr-xr-x, will assign read, write and execute permission to the owner, 
    and just read and execute permission to everyone.
```chmod -R 755 = for directories```

- Change mode file permission to -rw-r--r--, also means that files are readable and writeable by the owner of the file 
    and readable by users in the group owner of that file and readable by everyone else.
```chmod -R 644 = for files```

- Change owner of the directories/files.
```chown -R www-data:www-data /path```
```chown <user>:<user> path/file.ext```

- For accurate or automatic set of permission.
```find {./path} -type d -exec chmod 755 {} \;```
```find {./path} -type f -exec chmod -Rf 644 {} \;```

#### FOLDER / FILE COMMANDS ####
- File Rename. Its primary purpose is moving files and folders, but it can also rename them, 
    since the act of renaming a file is interpreted by the filesystem as moving it from one name to another.
```mv /source/file /path/file```

- File Copy.
```cp {-R} source/file path/file (-R is for recursive copy)```
```cp source/file /path/file (So far this is for the single copy tested)```

- Folder or File Remove. (This will delete permanently)
```rm -rf path/file```

- Change directory view.
```cd path/file```

- View file using VIM. (This will need to install the vim)
```vim path/file```        

- To view the Root trash bin.
```/root/.local/share/Trash/trash_files```

- To compress a file using tar.
```tar -czvf name-of-archive.tar.gz /path/to/directory-or-file```

- To decompress a file using tar.
```tar -xzvf /path/to/source/archive.tar.gz -C /tmp```

#### NETWORK CONFIGURATION ####
- To view the nmap NAT for host/ip. (This will need to install nmap)
```nmap {host/ip}```

- To show ip address of the current machine.
```ip addr show```

- or in Digital Ocean
```ip addr show eth0 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'```

- IP Tables. (This will need to install the iptables)
```iptables -t nat -L```

- The Firewall for ubuntu, this may help for preventing unwanted access to the server, atleast a first layer of protection.
```
ufw enable
ufw disable
ufw allow {port}
ufw reset
```

- To show the bridges in ubuntu. (This will need to install bridge-utils)
```brctl show```
   
- Flush DNS in Ubuntu/Linux.
```sudo /etc/init.d/dns-clean restart```

```sudo /etc/init.d/networking force-reload```

- Route Table Management. (This will show the current list of route(s) in the table) ```route ```
```
route add -net x.x.x.x (The IPADDR of route that will be adding) netmask 255.x.x.x gw (The current gateway of the local machine) 192.x.x.x
```
```
route del -net x.x.x.x/24 (The destination IPADDR, the 24 will be depend on the size of the IPADDR by default 24 can be use)
```

- To set static DNS.
    - Reference: https://askubuntu.com/questions/346838/how-do-i-configure-my-dns-settings-in-ubuntu-server
```
$ vim /etc/network/interfaces


# The loopback network interface  
auto lo  
iface lo inet loopback  


# The primary network interface  
auto eth0 
iface eth0 inet static  
address 192.168.X.X
netmask 255.255.255.0
gateway 192.168.X.X
dns-nameservers X.X.X.X

:wq (Save the changes)


$ /etc/init.d/networking restart (Refresh all the configuration)
```

- Some Reference to achive this command:
    * http://techstuffrevolution.blogspot.com/2012/10/access-your-smart-bro-canopy-connected.html
    * http://manpages.ubuntu.com/manpages/trusty/man8/route.8.html
    * https://askubuntu.com/questions/677548/cant-delete-a-route-with-0-0-0-0-gateway
    * http://www.configserverfirewall.com/ubuntu-linux/add-permanent-static-route-ubuntu/

#### UTILITIES ####
- VGA or Graphic Card Status
```lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA```

- To kill app in linux
```ps aux | grep <app>```

- This will search the application info
    - get the id on the ps aux result and use this command.
```kill <id>```      
    
- To check the server version Linux
```lsb_release -a```

- To delete downloaded packages (.deb) already installed (and no longer needed) 
```apt-get clean```

- To remove unnecessary packages (After uninstalling an app there could be packages you don't need anymore)
```apt-get autoremove```

- To show the real path of the running application. ex. java
```update-alternatives --list {java}```

- To show the hard drive usage.
```df```

- To show all the services available
```service --status-all```