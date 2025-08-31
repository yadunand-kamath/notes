
#bash 

## Contents :-

#### [[#3.01 - Linux File System]]
#### [[#3.02 - Filtering Content]]
#### [[#3.03 - Managing Directories and Files]]
#### [[#3.04 - Authenticate and Authorize Users]]
####

---

#fhs

## 3.01 - Linux File System

- **Argument** - specific information needed by a command 
- **FHS** (***Filesystem Hierarchy Standard***) - component of Linux OS that organizes data 

### Standard FHS Directories

- **Root Directory** (`/`): highest level directory represented by a forward slash.
- `/home`: each user in the system gets their own home directory. Also represented as tilde (`~`)
- `/bin`: stands for “binary” and contains binary files and other executables. Executables are files that contain a series of commands a computer needs to follow to run programs and perform other functions.
- `/etc`: stores the system’s configuration files.
- `/tmp`: stores many temporary files. The /tmp directory is commonly used by attackers because anyone in the system can modify data in these files.
- `/mnt`: stands for “mount” and stores media, such as USB drives and hard drives.

***Pro Tip***: You can use the man hier command to learn more about the FHS and its standard directories.

- **Absolute File Path** - full file path, which starts from the root.
- **Relative File Path** - file path that starts from a user's current directory.
***Note***: Relative file paths can use a dot (.) to represent the current directory, or two dots (..) to represent the parent of the current directory.

### Commands

- `pwd`: prints the working directory to the screen/returns the directory that you’re currently in. The output gives you the absolute path to this directory. 
- `man`: displays information on other commands and how they work.
- `whatis`: displays a description of a command on a single line.
- `apropos`: searches the manual page description for a specified string.
- `whoami`: returns the username of the current user.
- `ls`: displays the names of the files and directories in the current working directory.
- `cd`: navigates between directories. Use the relative file path and enter cd .. to go up one level in the file structure.
- `cat`: displays the content of a file. 
- `head`: displays just the beginning of a file, by default 10 lines. Useful when you want to know the basic contents of a file but don’t need the full contents. The number of lines returned by head can be specified by including -n.
- `tail`: does the opposite of head. Used to display just the end of a file, by default 10 lines. 
***Pro Tip***: You can use tail to read the most recent information in a log file.
- `less`: returns the content of a file one page at a time.
	Once you’ve accessed your content with the less command, you can use several keyboard controls to move through the file:
	- `Space bar`: Move forward one page
	- `b`: Move back one page
	- `Down arrow`: Move forward one line
	- `Up arrow`: Move back one line
	- `q`: Quit and return to the previous terminal window

---

#grep #piping

## 3.02 - Filtering Content 

**Filtering** is selecting data that match a certain condition.

### grep

- grep command searches a specified file and returns all lines in the file containing a specified string. 
- It commonly takes two arguments: a specific string to search for and a specific file to search through.
- For example, entering grep OS updates.txt returns all lines containing OS in the updates.txt file.

### Piping

- The pipe command is accessed using the pipe character (|). 
- Piping sends the standard output of one command as standard input to another command for further processing. As a reminder, standard output is information returned by the OS through the shell, and standard input is information received by the OS via the command line. 
- When used with grep, the pipe can help you find directories and files containing a specific word in their names. 

Note: Piping is a general form of redirection in Linux and can be used for multiple tasks other than filtering. You can think of piping as a general tool that you can use whenever you want the output of one command to become the input of another command.

### find

- The find command searches for directories and files that meet specified criteria. 
- We can search for files and directories that:
	- Contain a specific string in the name,
	- Are a certain file size, or
	- Were last modified within a certain time frame.
- When using find, the first argument after find indicates where to start searching. After this first argument, you need to indicate your criteria for the search. If you don’t include a specific search criteria with your second argument, your search will likely return a lot of directories and files. 
- Specifying criteria involves options. Options modify the behavior of a command and commonly begin with a hyphen (-). 
- For example, entering find /home/analyst/projects searches for everything starting at the projects directory. 

#### -name and -iname

- One key criteria analysts might use with find is to find file or directory names that contain a specific string. The specific string you’re searching for must be entered in quotes after the -name or -iname options. 
- The difference between these two options is that -name is case-sensitive, and -iname is not. 
- For example, you might want to find all files in the projects directory that contain the word “log” in the file name. To do this, you’d enter find /home/analyst/projects -name "*log*". You could also enter find /home/analyst/projects -iname "*log*".
- In these examples, the output would be all files in the projects directory that contain log surrounded by zero or more characters. The "*log*" portion of the command is the search criteria that indicates to search for the string “log”. When -name is the option, files with names that include Log or LOG, for example, wouldn’t be returned because this option is case-sensitive. However, they would be returned when -iname is the option.

***Note***: An asterisk (*) is used as a wildcard to represent zero or more unknown characters.

#### -mtime

- Security analysts might also use find to find files or directories last modified within a certain time frame. The -mtime option can be used for this search.
- For example, entering find /home/analyst/projects -mtime -3 returns all files and directories in the projects directory that have been modified within the past three days. 
- The -mtime option search is based on days, so entering -mtime +1 indicates all files or directories last modified more than one day ago, and entering -mtime -1 indicates all files or directories last modified less than one day ago. 

***Note***: The option -mmin can be used instead of -mtime if you want to base the search on minutes rather than days.

---

## 3.03 - Managing Directories and Files 

