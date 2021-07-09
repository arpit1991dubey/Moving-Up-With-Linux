# Moving-Up-With-Linux

Moving up with linux:

Basic Introduction-:

As windows operating system is based on NT kernal, Linux operating systems are based out of LINUX kernal. 
A kernal is a very Important part of OS, it performs functionalities like process managment,. memory managment, filesystem managment , etc.
Linux kernal was developed by Linus Torvalds.

Important points-:

* Linux distribution  is an operating system based on the Linux kernel and a package management system.
* Linux kernal is monolithic in nature.
* System calls are used to interact with linux kernal space.
* Kernel code can only be executed in the kernel mode. Non-kernel code is executed in the user mode.
* Device drivers are used to communicate with the hardware devices.

Important Concepts-:

#Shell vs Terminal#

* Shell is a program that takes commands from the users and gives them to the operating system for processing. 
Shell is an example of a CLI(command line interface). Bash is one of the most popular shell programs available on Linux servers. Other popular shell programs are zsh, ksh and tcsh.

* Terminal is a program that opens a window and lets you interact with the shell. Some popular examples of terminals are gnome-terminal, xterm, konsole etc.

* Linux users do use the terms shell, terminal, prompt, console etc. interchangeably. In simple terms, these all refer to a way of taking commands from the user.

#Command line basics#

~ Commands for Navigating the File System

There are three basic commands which are used frequently to navigate the file system:

 >ls
ls (list files and directories)
The ls command is used to list the contents of a directory. It will list down all the files and folders present in the given directory.

 >pwd
pwd (print working directory)
At any given moment of time, we will be standing in a certain directory. To get the name of the directory in which we are standing, we can use the pwd command in linux.

 >cd
cd (change directory)
The cd command can be used to change the working directory. Using the command, you can move from one directory to another.


~ Commands for Manipulating Files

There are four basic commands which are used frequently to manipulate files:

 >touch
touch (create new file)
The touch command can be used to create an empty new file. This command is very useful for many other purposes but we will discuss the simplest use case of creating a new file.
 
 >mkdir
mkdir (create new directories)
The mkdir command is used to create directories.You can use ls command to verify that the new directory is created.

 >cp
cp (copy files and directories)
The cp command is used to copy files and directories from one location to another. Do note that the cp command doesn't do any change to the original files or directories. The original files or directories and their copy both co-exist after running cp command successfully.

 >mv
mv (move files and directories)
The mv command can either be used to move files or directories from one location to another or it can be used to rename files or directories. Do note that moving files and copying them are very different. When you move the files or directories, the original copy is lost.
 
 >rm
rm (delete files and directories)
The rm command can be used to delete files and directories. It is very important to note that this command permanently deletes the files and directories. It's almost impossible to recover these files and directories once you have executed rm command on them successfully. Do run this command with care.

~ Commands for Viewing Files

There are three basic commands which are used frequently to view the files:

 >cat
The most simplest use of cat command is to print the contents of the file on your output screen. This command is very useful and can be used for many other purposes. We will study about other use cases later.

 >head
The head command displays the first 10 lines of the file by default. We can include additional arguments to display as many lines as we want from the top.

 >tail
The tail command displays the last 10 lines of the file by default. We can include additional arguments to display as many lines as we want from the end of the file.


Echo Command in Linux - The echo command is one of the simplest commands that is used in the shell. This command is equivalent to what we have in other programming languages.

Text Processing Commands

In the previous section, we learned how to view the content of a file. In many cases, we will be interested in performing the below operations:

 - Print only the lines which contain a particular word(s)

 - Replace a particular word with another word in a file

 - Sort the lines in a particular order

There are three basic commands which are used frequently to process texts:

  >grep
The grep command in its simplest form can be used to search particular words in a text file. It will display all the lines in a file that contains a particular input. The word we want to search is provided as an input to the grep command.

General syntax of using grep command:
grep <word_to_search> <file_name>
  
  >sed
The sed command in its simplest form can be used to replace a text in a file.

General syntax of using the sed command for replacement:
sed 's/<text_to_replace>/<replacement_text>/' <file_name>

  >sort
The sort command can be used to sort the input provided to it as an argument. By default, it will sort in increasing order.


Till now, we have displayed all the output on the screen which is the standard output.
We can use some special operators to redirect the output of the command to files or even to the input of other commands. I/O redirection is a very powerful feature.
ls > output.txt

we can also pass the output of cat command as an input to grep command using pipe(|) operator.
cat numbers.txt | grep "3"



***Server Administration***

An operating system is considered as multi-user if it allows multiple people/users to use a computer and not affect each other's files and preferences. 
Linux based operating systems are multi-user in nature as it allows multiple users to access the system at the same time. 
A typical computer will only have one keyboard and monitor but multiple users can log in via SSH if the computer is connected to the network.
We will cover more about SSH later.

As a server administrator, we are mostly concerned with the Linux servers which are physically present at a very large distance from us. 
We can connect to these servers with the help of remote login methods like SSH.

Since Linux supports multiple users, we need to have a method which can protect the users from each other. One user should not be able to access and modify files of other users.

# User/Group Management

* Users in Linux has an associated user ID called UID attached to them.

