# Terminal Commands
a general and minimalised list of useful day-to-day commands for Linux Debian

## Contents
- [Nano](#nano)
    + [Open File](#open-file)
    + [Save File](#save-file)
    + [Search](#search)
- [Debian](#debian)
  * [User Management](#user-management)
    + [Create User](#create-user)
    + [Change Username](#change-username)
    + [Set User Password ](#set-user-password)
    + [Delete User](#delete-user)
    + [Force Delete User](#force-delete-user)
    + [Delete user and associated directories](#delete-user-and-associated-directories)
    + [Kill user processes](#Kill-user-processes)
    + [Get all user groups](#get-all-user-groups)
    + [Set user directory and permissions](#set-user-directory-and-permissions)
    + [Delete Groups](#delete-groups)
    + [User groups](#user-groups)
    + [Add User to group](#add-user-to-group)
    + [Remove User from group](#remove-user-from-group)
  * [Directory Management](#directory-management)
    + [Make Directory](#make-directory)
    + [Remove Directory](#remove-directory)
    + [Remove Directory and Contents](#remove-directory-and-contents)
    + [Change Permissions](#change-permissions)
    + [Change Ownership](#change-ownership)
    + [Change Group ownership](#change-group-ownership)
  * [Debug](#debug)
    + [Locate active process](#locate-active-process)
  * [Kill Certbot Process](#kill-certbot-process)
    + [Find active Certbot processes](#find-active-certbot-processes)
    + [Kill Certbot processes](#kill-certbot-processes)
  * [Setup and Configuration](#setup-and-configuration) 
    + [Change resolution](#change-resolution) 

## Nano
#### Open File
```terminal
$ sudo nano /directory/filename.ext
```

#### Save File
```terminal
CTRL + S
```

#### Search
```terminal
CTRL + W
```

## Debian

### User Management

#### Create User
````terminal
sudo useradd username
````

#### Change username
````
usermod -l new-username current-username
````

##### Set user password
````terminal
sudo passwd username
````

##### Set user directory and permissions
```terminal
sudo chown username /homeusername
sudo chmod u+rwx /home/username
sudo chmod -R go-w /home/username
sudo chmod 755 /home/username
````

#### Delete user
```terminal
sudo userdel username
```

#### Force Delete User
````terminal
sudo userdel -f username
````

##### Delete user and associated directories
```terminal
sudo userdel -r username
```

#### Kill user processes
```terminal
sudo killall -u username
```


#### Get all user groups
```terminal
$ sudo getent group
```

#### Delete Groups
```terminal
$ sudo groupdel groupName
```

#### User groups
```terminal
$ sudo groups username
```

#### Add User to group
```terminal
$ sudo usermod -a -G groupname username
```

#### Remove User from group
```terminal
$ sudo gpasswd –delete username group
```

### Directory Management
#### Make Directory
```terminal
$ sudo mkdir /path/of/directory/folder1
```

#### Remove Directory
```terminal
$ sudo rmdir /path/of/directory/folder1
```

#### Remove Directory and Contents
```terminal
$ sudo rm -r /path/of/directory/folder1
```

#### Change Permissions
```terminal
$ sudo chmod 775 /path/of/directory/folder1
```

#### Change Ownership
```terminal
$ sudo chown username:username  /path/of/directory/folder1
```

#### Change Group ownership
```terminal
$ sudo chgrp userGroupName -R /path/of/directory
```


### Debug
#### Locate active process
Search for Port 8080 processes
```terminal
$ sudo ps -ef | grep ':8080'
```

#### Kill Certbot Process
Error: Another instance of Certbot is already running.
Find active Certbot processes
````terminal
$ ps -ef | grep certbot
````
 
#### Kill Certbot processes
Note: The process id shown in this image may be different from your own.
````terminal
$ sudo kill 47666
````

## Setup and Configuration
### Change Resolution
Note: in Hypervisors such as Hyper-V, the resolution of the Virtual machine may be lower than your screens discplay, we can increase / decrease with the following processes.

First, open the grub config file then search: GRUB_CMDLINE_LINUX_DEFAULT
```terminal
$ sudo nano /etc/default/grub
```
You can change the resolution to your requirements.
- Fullscreen : 1920x1080
- Windowed : 1680x1050

Make the following changes, save and close the file.
```nano
GRUB_CMDLINE_LINUX_DEFAULT="quiet video=hyperv_fb:1920x1080"
```
update Grub and restart
```
sudo update-grub
sudo reboot
```
If your Hyper-V virtual machine failed to load, you may need to restart the virtual machine.


