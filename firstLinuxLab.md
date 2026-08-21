
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


# File Contents and COmparing

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