* Users also has a home directory and a login shell associated with them.

* A group is a collection of one or more users. A group makes it easier to share permissions among a group of users.

* Each group has a group ID called GID associated with it.

>id command
id command can be used to find the uid and gid associated with an user. It also lists down the groups to which the user belongs to.
The uid and gid associated with the root user is 0. 

/etc/passwd 	Stores the user name, the uid, the gid, the home directory, the login shell etc

/etc/shadow 	Stores the password associated with the users.

/etc/group 	Stores information about different groups on the system.


# Important commands for managing users

Some of the commands which are used frequently to manage users/groups on Linux are following:

* useradd - Creates a new user
useradd
The useradd command adds a new user in Linux.
We will create a new user 'shivam'. We will also verify that the user has been created by tailing the /etc/passwd file. The uid and gid are 1000 for the newly created user. 
The home directory assigned to the user is /home/shivam and the login shell assigned is /bin/bash. Do note that the user home directory and login shell can be modified later on.


* passwd - Adds or modifies passwords for a user
passwd
The passwd command is used to create or modify passwords for a user.

* usermod - Modifies attributes of an user
usermod
The usermod command is used to modify the attributes of an user like the home directory or the shell.

* userdel - Deletes an user
userdel
The userdel command is used to remove a user on Linux. Once we remove a user, all the information related to that user will be removed.
The su command can be used to switch users in Linux.


# File Permissions

On a Linux operating system, each file and directory is assigned access permissions for the owner of the file, the members of a group of related users and everybody else. 
This is to make sure that one user is not allowed to access the files and resources of another user.

To see the permissions of a file, we can use the ls command. Let's look at the permissions of /etc/passwd file.

>Chmod command
The chmod command is used to modify files and directories permissions in Linux.

>Chown command
The chown command is used to change the owner of files or directories in Linux.

>Chgrp command
The chgrp command can be used to change the group ownership of files or directories in Linux. 

>SSH Command
The ssh command is used for logging into the remote systems, transfer files between systems and for executing commands on a remote machine.
SSH stands for secure shell and is used to provide an encrypted secured connection between two hosts over an insecure network like the internet.

# Passwordless Authentication Using SSH

Using this method, we can ssh into hosts without entering the password. This method is also useful when we want some scripts to perform ssh-related tasks.

> Steps for setting up a passwordless authentication with a remote host:

    Generating public-private key pair

    If we already have a key pair stored in \~/.ssh directory, we will not need to generate keys again.

    Install openssh package which contains all the commands related to ssh.

    Generate a key pair using the ssh-keygen command. One can choose the default values for all prompts.

    After running the ssh-keygen command successfully, we should see two keys present in the \~/.ssh directory. Id_rsa is the private key and id_rsa.pub is the public key.
    Do note that the private key can only be read and modified by you.

    Transferring the public key to the remote host

    There are multiple ways to transfer the public key to the remote server. We will look at one of the most common ways of doing it using the ssh-id-copy command.

    Install the openssh-clients package to use ssh-id-copy command.

    Use the ssh-id-copy command to copy your public key to the remote host.

    Now, ssh into the remote host using the password authentication.

    Our public key should be there in \~/.ssh/authorized_keys now.

    \~/.ssh/authorized_key contains a list of public keys. The users associated with these public keys have the ssh access into the remote host.

How to run commands on a remote host ?

General syntax: ssh \<user>@\<hostname/hostip> \<command>

How to transfer files from one host to another host ?

General syntax: scp \<source> \<destination>

# Package Management

Package management is the process of installing and managing software on the system. We can install the packages which we require from the Linux package distributor.
Different distributors use different packaging systems.
DNF is the successor to YUM which is now used in Fedora for installing and managing packages. DNF may replace YUM in the future on all RPM based Linux distributions.

# Process Management

In this section, we will study about some useful commands that can be used to monitor the processes on Linux systems.

>top
The top command is used to show information about Linux processes running on the system in real time. It also shows a summary of the system information.

# Memory Management

In this section, we will study about some useful commands that can be used to view information about the system memory.

>free
The free command is used to display the memory usage of the system. 
The command displays the total free and used space available in the RAM along with space occupied by the caches/buffers.

>vmstat
The vmstat command can be used to display the memory usage along with additional information about io and cpu usage.

# Checking Disk Space

In this section, we will study about some useful commands that can be used to view disk space on Linux.

>df (disk free)
The df command is used to display the free and available space for each mounted file system.

>du (disk usage)
The du command is used to display disk usage of files and directories on the system.

- Daemons
* A computer program that runs as a background process is called a daemon. Traditionally, the name of daemon processes ended with d - sshd, httpd etc.
We cannot interact with a daemon process as they run in the background.
Services and daemons are used interchangeably most of the time.
- Systemd
* Systemd is a system and service manager for Linux operating systems.
Systemd units are the building blocks of systemd. These units are represented by unit configuration files.

- Logs
* In this section, we will talk about some important files and directories which can be very useful for viewing system logs and applications logs in Linux.
These logs can be very useful when you are troubleshooting on the system.
/var/log/*- Stores logs related to daemon proceses along with system logs.
>dmesg - Shows kernal logs
