# Important Linux System Directories
The `Filesystem Hierarchy Standard (FHS)` defines the structure of Linux file systems. There are no drive letters.

## `/` - The Root Directory
*Everything* on the Linux system is located under the `/` directory. 

**A partition would just be listed under another folder under `/` in Linux.**

## `/bin` - Essential User Binaries
Important system programs and utilities such as the bash shell are located in `/bin`.

User applications like Firefox are stored under `/usr/bin`. It could even be in another directory.

`/sbin` contains system administration binaries.

## `/boot` - Static Boot Files
The `/boot` directory contains the files needed to boot Linux - like the GRUB boot loader and the Linux kernel is stored here.

>GRUB is a bootloader which is the first program that runs when a computer starts. It transfers control to the operating system kernel which in turn initializes the rest of the OS.

## `/cdrom` - Historial Mount Point for CD-ROMs
Is this even used anymore?

Not part of FHS standard but it still is on Ubuntu and other OS. Temporary location for CD-ROMs inserted in the system.

## `/dev` - Device Files
Linux exposes devices as "files".

- `/dev/dsp` - Digital Signal Processor, interface between software that produces sound and the soundcard.
- `/dev/fb0` - First framebuffer device. A framebuffer is basically a graphics driver (?).
- `/dev/null` - Blackhole where you can send data to never be seen again.
- `/dev/sda` - First SATA drive on the system. `/dev/sdb` is the second and so on.

## `/etc` - Configuration Files
Contains system-wide configuration files. User-specific configuration files are in each user's home directory.

## `/home` - Home Folders
Contains a home folder for each user. For example username bob's home folder is in `/home/bob`. 

Each user has ***write access only to their home folder*** and must obtain root permissions to modify other files on the system.

## `/lib` - Essential Shared Libraries
Contains libraries needed by the `/bin` and `/sbin`.

Necessary libraries for the binaries in `/usr/bin` are located in `/usr/lib`

## `/lost+found` - Recovered Files
Contains any corrupted files found when a file system check is performed after a system crash.

## `/media` - Removable Media (CDs/USBs)
Contains subdirectories where removeable devices are mounted.

## `/mnt` - Temporary Mount Points
Directory used by system admins to temporarily mount file systems while using them. For example: mounting a Windows partition to perform some file recovery operations. However this can be done in any other folder.

## `/opt` - Optional Packages
Contains subdirectories for optional packages, usually used by proprietary applications that do not obey the standard file system hierarchy.

## `/proc` - Kernel and Process Files
Contains special files that represent the system and process information.

## `/root` - Root Home Directory
Home directory of the root users instead of being located at `/home/root`.

## `/run` - Application State Files
A standard place for applications to store transient files they require like sockets and process IDs.

## `/sbin` - System Administration Binaries
The `/sbin` directory is similar to the `/bin` directory. Contains system admin binaries.

## `/selinux` - SELinux Virtual File System
Contains special files used by SELinux for security?

## `/srv` - Service Data
Contains site specific data to be served by the system for protocols like ftp, rsync, www, cvs. Not used that often.

## `/tmp` - Temporary Files
Temporary files that are deleted on restart or whenever by ultilities.

## `/usr` - User Binaries & Read-Only Data
Contains applications and files used by users. Read-only.

Non-essential applications are located in `/usr/bin` instead of `/bin`.

## `/var` - Variable Data Files
Writable counterpart to the `/usr` directory. Logs are usually found here.