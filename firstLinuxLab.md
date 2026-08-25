
# Use basic commands: echo, whoami, id.
# Extract a specific identity detail with id -un. 
echo "Hello LabEx"

whoami

id

id root

id -un # prints only your username 
### Summary
Congratulations! You learned how to:
- Open and use the terminal.
- Use basic commands: echo, whoami, id.
- Extract a specific identity detail with id -un

## Welcome to the Basic File Operations
pwd # stands for "print working directory"

echo ~

ls

ls ~

cd ..

cd project

cd ~

cd /home/labex/project

# Creating Files and Listing Directory Contents


touch file1.txt

echo "Hello, Linux" > file2.txt

echo "Hidden file" > .hiddenfile

mkdir testdir

ls

ls -l

ls -a

ls -la  # This combines the long format (-l) with showing all files (-a).

ls -l testdir

ls -R temp_dir  # means "recursive listing" (list subdirectories)

# Copying Files and Directories

cp file1.txt file1_copy.txt

cp file2.txt testdir/

cp -r testdir testdir_copy

# Moving and Renaming Files and Directories

mv file1.txt newname.txt

mv newname.txt testdir

mv testdir_copy new_testdir


mv testdir/newname.txt ./original_file1.txt  # This moves newname.txt out of testdir and renames it to original_file1.txt in the current directory.


# Removing Files and Directories

rm original_file1.txt  # The rm command (short for "remove") deletes files

rm -i file2.txt  # The -i option prompts you for confirmation before deleting each file. Type y (for yes) and press Enter to confirm the deletion. If you type n or anything else, the file will not be deleted.

 rm -r testdir  # Remove a directory and its contents (recursively)

## Summary
Congratulations! You've learned the essential file operations in Linux:

- Navigating the file system with cd and pwd
- Creating files and directories with touch and mkdir
- Listing contents with ls and its options
- Copying files and directories with cp
- Moving and renaming with mv
- Removing files and directories with rm and rmdir



# Files and Directories

## Copy Files and Directories


cp -r  ~/.zshrc ~/Desktop/zshrc-copy 

cp -r ~/Code ~/Desktop

ls -l ~/Desktop 

## Rename Files and Directories

mv ~/Desktop/zshrc-copy ~/Desktop/zshrc-move

mv ~/Desktop/zshrc-copy ~/Desktop/zshrc-move

mv ~/Desktop/zshrc-copy ~/Desktop/zshrc-move

ls -l ~/Desktop 

## Remove Files and Directories
rm -r ~/Desktop/Code-move 
rm -r ~/Desktop/zshrc-move
rm -r ~/Desktop/Code-move ~/Desktop/zshrc-move


### Summary
Congratulations! You have successfully completed the "Files and Directories" challenge, marking a significant step in your Linux journey. You are now equipped with the essential Linux file management commands: 
- cp for duplicating files and directories, 
- mv for both moving and renaming them, 
- rm for removing them when they are no longer needed.  


# File Contents and Comparing

## Print File Contents 
cat /tmp/hello

## Display File Contents with Line Numbers

cat -n  /tmp/hello


## Print the Top Lines of a File

head -n1 /tmp/hello   # First no1 line
 
head  /tmp/hello    # First 10 lines

## View the First Few Bytes of a File

 head -c1 /tmp/hello    # The -c1 option tells head to show only the first byte (character) of the file. Like with -n, you can change the 1 to any number to see that many bytes.

## Print the Last Lines of a File

tail -n1 /tmp/hello  # Last no1 line

tail  /tmp/hello      # Last 10 lines

## View the Last Few Bytes of a File

tail -c1 /tmp/hello   # You might not see any output. This is because the last character is likely a newline character, which is invisible.
tail -c2 /tmp/hello   # The -c2 option tells tail to show the last 2 bytes (characters) of the file


## Comparing Files
cd ~/project

diff file1 file2  ##  1c1: This indicates that line 1 in the first file needs to be changed to match line 1 in the second file.
< this is file1: The < symbol indicates a line from the first file (file1). ---: This is a separator between the lines from file1 and file2. > this is file2: The > symbol indicates a line from the second file (file2).

## Comparing Directories

diff -r ~/Desktop  ~/Code  # This output shows that the Desktop directory contains four files that are not in the Code directory.

