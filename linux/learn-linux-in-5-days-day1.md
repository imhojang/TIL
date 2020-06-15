## Learn Linux In 5 Days - Day 1

- What Linux is
  - An operating system
    - collection of software that manages hardware resources and provides an environment where applications can run
    - opereating system allows applications to store information, send documents to printers, interact with users, and other things.
  - A Kernel
    - the core or the heart of the operating system
    - the layer that sits between the hardware and applications
    - intermediary between software and hardware
    - to have a useful operating system you need other components in addition to kernel. suchas system libraries, graphical user interafces, email utilities web browsers, and other programs
  -  Created by Linus Torvalds
  - First version released in 1994
  - FOSS (Free/Open Source Software)
- What a Linux Distribution is
  - Linux Kernel Plus Additional Software
  - Each distribution can have a different focus
  - Many distributions available to choose from
    - server use
    - desktop use
    - research and science
    - Multimedia production
    - hundreds of linux distributions
  - Linux Distributions
    - Distrowatch.com
    - Red Hat Enterprise Linux (RHEL)
    - Fedora
    - Ubuntu
    - Debian
    - SuSE Linux Enterprise Server (SLES)
    - OpenSuSE
- Reasons Linux is used
  - Runs on many hardware platforms
    - runs on many hardware platforms
    - dedicated networking devices
    - phones
    - personal computers
    - super computers
  - Small footprint of linux 
    - allows it to run on older hardware or on embedded systems
  - Stable, Reliable, Secure
  - Great for server
  - FOSS
- Unix-like



## The Linux Directory Structure

### Common Directories

- / 
  - "root", the top of the file system hierarchy
- /bin
  - Binaries and other executable programs
  - programs are written in source code: human readable text
  - text files are then compiled into machine readable binaries
- /etc
  - system configuration files
  - configuration files control how the operating system or applications behave
-  /home
  - where user home directories live
  - "/home/name"
- /opt
  - optional or third party software
  - that is not bundled with the operating system
  - google earth
- /tmp
  - temporary space, typically cleared on reboot
- /usr
  - user related programs live
- /var
  - variable datra, most notably log files
  - think of things that change often on Linux system
  - like log files that are generated either by the operating system itself or applications

### Comprehensive Directory Listing

- /boot
  - files needed to boot the operating system
- /cdrom
  - mount point for CD-ROM
- /cgroup
  - control Groups hierarchy
- /dev
  - Device files, typically controlled by the operating system and the system administrators
- /export
  - shared file systems
- /lib
  - system libraries
- /libe64
  - system libraries
  - 64 bit
- /lost+found
  - used by the file system to store recovered files after a file system check has been performed
- /media
  - used to mount removable media like CD-ROMS
- /mnt
  - used to mount external file systems
- /proc
  - provides info about running processes
- /sbin
  - system administration binaries
- /selinux
  - used to display information about SELinux
- /srv
  - contains data which is served by the system
- /srv/www
  - web server files
- /srv/ftp
  - ftp files
- /sys
  - used to display and sometimes configure the devices known to the Linux Kernel

### Application Directory Structures

- optional application that is not bundled with Linux should be in : /usr/local OR /opt



## The Shell

- The default interface to Linux 

