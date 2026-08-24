
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



