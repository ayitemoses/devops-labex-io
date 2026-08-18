
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














