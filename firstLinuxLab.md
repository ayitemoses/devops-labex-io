
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