## Summary
Congratulations! You've completed the File Contents and Comparing lab. Let's recap what you've learned:

- cat to view the entire contents of a file.
- cat -n to view file contents with line numbers.
- head to view the beginning of a file, both by lines and by bytes.
- tail to view the end of a file, both by lines and by bytes.
- diff to compare the contents of files.
- diff -r to compare entire directories.

# The Manuscript Mystery

## Examining File Contents
In this step, you'll use cat, head, and tail to inspect two mysterious files.ca

cat /home/labex/project/manuscript_v1.txt 

head -n2 /home/labex/project/manuscript_v2.txt

tail -n1 /home/labex/project/manuscript_v1.txt

tail -n1 /home/labex/project/manuscript_v1.txt

## Comparing the Files

diff /home/labex/project/manuscript_v1.txt /home/labex/project/manuscript_v2.txt 


## Summary
Congratulations, junior editor! You've successfully applied your newly learned Linux file examination skills to uncover the differences between two versions of a manuscript page. Your ability to use cat, head, tail, and diff has proven invaluable in this editorial mystery.

# Permissions of Files

## Creating a New File

cd ~/project

touch example.txt

## Changing the Ownership of a File

ls -l example.txt | -rw-rw-r-- 1 labex labex 0 Aug 23 09:18 example.txt   # -rw-rw-r-- represents the file permissions - ( for a regular file, d for directory, etc.). The remaining characters represent read, write, and execute permissions for the owner, group, and others.

Now, let's change the ownership of the file to the root user. root is the administrator account on Linux systems, and it has special privileges. 

sudo chown root:root example.txt  # -rw-rw-r-- 1 root root 0 Aug 23 09:18 example.txt

## Changing the Ownership of a Directory

mkdir -p new-dir/subdir # mkdir -p new-dir/subdir creates the new-dir directory and its subdir subdirectory. The -p option tells mkdir to create parent directories as needed.

echo "Hello world" > new-dir/file1.txt

echo "Another file" > new-dir/subdir/file2.txt

ls -lR new-dir # lists the contents of new-dir recursively. 

sudo chown -R root:root new-dir  # The -R option tells chown to operate recursively, changing the ownership of all files and subdirectories within new-dir

## Changing the Permissions of a File

ls -l example.txt 
-rw-rw-r-- 1 root root 0 Aug 23 09:18 example.txt

