# 35 Useful [[#Linux]] Commands

When a command is executed, the [[Linux#What is the Shell|shell]] interpreter checks for an `alias` under that name before it looks in the [[Linux Directories#bin - Essential User Binaries|/bin]] directory.

https://www.hostinger.com/tutorials/linux-commands

## Displaying info

### `pwd`

Prints the working directory

### `ls`

List content of _**directory**_

- `-R` will list all files in the sub directories
- `-a` will show hidden files
- `-al` will list files and directories with detailed information like permissions, size, owner, etc.

### `cat` (List or joins file content)

List content of a **_file_**.

Other ways to use `cat`:

- `cat > filename` creates new file
- `cat filename1 filename2>filename3` joins files 1 and 2 and stores the output of them in a new file 3.
- `cat filename | tr a-z A-Z >output.txt` convert file to upper or lower case

### `head` (Text file)

Shows the first 10 lines of a text file.

`head -n 5 filename` to show 5 lines.

### `tail` (Text file)

Shows last lines of a text file.

### `diff` (Text file)

Compares contents of two files line by line, and prints the lines that do not match.

`diff file1.ext file2.ext`

## Navigating

### `cd`

Change directory.

Useful shortcuts:

- `cd` go to home folder
- `cd-` go to previous directory

## Creating

### `mkdir` (New directory)

Make a new directory.

- `mkdir directoryname`

Can make a directory one level inside

- `mkdir directory/nestdirectory`

If you want to make more levels, use `-p`, and it will make the directory if it doesn't already exist.

- `mkdir -p DirectoryName/Parent1/Parent2/NewDirectory`

### `touch` (New file)

Makes new empty **file**.

### `echo` (Write data to file)

Move data to a file. `echo Hello, my name is Vong >> name.txt`. Writes "Hello my name is Vong" to name.txt.

```bash

# displays variable name
echo sys

# displays variable value
echo $sys


```

## Moving Files

### `cp`

Copy files from current directory to different directory.

- `cp scenery.jpg /home/username/Pictures` would make a copy of `scenery.jpg` from your directory in the Pictures directory

### `mv` (Move and rename files)

Move files.

- `mv file.txt /home/username/Documents`

Can also be used to rename.

- `mv oldname.ext newname.ext`

## Deleting

### `rmdir` (Empty directories only)

Delete only **empty** directories.

### `rm` (Files and directories)

- `rm -d dirname` - Remove empty directories
- `rm -r dirname` - Delete directories and everything inside it.
- `rm file1 file2 file3` - Remove multiple files
- `rm *.png` - Use regex to delete files
- `rm -v filename` - Get info on what was removed. Will output _removed 'filename_.

## Searching

### `locate` (Files only)

Uses a database to search for **files**.

- `locate word1*word2` will search for files containing words 1 and 2.
- `-i` makes search case insensitive.

### `find` (Files or directories inside specific directories)

Searches for **files** and **directories**. However, you can use `find` to locate files within a given directory.

- `find . -name notes.txt`

### `grep` (Search text file)

Global regex print. Searches through text in a given file

- `grep blue notepad.txt` will search for "blue" in the "notepad.txt" file.

## Permissions

### `sudo`

Short for **SuperUser Do**. 😮 Gives admin rights and stuff.

### `chmod` (Change permissions)

Change mode. Change read, write, and execute permission of files and directories.

### `chown` (Change owner)

Changes ownership of a file.

`chown user2 file.ext` gives ownership to user2.

## Archiving

### `tar` (Optional compress)

Archive multiple files into a **tarball** - Linux file format that is similar to zip format with option compression.

### `zip` and `unzip`

Compress files to zip archive and use unzip to unzip.

## Processes

### `jobs`

Display all current jobs and their statuses. A job is a process that is started by the shell.

### `kill`

Manually terminate a program. There are **64** signals to tell a program to terminate. Need to provide the **process identification number** of the program.

- SIGTERM (15) is default. Gives program time to terminate and save its progress.
- SIGKILL (9) forces immediate stop, unsaved progress will be lost.

`kill [signal option] PID`

### `top` (Task Manager)

Display a list of running programs and how much CPU each program uses.

## Networking

### `ping`

`ping google.com` to get pings!

### `wget` (Download - webget)

Download files.

`wget <downloadlink>`

### `hostname`

Displays computer's network name. Adding `-i` will display IP address

## System

### `uname`

Short for Unix Name, will print detailed information about the Linux system, like machine name, operating system, kernel, etc.

### `history`

List a history of all commands that have been run.

### `man` (Manual)

Manual! `man tail` will show manual for the `tail` command

### `df` (Show how much space available)

Disk free. Show system disk space usage in percentage and KBs.

`df -h` to see human readable.

### `du` (disk usage for directories)

Disk usage?. Show how much space the file or directory takes.

`du -h` to show in normal size format.

### `useradd` and `userdel`

`useradd` creates new user, `passwd` adds a password to the account.
`useradd John` then `passwd 123456`.

`userdel John` deletes the account.

### `export`
Each shell session has access to a list of variables. Using `export` will list them and variables can be created/modified with: `export variableName[=value]`.

Exporting functions can also be done:
```bash
function hello {
	echo hello, world
}

export -f hello`
```