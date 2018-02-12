# Linux Users, Groups, Permissions and Directory Jail

----

### Manage User Linux
- To add user.
    ```
    useradd new_username
    ```
- To delete user.
    ```
    userdel username
    ```
- To modify user username:
    ```
    usermod -l new_username old_username
    ```
- To change password of username:
    ```
    passwd username
    ```
- To change the shell for a user:
    ```
    chsh username
    ```
- To change the details for a user
    ```
    chfn username
    ```
- Reference:
    - Add user to group | create group : http://www.hostingadvice.com/how-to/linux-add-user-to-group/
    - Add user : https://askubuntu.com/questions/410244/a-command-to-list-all-users-and-how-to-add-delete-modify-users\
    - Unix calculator : http://permissions-calculator.org/
    - umask 027 : https://blogs.gentoo.org/mgorny/2011/10/18/027-umask-a-compromise-between-security-and-simplicity/
    - The purpose of each permission : https://unix.stackexchange.com/questions/21251/execute-vs-read-bit-how-do-directory-permissions-in-linux-work
    - Deleting group to the user : https://unix.stackexchange.com/questions/29570/how-do-i-remove-a-user-from-a-group

----

### Chroot Jail (Limiting Directory Access to the User)

#### Setup SFTP Group and Service
- Note: 
    - This require ```apt-get install openssh-server```
    - Require ```port 22``` open.

1. Create sftpusers group.
    ```
    $ sudo groupadd sftpusers
    ```
2. Open sshd config file located in ```vim /etc/ssh/sshd_config``` and comment out the:
    ```
    #Subsystem sftp /usr/libexec/openssh/sftp-server
    ```
3. and set UsePAM ```yes```
    ```
    UsePAM yes
    ```
4. Open sshd config file again and add the snippet code below:
    ```
    #Enable sftp
    Subsystem sftp internal-sftp

    Match Group sftpusers
       # You can set here you custom directory that will the group can access | make sure that the pointed directory is set to owner root:root
       # to avoid "broken pipe" error when trying to access the username.
       ChrootDirectory "custom directory" 
       ForceCommand internal-sftp
       X11Forwarding no
       AllowTCPForwarding no
       # PasswordAuthentication yes
    ```
5. Restart ```ssh``` service.
    ```
    $ sudo service ssh restart
    ```
#### Create Users
- To create user that will include to the sftp group.
1. Create user, set the home directory of the user and disable the ssh access of the user.
    ```
    $ sudo useradd -g sftpusers -d "custom directory" -s (/sbin/nologin | /usr/sbin/nologin) "username"
    ```
    - The purpose of ```-g``` is to add group to that user.
    - The purpose of ```-d``` is to set the default or home directory of that user.
    - Takenote ```/sbin/nologin``` in other cases will not be available so check the ```/usr/sbin/nologin``` instead. 
    - The purpose of ```-s``` setting to ```/sbin/nologin | /usr/sbin/nologin``` is to disable the ssh access to that user.
- Reference:
    - Straight forward example how to limit access in a specific directory for user : https://www.vultr.com/docs/setup-sftp-only-user-accounts-on-ubuntu-14
    - https://www.digitalocean.com/community/questions/how-do-i-restrict-a-user-to-a-specific-directory
    - https://www.digitalocean.com/community/questions/trying-to-setup-a-sftp-user-with-limited-access
    - Solving the chroot required permission for the given directory : https://www.digitalocean.com/community/questions/chrootdirectory-access-and-privilege-problem
    - Solution for broken pipe error for Chroot when the given directory not owned by root : https://superuser.com/questions/394298/sftp-chroot-result-in-broken-pipe
    - Custom directory pointing for Chroot : https://www.tecmint.com/restrict-ssh-user-to-directory-using-chrooted-jail/

