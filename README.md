                                                                 # Linux_Command


 <hr>


 NOTE : LINUX IS A KERNAL NOT AN OS  ( KERNAL IS A MASTER PROGRAM WHICH MANAGE ALL THE OTHER PROGRAM ) 
 =============

 <hr>
 
 Basic Linux Commands
========================

**ROOT DIRECTORY**

```
Here are some common directories in the root directory of a Linux system and a brief description of their purposes:

/bin: Essential binary files (commands) required for system boot and repair.

/boot: Contains files necessary for the boot process, including the Linux kernel.

/dev: Device files, representing hardware devices and system peripherals.

/etc: Configuration files for the system and installed applications.

/home: Home directories for regular users.

/lib and /lib64: Libraries essential for the operation of system binaries.

/media: Mount points for removable media (e.g., USB drives, CD-ROMs).

/mnt: Temporary mount points for additional filesystems.

/opt: Optional software packages that are not part of the default system installation.

/proc: A virtual filesystem providing information about processes and kernel parameters.

/root: Home directory for the root user.

/run: Run-time variable data, including information about the running system.

/sbin: System binaries - essential binaries for system administration tasks.

/srv: Data for services provided by the system.

/sys: A virtual filesystem providing information about kernel and devices.

/tmp: Temporary files and directories that are deleted on system reboot.

/usr: User-related programs and data. This includes user binaries, libraries, documentation, etc.

/var: Variable data that changes during the course of normal system operation (e.g., logs, spool files).

```


<hr>

** FOR CREATING A USER **

  ```
  - sudo useradd username
  - sudo passwd username

 
  ```

  <hr>

   **LS**

   ```

- ls => ls -l ==> for listing down all the files and folders.
- ls -lh => for listing down all files in **HUMAN READABLE** Format.
- ls -lht => Sort By Recent Update.
- ls -lhti => include Inode Number also.
- ls -lhtia => (here a is hidden file)

```
<hr>

**PWD COMMANDS**

```
- pwd(present working directory) -> for know the present working directory.
- pwd -p => show The real Directory.

CD(CHANGE DIRECTORY)==>

- cd .. =>For Previous Path.
- cd -

```
<hr>

**mkdir**

```
mkdir - for making new directory.

```

<hr>

# What is root user ?

- > root user has all the previliaged for modifying the files and some other special permission . if # ==> So it is indicating root user  and $ other than root user .

- eg => [root@ip-172-31-10-37 ec2-user]#   (root user).   
- eg => [ec2-user@ip-172-31-10-37 ~]$  (other than root user).  Switch root user to other user => su username.

<hr>
[ec2-user@ip-172-31-10-37 ~]$ yum install httpd
Error: This command has to be run with superuser privileges (under the root user on most systems). 
 - This error indicates that this particular command can only run by root user .
 #Solution :--> now how to solve it 

 # first method.
 - You should switch to the root user and run the command. 

 # second method.
 -first write sudo then write the command. here sudo indicate that super user previlaged.

<hr>

 ** SU(SWITCH USER)**

 ```

- su -username => Switch to user Account(Home Path).
- sudo su => for switching to root user.

```
<hr>

**HISTORY COMMONDS**

```



```
<hr>

**READ THE FILE CONTENT IN LINUX**

- some Read files commands are cat, tac, nl, less, more, head, tail . let's explore one by one.
```
- cat filename.txt          # Display the contents of a file

- tac filename.txt          # Display the contents of a file in reverse order

- nl filename.txt           # Display the contents of a file with line numbers

- less filename.txt         # View the contents of a file with pagination

- more filename.txt         # Display the contents of a file page by page

- head -n 10 filename.txt   # Display the first 10 lines of a file

- tail -n 20 filename.txt   # Display the last 20 lines of a file

- head -n 35 filename.txt | tail -n 5   #This combination of head and tail prints the last 5 lines (tail -n 5) of the first 35 lines (head -n 35) from the file.


```

<hr>

**echo**

-The echo command in Linux is used to display text or messages to the terminal. 

