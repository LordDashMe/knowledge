# Linux Basic Commands

## FOLDER AND FILE PERMISSION SETUP

* Change mode all with group write.

    ```text
    chmod -R g+w /path
    ```

* Change mode folder permission to drwxr-xr-x, will assign read, write and execute permission to the owner, and just read and execute permission to everyone.

    ```text
    chmod -R 755 = for directories
    ```

* Change mode file permission to -rw-r--r--, also means that files are readable and writeable by the owner of the file and readable by users in the group owner of that file and readable by everyone else.

    ```text
    chmod -R 644 = for files
    ```

* Change owner of the directories/files.

    ```text
    chown -R www-data:www-data /path
    chown {user:group} path/file.ext
    ```

* For accurate or automatic set of permission.

    ```text
    find {./path} -type d -exec chmod 755 {} \; # For Directory
    find {./path} -type f -exec chmod -Rf 644 {} \; # For Files
    ```

## FOLDER AND FILE COMMANDS

* File Rename. Its primary purpose is moving files and folders, but it can also rename them, since the act of renaming a file is interpreted by the filesystem as moving it from one name to another.

    ```text
    mv /path/source /path/destination
    ```

* File Copy.

    ```text
    cp {-R} source/file path/file (-R is for recursive copy)
    cp source/file /path/file (So far this is for the single copy tested)
    ```

* Folder or File Remove. (This will delete permanently)

    ```text
    rm -rf path/file
    ```

* Change directory view.

    ```text
    cd path/file
    ```

* View file using VIM. (This will need ```apt-get install vim```)

    ```text
    vim path/file
    ```

* To view the Root trash bin.

    ```text
    /root/.local/share/Trash/trash_files
    ```

* To compress a file using tar.

    ```text
    tar -czvf name-of-archive.tar.gz /path/to/directory-or-file
    ```

* To decompress a file using tar.

    ```text
    tar -xzvf /path/to/source/archive.tar.gz -C /tmp
    ```

* To check the directory or file size.

    ```text
    du -sh directory/
    ```

* To check the free space in the disk

    ```text
    df -h .
    ```

## NETWORK CONFIGURATION

* To view the nmap NAT for host/ip. (This will need ```apt-get install nmap```)

    ```text
    nmap {host/ip}
    ```

* To show ip address of the current machine.

    ```text
    ip addr show
    ```

* IP Tables. (This will need ```apt-get install iptables```)

    ```text
    iptables -t nat -L
    ```

* The Firewall for ubuntu, this may help for preventing unwanted access to the server, atleast a first layer of protection.

    ```text
    ufw enable
    ufw disable
    ufw allow {port}
    ufw deny {port}
    ufw reset
    ```

* To show the bridges in ubuntu. (This will need ```apt-get install bridge-utils```)

    ```text
    brctl show
    ```

* Flush DNS in Ubuntu/Linux.

    ```text
    sudo /etc/init.d/dns-clean restart
    ```
* Restart network in Ubuntu/Linux.

    ```text
    sudo /etc/init.d/networking force-reload
    ```

* Route Table Management (This will show the current list of route(s) in the table).

    ```text
    route add -net x.x.x.x (The IPADDR of route that will be adding) netmask 255.x.x.x gw (The current gateway of the local machine) 192.x.x.x
    route del -net x.x.x.x/24 (The destination IPADDR, the 24 will be depend on the size of the IPADDR by default 24 can be use)
    ```

* To set static DNS.

    Reference: https://askubuntu.com/questions/346838/how-do-i-configure-my-dns-settings-in-ubuntu-server

    ```text
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

* Some Reference to achive this command:

    http://techstuffrevolution.blogspot.com/2012/10/access-your-smart-bro-canopy-connected.html

    http://manpages.ubuntu.com/manpages/trusty/man8/route.8.html

    https://askubuntu.com/questions/677548/cant-delete-a-route-with-0-0-0-0-gateway

    http://www.configserverfirewall.com/ubuntu-linux/add-permanent-static-route-ubuntu/

## UTILITIES

* VGA or graphic card status.

    ```text
    lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
    ```

* To search application in the current proccess of linux.

    ```text
    ps aux | grep {appname}
    ```

* This will kill the searched ID application in the current proccess of linux.

    ```text
    kill {id}
    ```

* To check the server version linux.

    ```text
    lsb_release -a
    ```

* To delete downloaded packages (.deb) already installed (and no longer needed).

    ```text
    apt-get clean
    ```

* To remove unnecessary packages (after uninstalling an app there could be packages you don't need anymore).

    ```text
    apt-get autoremove
    ```

* To show the real path of the running application. (ex. java)

    ```text
    update-alternatives --list {java}
    ```

* To show the hard drive usage.

    ```text
    df
    ```

* To show all the services available.

    ```text
    service --status-all
    ```

* To change the server or local machine timezone.

    ```text
    dpkg-reconfigure tzdata
    ```