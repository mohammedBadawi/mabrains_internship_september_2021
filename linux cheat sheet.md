## Getting Help
* **man [command]** : displays the manual page for the command.
  * /key word : to search the man page.
  * man -f [command] = whatis [command] :  It displays man pages that match, or partially match, a specific name and provide the section number.
  * man [_**sec_number**_] [command] : display the man page that located at the section with that number.
  * man -k [_**key_word**]_ : searches both the names and descriptions of the man pages for a keyword. 
* **whereis [command]**   : search for the location of a command or the man pages for a command.
* **locate [file/dir]**   : searches a database of all files and directories that were on the system when the database was created.
  * locate -c [file/dir]  : how many files match.
  * locate -b [file/dir]  : only includes listings that have the search term in the basename of the filename.
  * locate -b ["\file_dir]: this character limits the output to filenames that exactly match the term. 
* **info [command]**   : displays documentation for the command in a way different to the man command.
* **command --help** : provides basic information about the command.
## Navigating the Filesystem
* **pwd** : prints the current directory path
* **cd [path]** : change the current directory.
  * cd ~  : go to the current user directory (/home/usrname)
  * cd .. : got back one step in the path
  * cd .  : the current directory.
* **ls [OPTION]... [FILE]...**: list the contents of the directory
  * \ls      : to avoid using the aliasing for _**ls --color=auto**_
  * ls -a    : listing all files including the hidden files.
  * ls -l    : use the long list format.
  * ls -h    : use the human readable size format
  * ls -l -d : show the information of the current directory without its contents.
  * ls -R    : recursive listing.
  * ls -S    : sort by file sizes in descending order
  * ls -t    : sort by file editing time starting with the most recent file.
## Managing Files and Directories
* **#!/bin/sh** : Typed at the first line of the file to define the interpreter used
* **cp [source] [destination]** : copy the source file to the destination directory "only files"
  * cp -v : vorbose option to print output showing the steps of operation
  * cp -i : interactive options asks the user before overwriting
  * cp -n : means no overwrite for all files
  * cp -r : recursive copy means copy the whole directory structure. "copy files and directories"
  * cp sourcefile destination/filename : to give the file a new name
* **mv [source] [destination]** : remove the file from the original location and place it in the destination.
  * Like the cp command, the mv command provides the following options: -v, -i, -n
  * There is no -r option for mv command.
* **touch [filename]** : create a file
* **rm [filename]** : delete a file permanently
  * rm -i : ask before deleting
  * rm -r : delete the directory with all directories and files included
* **mkdir [dir_name]** : create a directory.
* **rmdir [dir_name]** : remove the directory only if it's empty
## Archiving and Compression
* **gzip file / gunzip file**   : compress/decompress the file using  **_Lempel-Ziv-Markov (LZMA)_** algorithm
* **bzip2 file / bunzip2 file** : compress/decompress the file using  **_Burrows-Wheeler_** algorithm (better compression, more cpu time)
* **xz file / unxz file**       : compress/decompress the file using  **_Lempel-Ziv-Markov (LZMA)_** algorithm
* **tar -c [-f ARCHIVE] [OPTIONS] [FILE...]**  : archive files into one file
  * tar -cz [-f ARCHIVE] [OPTIONS] [FILE...]   : compress the resulting file with gizp
  * tar -cj [-f ARCHIVE] [OPTIONS] [FILE...]   : compress the resulting file with bzip2
* **tar -t [-f ARCHIVE] [OPTIONS] [FILE...]**  : list the archived files
* **tar -x [-f ARCHIVE] [OPTIONS] [FILE...]**  : extract the archived files
  * tar -xz [-f ARCHIVE] [OPTIONS] [FILE...]** : extract the archived files after decompressing using gzip
  * tar -xj [-f ARCHIVE] [OPTIONS] [FILE...]** : extract the archived files after decompressing using bzip2
## Working With Text
* **cat [filename]** : view the file in the std output
* **less [filename]** : view the file using the less pager
  * Spacebar : 	Window forward
  * B	       : Window backward
  * Enter    :	Line forward
  * Q        :	Exit
  * H        :	Help 
* **head/tail [filename]** : view the first/last 10 lines from the file in the std output
  * head -5    : view the first lines
  * head -n 5  : view the first 5 lines
  * head -n -5 : view the whole file except the last 5 lines
  * tail -5    : view the last 5 lines
  * tail -n -5 : view the last 5 lines
  * tail -n 5  : view the last 5 lines
  * tail -n +5 : view the file from the line number 5 to the end
* **tail -f [filename]** : view the live file changes , ex: used in viewing the log files
* **standard streams**
  * STDIN  : standard input
  * STDOUT : standard output , stream/channel #1
  * STDERR : standard error  , stream/channel #2
  * echo "hello" > file.txt : redirect the STDOUT stream to the file (overwrite)
  * echo "hello" >> file.txt : redirect the STDOUT stream to the file and overwrite (append)
  * ls /ABC 2> file.txt     : redirect the STDERR stream to the file
  * ls /fake /etc/ppp &> all.txt : &> is used to direct both stream 1&2 to the file
  * ls /etc /fake > output.txt 2> error.txt : direct the stream 1 to output.txt and stream 2 to error.txt
  * tr 'a-z' 'A-Z' : tar command is used to translat a set of characters to another set of characters. In this case it's used to capitaize the word input from the STDIN.
* **sort [file]** : sort the lines of the file in alphabetical order.
  * sort -t: -k3 -n file.txt : -t: defines the field delimiter which is now : , -k3 means sort by the 3rd field , -n means numerical sort
  * sort -t, -k2 -k1n -k3 -r file.txt : defines the delimiter as ',' and sort by the 2nd field then the first field numerically then the third field and use reverse order for sorting.
* **wc file.txt** : count the number of lines,words and bytes.
  * wc -l : count the lines only
  * wc -w : count the words only
  * wc -c : count the bytes (characters) only
* **cut -d[delimiter] -f[columns numbers] [file name]** : extract the columns from the file using the defined delimiter
  * cut -d: -f1,5-7 mypasswd : extract columns number 1,5,6,7 from the mypasswd file using ':' as delimiter
* **cut -c[characters numbers] [file name]** : extract the columns of the defined characters from the file
  * ls -l | cut -c1-11,50- : pipline the output of the ls command to the cut command to extract the columns of the first 11 characters and from 50 to the end.
* **grep [text] [file]** : find the linein the specified file that contain the specified text.
  * grep -c [text] [file] : prints the number of lines that contain the specified text.
  * grep -v [text] [file] : finds the lines that don't contain the specefied text.
  * grep -n [text] [file] : adds the lines numbering.
  * grep -i [text] [file] : ignores the case (capitalization) distinctions.
  * grep -w [text] [file] : only returns lines which contain matches that form whole words.
  * grep -q [text] [file] : run in the quit mode (if string is found return 0 otherwise return 1) and this value is not printed. We can see it using _**echo $0**_
## Basic Scripting
* **nano editor commands**
  * Ctrl + W	search the document
  * Ctrl + W, then Control + R	search and replace
  * Ctrl + G	show all the commands possible
  * Ctrl + Y/V	page up / down
  * Ctrl + C	show the current position in the file and the file’s size
* **Variables**
  * myvar="Hello"
  * echo $myvar prints the value of the variable
  * myvar=$1 this means frist argument passed to the script
  * mypath=\`pwd\` this backticks is used to run the command then pass the output to the variable
  * echo $0 this prints the status of the last command , 0 means successful otherwise means failed
## Understanding Computer Hardware
* **arch** : view the processor architecture (64 or 32)
* **lscpu** : view more information concerning the cpu
* **free** :  view the amount of RAM in your system, including the swap space.
  * free -m : force the output to be rounded to the nearest megabyte (MB)
  * free -g : force the output to be rounded to the nearest gegabyte (GB)
  * free -s [seconds] : Update the output every a number of seconds
* **lspci** : view all of the devices connected by the PCI bus
* **lsusb** : display the devices connected to the system via USB
* **fdisk** : display information about the partitions
# Where Data is Stored
* **pstree** : view the processes family tree of parent and child couplings.
* **ps** : provides a snapshot of the processes running at the instant the command is executed.
* **top** : the top command has a dynamic, screen-based interface that regularly updates the output of running processes.
  * press H to view the full list.
  * press K to terminate the runaway process.
  * press R to adjust the process priority
* **dmesg** : view the kernel ring buffer, which holds a large number of messages that are generated by the kernel.
* **dpkg -L packagename** : get the list of file locations. 
# Network Configuration
* **ifdown eth0** : The widely accepted method of making changes to a network interface is to take the interface down using this command, then make the desired changes to the configuration file, and then bring the interface back up into sevice.
* **ifup eth0** : bring th interface back up into service.
* **service network restart** : restart the system’s networking entirely
* **host [url]** : find the associated ip address
* **ifconfig** : Display network configuration information.
* **ip [OPTIONS] OBJECT COMMAND** : Display network configuration information.
  * ip addr show : show the type of interface, protocols, hardware and IP addresses, network masks and various other information about each of the active interfaces on the system.
* **route**  :   view a table that describes where network packages are sent (routing table).
  * route -n :  display this information with numeric data only. (default gateway is 0.0.0.0)
* **ping** : used to determine if another machine is reachable.
  * ping -c [number] : determine the number of packets to be sent.
* **netstat** : provides a large amount of network information. It can be used to display information about network connections as well as display the routing table similar to the route command.
  * netstat -i : display statistics regarding network traffic (TX-OK , TX-ERR)
  * netstat -r : display routing information 
  * netstat -tln : To see a list of all currently open ports (In the previous example, -t stands for TCP, -l stands for listening (which ports are listening) and -n stands for show numbers, not names.)
* **ss** : show socket statistics and supports all the major packet and socket types.
* **dig** : tests the functionality of the DNS server that your host is using.
* **ssh** : allows you to connect to another machine across the network, log in and then perform tasks on the remote machine.
  * ssh [username@hostname] : to connect using a different username from the one you currently using.
  * exit : to return to the local machine
## System and User Security
* **su [options] [username]** : allows you to run a shell as a different user (switching to the root user, switch to other users as well).
  * If the username is not specified, the su command login to the root by default. so, all the following commands are equivalent
    * su -
    * su -l
    * su --login
    * su - root
* **sudo [options] command** : It allows users to execute commands as another user. Similar to the su command, the root user is assumed by default.
* **id [options] username**  : used to print user and group information for a specified user.
  * id -g : To print only the user's primary group.
  * id -G : To print all the groups that a user belongs to.
* **who** : displays a list of users who are currently logged into the system
* **w**:  provides a more detailed list about the users currently on the system than the who command. It also provides a summary of the system status.
* **last** : reads the entire login history from the /var/log/wtmp file and displays all logins and reboot records by default.
## Creating Users and Groups
* **groupadd [group_name]** : executed by the root user to create a group.
  * gropuadd -g[GID] [group_name] : to specify a group id, otherwise the command will automaticallu specify GID by looking at **/etc/group** and choose a number higher by one that the highest GID.
  * groupadd -r [group_name] : assigns the GID to a number lower than the standard (1000 for debian , 500 for redhat).
* **groupmod** : groupmod command can be used to either change the group name or GID.
  * groupmod -n [new_name] [old_name] : change the group name. (will not affect the group members or the files access as the system define them by th GID).
  * groupmod -g [new_GID] [group_name] : change the GID. (all members and files that were associated with that group will no longer be associated with that group.Instead, these files will be owned by a GID only).
  * find / -nogroup : To search for all files that are owned by just a GID (not associated with a group name) use the -nogroup option of the find command.
* **groupdel [group_name]** : delete the group. Only supplemental groups can be deleted, so if any group that is the primary group for any user, it cannot be deleted.
* **To change the default values regarding creating a new user we have two options**
   1. Manipulate the **etc/default/useradd** file
   2. To use the **useradd** command with **-D** option. and this is the recommended method.
* **useradd -D** : View the default values of the /etc/default/useradd file.
  * useradd -D -g [primary group id] : in distributions that don't set the UPG to the UID and put a default value, we can change that value.
  * useradd -D -b [home address] : to use a different base directory group than the default when creating a new user account.
  * useradd -D -f [no. days] :  to use a different INACTIVE value (number of days after the pass expires that the account is disabled).
  * useradd -D -e [no. days] : to change the default expiration date of the account.
  * useradd -D -s [shell path] : to use a different login shell than the default when creating a new user account.
  * useradd -D -k [skeleton directory] : to use a different SKEL directory than the default when creating a new user account.

* **useradd [user_name]** : creats a new user account.
  * useradd -u [UID] [user_name]  : allows you to specify the UID number. (above 1000 and not nfsnobody (65534)).
  * useradd -g [primary group name or ID] [user_name]  : specify the user's primary group
  * useradd -G [sub groups id list] [user_name]  : specify the user's supplementary groups
  * useradd -b [base-directory] [user_name]  : specify a different base directory under which the user's home directory is created.
  * useradd -M [user_name] : tell the command not to make a home directory even if CREATE_HOME is set to yes in the /etc/login.defs file.
  * useradd -m [home_directory] [user_name]  : used to make the home directory.
  * useradd -d [home_directory] [user_name]  : used to specify existing or new home directory.
  * useradd -mK [skeleton directory] [user_name]  : specify a new skeleton directory rather that /etc/skel.
  * useradd -s [bash directory] [user_name] : specify another login shell.
  * useradd -c [comment] [user_name] : specify a value for the General Electric Comprehensive Operating System (GECOS) field.
* **usermod** : modify an existing user account information.
  * usermod -c [comment] [user_name] : Sets the value of the GECOS or comment field to COMMENT.
  * usermod -d [HOME_DIR] [user_name] : Sets HOME_DIR as a new home directory for the user.
  * usermod -E [EXPIRE_DATE] [user_name] : Set account expiration date to EXPIRE_DATE.
  * usermod -f [INACTIVE] [user_name] : Set account to permit login for INACTIVE days after password expires.
  * usermod -g [GROUP] [user_name] : Set GROUP as the primary group.
  * usermod -G [GROUPS] [user_name] : Set supplementary groups to a list specified in GROUPS.
  * usermod -a [user_name] : Append the user's supplemental groups with those specified by the -G option.
  * usermod -l [NEW_LOGIN] [user_name] : change the user's login name
  * usermod -L [user_name] : lock the user account.
  * usermod -s [SHELL] [user_name] : Specify the login shell for the account.
  * usermod -u [NEW_UID] [user_name] : Specify the user's UID to be NEW_UID.
  * usermod -U [user_name] : unlock the user account.
* **userdel [user_name]** : delete the user account without deleting its home directory, mail spool or files.
  * userdel -r [user_name] : delete the user account and his home, mail spool, and files.
## Ownership and Permission
* **id** : displays the UID and user account name of the current user followed by the GID and group name of the primary group and the GIDs and group names of all group memberships.
* **newgrp [grp_name]** : change your current primary group to change the group owner of the file that you will create.
  * exit : to close the shell of the newgrp command and go back to your original primary group.
* **groups** : show the groups ypu are belong to.
* **usermod -g groupname username** : To change the user group permanentally.
* **chgrp [group_name] [file_name]** : to change the owner group of an existing file to another group.(the root user can change to any group, but any user chnage to only the groups that he belongs to)
  * chgrp -r : to change the owner group of all the files in a directory structure.
* **chown user /path/to/file** : to change the user owner of a file.
  * chown user:group /path/to/file : chnage the user and group owner (only the root user can do this).
  * chown :group /path/to/file : to chnage the ower group (only the root user can do this).
* **chmod new_permission file_name** : change permissions on files and directories.
  * u	user owner
  * g	group owner
  * o	others
  * a	all (user owner, group owner, and others)
    * (+)	add
    * (-)	remove
    * (=)	equals
      * r	read
      * w	write
      * x	execute
## Special Directories and Files
* **setuid** : setuid permission is set on an executable binary file (a program) the binary file is run as the owner of the file, not as the user who executed it.
  * chmod u+s file : to add setuid permission symbolically.
  * To add the setuid permission numerically, add 4000 to the file's existing permissions 
  * chmod u-s file : to remove setuid permission symbolically.
  * To remove the setuid permission numerically, subtract 4000 from the file's existing permissions.
* **setfig on the files** : it allows a user to run an executable binary file in a manner that provides them additional (temporary) group access. The system allows the user running the command to effectively belong to the group that owns the file, but only in the setgid program.
* **setfig on the directories** : the setgid permission causes files created in the directory to be owned by the group that owns the directory automatically, not the primary group of the file owner.
  * chmod g+s <file|directory> : to add setgid symbolically.
  * To add the setgid permission numerically, add 2000 to the file's existing permissions
  * chmod g-s <file|directory> : to remove the setgid permission symbolically.
  * To remove the setgid permission numerically, subtract 2000 to the file's existing permissions.
* **sticky bit** : The sticky bit permission is used to prevent other users from deleting files that they do not own in a shared directory.
  * chmod o+t <directory> : to add the stick bit permission symbolically.
  * To add the sticky bit permission numerically, add 1000 to the file's existing permissions.
  * chmod o-t <directory> : to remove the stick bit permission symbolically.
  * To remove the sticky bit permission numerically, subtract 1000 to the file's existing permissions.
* **ls -i** : displays the inode number of a file.
* **ln [target file] [link file]** : to create a hard link to an existing file (a file that holds the same inode number).
* **ln -s target link_name** : to create a symbolic link.
* **find / -inum [inum]** : to search for files that have the same inum (hard links).
 
