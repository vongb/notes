# 35 Useful Linux Commands

https://www.hostinger.com/tutorials/linux-commands

## `pwd`

Prints the working directory

## `cd`

Change directory.

Useful shortcuts:

- `cd` go to home folder
- `cd-` go to previous directory

## `ls`

List content of _**directory**_

- `-R` will list all files in the sub directories
- `-a` will show hidden files
- `-al` will list files and directories with detailed information like permissions, size, owner, etc.

## `cat`

List content of a **_file_**.

Other ways to use `cat`:

- `cat > filename` creates new file
- `cat filename1 filename2>filename3` joins files 1 and 2 and stores the output of them in a new file 3.
- `cat filename | tr a-z A-Z >output.txt` convert file to upper or lower case

## `cp`

Copy files from current directory to different directory.

- `cp scenery.jpg /home/username/Pictures` would make a copy of `scenery.jpg` from your directory in the Pictures directory

## `mv`

Move files.

- `mv file.txt /home/username/Documents`

Can also be used to rename.

- `mv oldname.ext newname.ext`

## `mkdir`

Make a new directory.

- `mkdir directoryname`

Can make a directory one level inside

- `mkdir directory/nestdirectory`

If you want to make more levels, use `-p`, and it will make the directory if it doesn't already exist.

- `mkdir -p DirectoryName/Parent1/Parent2/NewDirectory`

## `rmdir`

Delete only **empty** directories.

## `rm`

- `rm -d dirname` - Remove empty directories
- `rm -r dirname` - Delete directories and everything inside it.
- `rm file1 file2 file3` - Remove multiple files
- `rm *.png` - Use regex to delete files
- `rm -v filename` - Get info on what was removed. Will output _removed 'filename_.

## `touch`

Makes new empty **file**.

## `locate`

Uses a database to search for **files**.

- `locate word1*word2` will search for files containing words 1 and 2.
- `-i` makes search case insensitive.

## `find`

Searches for **files** and **directories**. However, you can use `find` to locate files within a given directory.

- `find . -name notes.txt`

## `grep`

Searches through text in a given file

- `grep blue notepad.txt` will search for "blue" in the "notepad.txt" file.

## `sudo`

Short for **SuperUser Do**. 😮 Gives admin rights and stuff.

## `df`

Show system disk space usage in percentage and KBs.

`df -m` to see in MBs.

## `du`

Show how much space the file or directory takes.

`du -h` to show in normal size format.

## `head`

Shows the first 10 lines of a text file.

`head -n 5 filename` to show 5 lines.

## `tail`

Shows last lines of a text file.

## `diff`

Compares contents of two files line by line, and prints the lines that do not match.

`diff file1.ext file2.ext`

## `tar`

Archive multiple files into a **tarball** - Linux file format that is similar to zip format with option compression.

## `chmod`

Change read, write, and execute permission of files and directories.

## `chown`

Changes ownership of a file.

`chown user2 file.ext` gives ownership to user2.

## `jobs`

Display all current jobs and their statuses. A job is a process that is started by the shell.

## `kill`

Manually terminate a program. There are **64** signals to tell a program to terminate. Need to provide the **process identification number** of the program.

- SIGTERM (15) is default. Gives program time to terminate and save its progress.
- SIGKILL (9) forces immediate stop, unsaved progress will be lost.

`kill [signal option] PID`

## `ping`

# Questions

1. I read that `locate` uses a database to search through so it's fast. Have to `updatedb`. Does it make `locate` less reliable? Do you use this command often?
2. `tar` still unclear.
3. `chmod` too