### Creating and modifying directories

1. **mkdir**
	- The mkdir command creates a new directory. The new directory can either be provided  as the absolute file path, which starts from the root, or as a relative file path, which starts from your current directory.

***Pro Tip***: You can use the ls command to confirm the new directory was added.

2. **rmdir**
	- The rmdir command removes, or deletes, a directory. 
	
***Note***: The rmdir command cannot delete directories with files or subdirectories inside.

### Creating and modifying files

1. **touch** 
	- The touch command creates a new file. 
	- This file won’t have any content inside. 

2. **rm**
	- The rm command removes, or deletes, a file. 
	- This command should be used carefully because it’s not easy to recover files deleted with rm. 

***Pro Tip***: You can verify that permissions.txt was successfully created or removed by entering ls.

3. **mv and cp**
	- The mv command moves a file or directory to a new location, and the cp command copies a file or directory into a new location. 
	- The first argument after mv or cp is the file or directory you want to move or copy, and the second argument is the location you want to move or copy it to.
	- Moving a file removes the file from its original location. However, copying a file doesn’t remove it from its original location. 
	
***Note***: The mv command can also be used to rename files. To rename a file, pass the new name in as the second argument instead of the new location. 

### nano text editor

- nano is a command-line file editor that is available by default in many Linux distributions. 
- To open an existing file in nano from the directory that contains it, enter nano followed by the file name. 
- A new file can also be created in nano by entering nano followed by a new file name. 
- Since there isn't an auto-saving feature in nano, it’s important to save the work before exiting. To save a file in nano, use the keyboard shortcut Ctrl + O. You’ll be prompted to confirm the file name before saving. 
- To exit out of nano, use the keyboard shortcut Ctrl + X.

***Note***: Vim and Emacs are also popular command-line text editors.

### Standard output redirection

- Piping sends the standard output of one command as standard input to another command for further processing. It uses the pipe character (|). 
- In addition to the pipe (|), you can also use the right angle bracket (>) and double right angle bracket (>>) operators to redirect standard output.
- When used with echo, the > and >> operators can be used to send the output of echo to a specified file rather than the screen. 
- The difference between the two is that > overwrites your existing file, and >> adds your content to the end of the existing file instead of overwriting it. The > operator should be used carefully, because it’s not easy to recover overwritten files.

***Note***: Both the > and >> operators will create a new file if one doesn’t already exist with your specified name.

---

#permissions

## 3.04 - Authenticate and Authorize Users

- **Permissions** - type of access granted for a file or directory
- **Authorization** - concept of granting access to specific resources in a a system

### Types of Permissions

In Linux, permissions are represented with a 10-character string. Permissions include:

- **read**: for files, this is the ability to read the file contents; for directories, this is the ability to read all contents in the directory including both files and subdirectories
- **write**: for files, this is the ability to make modifications on the file contents; for directories, this is the ability to create new files in the directory
- **execute**: for files, this is the ability to execute the file if it’s a program; for directories, this is the ability to enter the directory and access its files

These permissions are given to these types of owners:

- **user**: the owner of the file
- **group**: a larger group that the owner is a part of
- **other**: all other users on the system

### Viewing Permissions

There are additional options you can add to the ls command to make your command more specific. Some of these options provide details about permissions. Here are a few important ls options for security analysts:

- `ls -a`: Displays hidden files. Hidden files start with a period (.) at the beginning.
- `ls -l`: Displays permissions to files and directories. Also displays other additional information, including owner name, group, file size, and the time of last modification.
- `ls -la`: Displays permissions to files and directories, including hidden files. This is a combination of the other two options.

### Changing permissions

The **principle of least privilege** is the concept of granting only the minimal access and authorization required to complete a task or function. In other words, users should not have privileges that are beyond what is necessary. Not following the principle of least privilege can create security risks.

The chmod  command can help you manage this authorization. The chmod command changes permissions on files and directories.

#### Using chmod

- The chmod command requires two arguments. 
- The first argument indicates how to change permissions, and the second argument indicates the file or directory that you want to change permissions for.  

For example, the following command would add all permissions to login_sessions.txt:
`chmod u+rwx,g+rwx,o+rwx login_sessions.txt`

To take all the permissions away, use:
`chmod u-rwx,g-rwx,o-rwx login_sessions.txt`

- Another way to assign these permissions is to use the equals sign (=) in this first argument. Using = with chmod sets, or assigns, the permissions exactly as specified. 

For example, the following command would set read permissions for login_sessions.txt for user, group, and other:
`chmod u=r,g=r,o=r login_sessions.txt`

This command overwrites existing permissions. For instance, if the user previously had write permissions, these write permissions are removed after you specify only read permissions with =. 

### Users

- **Root User (superuser)** - a user with elevated privileges to modify the system. Not recommended to login as root user.
- `sudo`: super user do temporarily grants elevated permissions to specific users
- `useradd`: adds a user to the system
- `userdel`: deletes a user from the system
- `usermod`: modifies existing user accounts
- `chown`: changes ownership of a file or directory
- `groupdel`: delete a group 

***NOTE***: When you create a new user in Linux, a group with the same name as the user is automatically created and the user is the only member of that group. After removing users, it is good practice to clean up any such empty groups that may remain behind.

---

#additional-info 

## 3.05 - Additional Information

- [Unix Stack Exchange](https://unix.stackexchange.com/)

---