The first character (-) indicates this is a regular file. Other common indicators are d for directory and l for symbolic link.
The next three characters (rw-) represent the owner's permissions (read and write, but not execute).
r stands for read permission: The owner can open and read the file.
w stands for write permission: The owner can modify the file.
x stands for execute permission: The owner can run the file (if it's a program or script). A - means the permission is denied.
The next three (rw-) are for the group. They have the same meaning as above, but apply to members of the file's group.
The last three (r--) are for others (everyone else). They also have the same meaning, but apply to users who are neither the owner nor members of the file's group.


sudo chmod 700 example.txt
ls -l example.txt 
-rwx------ 1 root root 0 Aug 23 09:18 example.txt


700 is a numeric representation of permissions:
- The first digit (7) represents the owner's permissions.
- The second digit (0) represents the group's permissions.
- The third digit (0) represents the others' permissions.

4: Read permission  2: Write permission 1: Execute permission 0: No permission

So, 7 (first digit) gives the owner read (4), write (2), and execute (1) permissions: 4+2+1=7
0 (second digit) gives the group no permissions (0+0+0=0).
0 (third digit) gives others no permissions (0+0+0=0).

Therefore, 700 means: Owner: read, write, execute. Group: none. Others: none.

## Changing the Permissions of a Directory

mkdir ~/test-dir

chmod 700 ~/test-dir

ls -ld ~/test-dir
drwx------ 2 labex labex 6 Aug 23 09:39 /home/labex/test-dir

chmod -R 755 ~/test-dir # -R applies the change recursively to all files and subdirectories (though our directory is empty in this case)

ls -ld ~/test-dir 
drwxr-xr-x 2 labex labex 6 Aug 23 09:39 /home/labex/test-dir

755 gives read, write, and execute permissions to the owner, and read and execute permissions to group and others.
Let's break down 755:

- Owner (7): Read (4) + Write (2) + Execute (1) = 7 | drwx
- Group (5): Read (4) + Execute (1) = 5 rx
- Others (5): Read (4) + Execute (1) = 5 rx 

## Using Symbolic Notation for Permissions

cd ~/project
echo '#!/bin/bash' > script.sh
echo 'echo "Hello, World"' >> script.sh

The first echo command creates script.sh and writes the first line, #!/bin/bash, into it. This line is called a shebang, and it tells Linux to run the script with Bash.

The second echo command adds a new line to the end of the file with >>. It writes echo "Hello, World", which will display Hello, World when the script runs.

chmod u+x script.sh  # u refers to the user (owner). Other options are g for group, o for others, and a for all (user, group, and others). +x adds execute permission. The + symbol adds a permission, while the - symbol removes a permission.
So, u+x means "add execute permission for the owner."

## Summary
In this lab, we've explored essential Linux commands for managing file permissions:

- touch to create new files and update existing ones.
- chown to change file and directory ownership, including recursive changes for entire directory structures.
- chmod with both numeric and symbolic notation to modify file and directory permissions, understanding the different permission levels for owner, group, and others.
We saw practical examples of why permissions matter, such as needing execute permissions to run scripts.
We clarified the differences between numeric and symbolic notation for chmod and when each might be more appropriate.
These commands are crucial for maintaining security and controlling access in Linux systems. Remember to always be cautious when changing permissions, especially when using sudo, as incorrect changes can have significant consequences for system security and functionality. Always double-check your commands before executing them, and understand the implications of the changes you're making.

## Practice
### change File Ownership

touch ~/project/target_file

cd ~/project && ls

sudo chown user1:group1 target_file

ls -l ~/project/target_file 
-rw-rw-r-- 1 user1 group1 0 Aug 23 10:01 /home/labex/project/target_file

### Set the File Permissions

sudo chmod 760 target_file

ls -l target_file         
-rwxrw---- 1 user1 group1 0 Aug 23 10:01 target_file


# User Account Management

## Creating a New User

sudo useradd joker

- sudo is a command that gives you temporary superuser (administrator) privileges. We use it because creating a new user requires these higher-level permissions.
- useradd is the command to create a new user.
- joker is the username we're creating.


sudo grep -w 'joker' /etc/passwd # To verify that the user was created, we'll examine the /etc/passwd file:
joker:x:5001:5001::/home/joker:/bin/sh

Username: joker | Password: x (the actual password is stored securely elsewhere) | User ID: 5001 | Group ID: 5001
Home Directory: /home/joker, but it hasn't been created yet | Default Shell: /bin/sh

## Creating a User with a Home Directory

sudo useradd -m bob # The -m option tells the system to create a home directory for the user. 

sudo ls -ld /home/bob   
drwxr-x--- 2 bob bob 57 Aug 23 10:16 /home/bob
d at the start means it's a directory | rwxr-x--- shows who can read, write, or execute in this directory
The two bob entries show that both the user and group owner of this directory is bob 
57 is the size of the directory in bytes | Aug 23 10:16 is when the directory was created


## Setting a User Password

sudo passwd joker

Behind the scenes, Linux stores encrypted passwords in a secure file called /etc/shadow. This is more secure than storing them in the /etc/passwd file where anyone could see them.

## Modifying User Properties

sudo usermod -d /home/wayne joker

usermod is the command to modify user account settings
-d /home/wayne specifies the new home directory
joker is the user we're modifying

sudo grep -w 'joker' /etc/passwd
joker:x:5001:5001::/home/wayne:/bin/sh

-w is used to match the whole word, and grep is used to search for the word in the file. You should see that joker's home directory has been updated in the output.

## Changing User Shell

By default, the user 'joker' is using /bin/sh as their shell. While sh (Bourne Shell) is a basic shell that's present on most Unix-like systems, bash (Bourne Again Shell) offers more features and is generally more user-friendly.

sudo usermod -s /bin/bash joker 

sudo grep -w 'joker' /etc/passwd
joker:x:5001:5001::/home/wayne:/bin/bash


## Adding a User to a Group

sudo usermod -aG sudo joker 

usermod is the command to modify user accounts | -aG means "append to Group" (add to a group without removing from other groups) | sudo is the group we're adding the user to | joker is the user we're modifying

groups joker 
joker : joker sudo # sudo listed among joker's groups.


su - joker  # This command switches from your current user (labex) to the joker user.

## Locking and Unlocking User Accounts

sudo passwd -l joker   # Lock the joker account. The -l option locks the password.

Try to switch to the joker user:
su - joker 
Password: 
su: Authentication failure

sudo passwd -u joker   # Unlock the joker account. The -u option unlocks the password.

## Deleting a User

sudo userdel -r bob  # The userdel command deletes user accounts. The -r option removes the user's home directory and mail spool.

Verify that the user has been deleted:
sudo grep -w 'bob' /etc/passwd

sudo ls -l /home/bob
ls: cannot access '/home/bob': No such file or directory

## Summary
Congratulations! You've completed the Linux User Account Management lab. You've learned how to:

- Create new user accounts                                          # useradd
- Set user passwords                                                # passwd        
- Modify user properties like home directory and default shell      # usermod -s
- Add users to groups                                               # usermod -aG
- Lock and unlock user accounts                                     # passwd -l or -u
- Delete user accounts                                              # userdel

You've also been introduced to important Linux concepts like the /etc/passwd file, home directories, shells, and user groups. These are fundamental skills for Linux system administration. Remember, in real-world scenarios, always follow your organization's security policies when managing user accounts.


# The Joker's Trick

## Creating User Accounts

1. Create a user named joker.

sudo useradd joker

2. Create a user named batman with a home directory at /home/gotham.
sudo useradd -m batman

sudo usermod -d /home/gotham batman

## Managing User Passwords

1. Set a password for the joker user.
sudo passwd joker

2. Set a password for the batman user.
sudo passwd batman

After setting the passwords, you can check the password status: sudo passwd -S joker


## Modifying User Accounts

1. Change the joker user's home directory to /home/arkham.
sudo usermod -d /home/arkham joker

sudo grep joker /etc/passwd
joker:x:5003:5004::/home/arkham:/bin/sh

2. Change the batman user's shell to /bin/bash.

sudo usermod -s /bin/bash batman

sudo grep batman  /etc/passwd
batman:x:5004:5005::/home/gotham:/bin/bash


## Deleting User Accounts

1. Delete the joker user without removing their home directory.
sudo userdel joker


2. Delete the batman user and their home directory /home/gotham.
sudo userdel -r batman 

# The Lay of the Land


## First Login and Environment Check
- Find out the username of the current user. : 
whoami
- Display the kernel name of the operating system. : 
uname


## Checking System Information and Uptime
- Display comprehensive system information including operating system details, kernel version, and hardware architecture.
uname -a 

- Check how long the system has been running and current system load.
uptime

## Gathering User and Group Details
- Display the detailed user and group information for your current user account.
id

uid=5000(labex) gid=5000(labex) groups=5000(labex),27(sudo),121(ssl-cert),5002(public)

- uid=5000(labex): Your user ID is 5000 with username "labex"
- gid=5000(labex): Your primary group ID is 5000 with group name "labex"
- groups=...: You belong to multiple groups including "sudo" (administrative privileges), "ssl-cert" (SSL certificate access), and "public" (shared resources)

## Monitoring Real-time System Performance

- provides a dynamic, real-time view of a running system. It refreshes automatically.
top


## Generating a System Status Report


- Create a file named system_report.txt in your current directory (~/project).
touch system_report.txt

- The file must contain the output of the whoami, uname -a (all system information), and uptime commands.
whoami > system_report.txt

uname -a >> system_report.txt

uptime >> system_report.txt

# The Digital Architect

## Setting Up the Project Directory Structurels

1. Navigate into the ~/project/phoenix_project directory.
cd phoenix_project 

2. Create three new subdirectories: src for source code, config for configuration files, and docs for documentation
mkdir src config docs
ls -F

## Navigating and Creating Project Files

1. Move the main_app.py file into the src directory.

mv main_app.py src/ 
2. Move the config.json file into the config directory.
mv config.json config/

3. Move the README.md file into the docs directory.
 mv README.md docs/


 ## Backing Up Critical Configuration Files

cd config/

cp config.json config.json.bak

## Reorganizing the Team’s Shared Resources

Move the entire shared_docs directory and all of its contents into the ~/project/phoenix_project/docs/ directory.

mv shared_docs phoenix_project/docs 

## Archiving and Removing Outdated Log Files

The tar command uses different options (flags) to control its behavior:
c: Create a new archive
z: Compress the archive using gzip
f: Specify the filename of the archive
So tar -czf archive.tar.gz file1 file2 creates a new compressed archive named archive.tar.gz containing file1 and file2

1. Navigate to the ~/project/logs directory.

cd ~/project/logs

2. Create a compressed tar archive named old_logs.tar.gz that contains all log files from the year 2023.

tar -czf old_logs.tar.gz app_2023-01-15.log db_2023-02-20.log 

3. After the archive is successfully created, delete the original 2023 log files that you just archived.

rm *_2023-*.log

# The Log Investigator

## Reviewing Application Log File Contents

Filter the ~/project/logs/app.log file to find all lines containing the word ERROR.
sudo grep -w "ERROR" logs/app.log

Save the filtered lines to a new file named ~/project/error_report.txt.

sudo grep -w "ERROR" logs/app.log > error_report.txt

## Investigating System Boot Messages

Examine the system's kernel messages for any lines related to fail or error.
Save these findings into a file named ~/project/boot_issues.txt.

sudo dmesg   

sudo dmesg | grep -E 'fail|error' > boot_issues.txt


The dmesg command displays kernel messages. You can "pipe" its output to another command for filtering.
The pipe operator | sends the output of one command to the input of another.
The grep command's -i option makes the search case-insensitive.
To search for multiple patterns at once (like fail OR error), you can use grep -E 'pattern1|pattern2'.
Note: If you encounter a "Operation not permitted" error, try running the command with sudo to gain the necessary privileges.


## Examining the Web Server Configuration File

Search the web server configuration file at ~/project/config/nginx.conf.
Find the line containing the worker_processes directive.
Append this line to the ~/project/error_report.txt file you created in the first step.

sudo grep -w 'worker_processes' ~/project/config/nginx.conf >> ~/project/error_report.txt 

## Comparing Staging and Production Configuration Files

Compare the staging configuration file ~/project/config/staging/app.conf with the production configuration file ~/project/config/production/app.conf.
Save the differences to a new file named ~/project/config_diff.txt.

diff config/staging/app.conf config/production/app.conf > config_diff.txt

cat config_diff.txt 

## Verifying Directory Consistency Between Servers

You have two directories: /home/labex/project/server1_files (representing the staging server) and /home/labex/project/server2_files (representing the production server).
Compare these two directories to find out which files are unique to server1_files.
Save the complete comparison output to a file named /home/labex/project/missing_files.txt.

diff -r /home/labex/project/server1_files /home/labex/project/server2_files > /home/labex/project/missing_files.txt


##Summary
Exceptional detective work! You have successfully identified the root causes of Project Phoenix's critical failures and provided Sarah Chen and the development team with actionable intelligence to resolve the issues.

Through your systematic investigation, you've mastered essential troubleshooting commands:

- grep: To filter log files and extract critical error information.
- dmesg: To investigate system-level hardware and kernel issues.
- diff: To compare configuration files and identify discrepancies between environments.
- Command pipelines and redirection: To efficiently process and document your findings.

# The Fortress Guardian

## Creating a Secure File for a New Project

Create a new, empty file named project_keys.txt inside the ~/project/phoenix_project directory.
Set the permissions for this file so that only the owner has read and write access, and no one else (not even users in the same group) has any access.

You can create an empty file using the touch command.
Remember the numeric values for permissions: read (4), write (2), and execute (1).
The final permission should be 600 (read+write for owner, nothing for group and others).

touch ~/project/phoenix_project/project_keys.txt 

chmod 600 phoenix_project/project_keys.txt

## Assigning Ownership of Project Resources

Change the owner of the ~/project/phoenix_project directory and all its contents to the user dev_lead.
Change the group owner of the ~/project/phoenix_project directory and all its contents to the developers group.

sudo chown -R dev_lead:developers ~/project/phoenix_project

ls -ld ~/project/phoenix_project 

ls -l ~/project/phoenix_project 

## Securing the Main Project Directory

Set the permissions for the ~/project/phoenix_project directory.

The owner (dev_lead) must have read, write, and execute permissions.
The group (developers) must have read and execute permissions.
Others must have no permissions.
Use the chmod command to apply these permissions to the ~/project/phoenix_project directory itself (not recursively).
Since the directory is owned by dev_lead, you may need to use sudo to change permissions.

sudo chmod 750 ~/project/phoenix_project 
ls -ld ~/project/phoenix_project

## Setting Up Collaborative Permissions for the Dev Team

Set a special permission on the ~/project/phoenix_project/src directory that forces all new files and subdirectories created within it to inherit the group ownership from the src directory itself (which is developers).

This special permission is called the "set group ID" or setgid bit.
You can apply the setgid bit using either symbolic (g+s) or numeric notation.
In numeric notation, the setgid bit has a value of 2. It is placed before the standard three permission digits (e.g., 2770).

ls -ld ~/project/phoenix_project/src
drwxrws--- 2 dev_lead developers 6 Aug 25 11:51 /home/labex/project/phoenix_project/src

The s in the group execute position indicates the setgid bit is set and the group has execute permission.


## Summary
Outstanding work, Fortress Guardian! You have successfully built an impenetrable security foundation for Project Phoenix. The CTO and Sarah Chen are amazed by your comprehensive security implementation. The project directory is now a fortress that will protect TechNova's intellectual property while enabling seamless collaboration.

Throughout this challenge, you've mastered critical Linux security skills:

Creating Files and Basic Permissions: You secured sensitive project keys with precise permission controls.
Ownership Management: You expertly assigned ownership to Sarah's development team and technical leadership.
Directory Security: You balanced access and security for the main project infrastructure.
Advanced Permissions: You configured setgid permissions to ensure collaborative team workspaces with automatic group ownership inheritance.

# The Keeper of the Keys

## Onboarding a New Developer to the System

Create a new user account for Brenda Smith.

sudo useradd b.smith

sudo grep -w b.smith /etc/passwd
b.smith:x:5002:5004::/home/b.smith:/bin/sh

The user account will be created with a system-assigned user ID and group ID. You can verify the account exists and check its details using:

id b.smith 
uid=5002(b.smith) gid=5004(b.smith) groups=5004(b.smith)

## Creating a Dedicated Home Directory for the New User

Create a home directory for the user b.smith located at /home/b.smith.

sudo useradd -m b.smith

sudo ls -la /home/b.smith

## Assigning an Initial Password for the New User

Set a password for the user b.smith.

sudo passwd b.smith 

sudo grep b.smith /etc/shadow
b.smith:$y$j9T$e52hXwvTC5lCsoo6zKJXF0$VHKiDpz5PJgmqBQEksBP9qjSCb3M1aU13XdFNPtyEq/:20690:0:99999:7:::


## Adding the New Developer to the "developers" Group

Add the user b.smith to the developers group.

sudo usermod -aG developers b.smith

groups b.smith 
b.smith : b.smith developers


## Temporarily Disabling a Departing Employee’s Account

Lock the user account for j.doe to prevent logins.

sudo usermod -L j.doe 

sudo passwd -l j.doe 
passwd: password expiry information changed.

sudo grep "^j.doe" /etc/shadow
j.doe:!:20690:0:99999:7:::

Notice the exclamation mark (!) at the beginning of the password field - this indicates the account is locked. The original password hash is preserved after the ! for potential future unlocking.

## Summary
Congratulations, Keeper of the Keys! You have successfully completed your incredible first week at LabEx Corporation and secured Project Phoenix for its final push to completion.

Throughout this transformative week, you've evolved from a new junior system administrator into a trusted guardian of TechNova's most critical systems. In your final challenge, you mastered essential user management commands:

- Created a new user account for the senior developer leading Project Phoenix's completion.
- Configured secure home directories for critical team members.
- Implemented robust password policies using passwd.
- Managed group memberships to ensure proper access to Project Phoenix resources.
- Secured the system by disabling unauthorized access while preserving audit trails.
From initial reconnaissance to digital architecture, log investigation, security implementation, and finally user management—you've demonstrated the complete skill set of a professional System Administrator. The CTO has confirmed your permanent position and is already discussing promotion opportunities.

Project Phoenix is now in safe hands, and TechNova's future is secure thanks to your dedication and expertise!