```
  - Basic Text Output:  echo "Hello, Linux!"

  - Display Variable Content:  my_variable="World"   echo "Hello, $my_variable!"

  - Escape Characters: echo "This is a new line.\nThis is another line." (next line).

  - Overwrite : echo "overwrite this text " > output.txt.

  - Appending to a File: echo "Append this text to a file" >> output.txt.

  - Command Substitution: echo "The current date is $(date)"

   [[root@ip-172-31-10-37 ec2-user]# echo "The current date is $(date)"
    The current date is Wed Feb 14 20:25:10 UTC 2024 ]


```

<hr>

**NETWORK RELATED SOME EXTRA FACT**


# ifconfig -> cehck the IP address of VM . 

# set the hostname -> sudo hostnamectl set-hostname anjali 

# check the hostname -> hostname.

<hr>


** REMOVE(rm) / MOVE(mv) / Copy / rename Command **

```
# Remove a file
rm filename

# Remove a directory and its contents recursively
rm -r directoryname


# Move a file to a new location
mv oldfile newlocation/

# Rename a file
mv oldfilename newfilename

# Move a directory and its contents to a new location
mv olddirectory newlocation/

# Rename a directory
mv olddirectory newdirectory

# rm -rvf directoryname => remove directory.

# rm -rvf* => remove all directory.


# Copy a file to a new location
cp sourcefile destination/

# Copy a directory and its contents to a new location
cp -r sourcedirectory destination/



```






** SSH ( Secure Shell ) **

```

- ssh => it is a network protocol that is used for accessing the remote server .


# if we are accessing the machine through key then we have to write this commands .

- ssh -i keyname ec2-user@PUBLICIP ==> here i stand for identify private key file.

#  if password authentication is enabled then we have to write this command .
 - ssh ec2-user@PUBLICIP

```

<hr>


** LINUX COMMAND FOR APACHE WEBSERVER **

```

- yum install httpd -y ==>( To Install Apache WEB SERVER ) ....

- cd /var/www/html/ ==> inside this directory we have to placed the all our frontend code.

- wget downloadLink =>(we download the zip of our frontend code).

- unzip filename

- Notes : after unziping the code we need to copy all the files and paste into the above directory.(cd /var/www/html/).

- cp -rvf * /var/www/html/

- systemctl restart httpd

```

** LINUX COMMAND FOR FILE SYSTEM ** 

```
- df -h ==> It shows all the mounted volumes .

- lsblk / fdisk -l => it shows all the volumes mounted and unmounted .

# Now how to check volume is mounted or not .

- blkid ==> if we got uuid that's means the volume is mounted . 

```

# steps for mounting the volumes 

```

- step1 => first we have to format the volume. 
- step2 => we have to make a folder which is going to be mounted with the volume.
- step3 => mount that folder with volume.

 # commands 
 - mkfs.ext2 /dev/xvda1 => make sure to rename xvda1 to your volume name.

 - after formatting we have to make a folder
 - mkdir foldername

 - mount /dev/sdba1 /utkarsh/ ==> mounting done .
 - now whatever we are storing inside the utkarsh folder that is going to save in the that volume.

 # now if want to increase the size of volume then linux command for that is

- step 1 = > we have to know the type of file system. for this we have to run ====> blkid .
- step 2 => after knowing the file system we have to run the command for extending the size of volume . ==> resize2fs /dev/xvdf

- but this command is for if the type of file system is ext2 ext3 ext4 . and if the file system is xfs then the command is

- growpart /dev/xvda 1

- xfs_growfs /dev/xvda1


- By Default the type of file system is xfs.
   ```


<hr>

** DOCKER COMMAND FOR LINUX **

- docker build -t appname .
- docker tag appname dockerusername/appname
- docker push username/appname
- docker pull username/appname
- docker run -d -p port:prot username/appname

  <hr>


**LINUX COMMAND FOR EC2 INSTENCE ** 

- step 1 => sudo yum install docker  (docker info to check whether docker is install or not).
- step 2 -> sudo usermod -aG docker ec2-user
- step 3 -> reboot the system.
- step 4 -> sudo service docker start 
- docker pull username/appname
- docker run -d -p port:prot username/appname


<hr>












