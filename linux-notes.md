----------------------
<<0>> CONTENTS:
----------------------
<<1>>  TTY, terminal, working with stdin/stdout/stderr
<<2>>  Kernel, date, time, locale
<<3>>  Users, groups, permissions
<<4>>  Hardware and firmware
<<5>>  Package managers (snap, apt, rpm, dpkg, pacman)
<<6>>  File system and disk space, logs
<<7>>  Processes and memory
<<8>>  Networking
<<9>>  Vi + Vim
<<10>> Other

! search for <<N>> to jump quickly on a specific topic


## <<1>> TTY

*

     ctr + alt + Fn - open the virtual console number n

* 

     stty - changes and prints terminal line settings (for the control sequences)
     stty -a  - prints all


     bind -l - lists all readlines in Bash session 
     bind -p  - displays all control sequences' keys and their meanings (.inputrc)


*
     Keybindings:

     ctrl + alt + d  - minimize all windows (ubuntu)

     ctrl + alt + t  - open a terminal window (ubuntu)

     ctrl + R - to redraw (when control sequences 

     ctrl + U - to delete a whole line in terminal 

     ctrl + W - to delete a word (from right to left)

     crtl + Z - to stop a process 

     crtl + C  - to abort from a process 

     ctrl + D - to send an interrupt message 

     Alt + Space (then select "minimize") - minimize a window

*

     https://devhints.io/bash

*

     stdin (0)

     stdout (1)

     stderr (2)



     Examples:

     info cat > cat.info 2> cat.stderr 

     Merging sources :

     2>&1 - tells the terminal to put stderr together with stdout:
     info cat > cat.info 2>&1 
     TIP! : to avoid writing "2>&1 file" there's a shortcut "&> file"/">& file"
     info cat > cat.info 2> /dev/null


     ; - to restrict commands in a line between each other

*

     expr - to calculate some integers in terminal

     bc - to calculate ( more powerful one)

*

     read -r  - read from std input( -r means that each backslash will be ignored)

*

     exec - execute a command/file

     execlp - execute a file

*

     test -f (file )/ -d (dir) - to test IF a file is a file or dir 

*

     info commandName

     man commandName

     commandName --help (or) -h

     whatis commandName

     apropos [keyword,command,string] - search for a command/service by keywords or name (into man pages)

*

     locate fileName

*

 NOTE!:
          Aliases are not expanded when the shell is not interactive, unless the expand_aliases shell option is set using shopt (see the description of shopt under SHELL BUILTIN COMMANDS below).
          The simple answer for you is that scripts create non-interactive shells and, by default, the expand_aliases option is often disabled.

          You can fix this very simply by just adding the following line to the top of your script to enable the alias expansion:
               shopt -s expand_aliases
               source ~/.bash_aliases

     alias (show all alias)

     alias neWname='someCommand'

     unalias commandName

     unalias -a ( "-a" means all)

     alias lf='ls -alF | sort'

*

     pwd - print working directory

*

     whereis [object | bash-file | command]

     which commandName - show a full path to binaries of the command

*

     clear - clear a terminal screen

*
     https://www.howtogeek.com/howto/44997/how-to-use-bash-history-to-improve-your-command-line-productivity/

     history - list all used commands ( their number is limited and they are stored in )

     !PATTERN - run the last used command matching the PATTERN

     !PATTERN:p - print the last used command mathching PATTERN without running it

     commandName !$  - to run commandName reusing the first argument passed to the last used command (tip: path to a file/dir)
               Usage:
                    touch ~/test.txt
                    vi !$ (means "vi ~/test.txt")

     commandName !* - to do that reusing all the arguments passed to the last used command

*

     dmesg - display all dignostic messages from tty1 into a current treminal which is running from Kernel Linux

*

     commandName & - run a command in a background

     %jobName & - put a job in background  (not stopping it)

     %jobName - put a job in foreground

*

     yes - output a string repeatedly until killed

*

     look - display lines beginning with a given string (look up for a given string or a word in a file)

*

     tee  - eads the standard input and writes it to both the standard output and one or more files.
     Options:
          -a - append output to a file without overwriting its content
          -i - ignore interrupt signals

     command | tee file.out >/dev/null - supress writing to stdout
     watch -e command | tee -a error.log >/dev/null


*

     dircolors - colour setup for ls (perhaps it's useless)



*

     awk - 

     https://www.geeksforgeeks.org/awk-command-unixlinux-examples/

*

     https://www.opensourceforu.com/2012/06/beginners-guide-gnu-grep-basics/

     https://stackoverflow.com/questions/1546711/can-grep-show-only-words-that-match-search-patternw

     cat Bookmarks.json | grep -oh "\w*http\w*" | awk '{print $0,"\n"}'

     grep '}$' - matches \n character or end line in POSIX/GNU

     grep "pattern" /path/to/file | awk '{print $0,"\n"}'  - putting new line between each element of the output

     grep linux file*.{txt,htm*} - search for all strings that contain "linux" in a current directory

     grep -h -v 2017-07  - print lines matching a pattern

*    

     tr - Translate, squeeze, and/or delete characters from standard input, writing to standard output.

     echo $PATH | tr ":" "\n"  -- separates the output by ":" and prints line by line

*

     wc - word calculator 
     - w (words)
     - l (lines)
     - c (bytes)
     - m (chars) print the character counts 

*

     comm - select or reject lines common to two files / compare two sorted files line by line (standart output is 3 columnes (unique for 1st file, unique for 2nd and lines that appear in both files) 

     comm -12 file1 file2  - Prints only lines in both file1 and file2

     comm -3 file1 file2 - Prints only lines in file1 not in file2, and vice versa

*

     uniq - report or omit repeated lines

*

     diff -r - to compare one dir to another ( recursively any subdirs found )
          -s reports when two files are the same
          -q brief. Reports only when files differ
          -y side-by-side output in two columnes
          -i ignore case differents in files

*

     echo "This is test" | cut -f 1 -d ' ' - where space is used as a delimiter

     cut -d, -f 2 ./dir/file  wc ( cut - remove sections from each line of files )

*

     split - split files into pieces 

*

     sed - text stream editor for filtering and transforming text
     sed OPTIONS ... [SCRIPT] [INPUT_FILE...]

     sed 's/unix/linux/' geekfile.txt - replace all occurences of "unix" with "linux"
     sed 's/unix/linux/1, /2' geekfile.txt - replace the 1-st & the 2-nd occurences of "unix" with "linux"

     sed 's/unix/linux/3g' geekfile.txt - replace all occurence from 3-rd one in a file
     sed '3 s/unix/linux/' geekfile.txt - replace on a specific line number
     sed '1,3 s/unix/linux/' geekfile.txt - replace on a range of lines
     sed '4,$ s/unix/linux/' geekfile.txt - replace from the 4-th line to the end of a file.

     sed '1 s/unix/linux/p' geekfile.txt - duplicate a specific line number
     sed -n 's/unix/linux/p' geekfile.txt - print lines that are going to be duplicated

     sed '5d' file.txt - delete 5-th line
     sed '$d' file.txt - delete the last line
     sed '3,6d' file.txt - delete on a range from 3 to 6 lines
     sed '12,$d' file.txt - delete from 12-th to the end of a file
     sed 'abc/d' file.txt - delete pattern matching line

          https://www.geeksforgeeks.org/sed-command-linux-set-2/?ref=rp

*

     shred - overwrite a file to hide its contents, and optionally delete it 

*

     string - shows only those lines that can be read as text (plain, probably)

     hexdump  - similar to the above one

*

     cat - concatenate files and and print on the standard output 

     cat /dev/null > file.txt - purge file's content 

     +

     tac - concatenate and print files in reverse / opposite to "cat" command 

*

     head -n 5 ./dir/name.txt

*

     tail -n 7 ./dir/name.txt

     tail -f/F log.txt - listen to changes in a file(in the last 10 lines of a file--> latest)

*

     less ./dir/file

     less seasonal/spring.csv seasonal/summer.csv - to view those two files in that order. Press spacebar to page down, :n to go to the second file, and :q to quit.

     less -f/F log.txt - listen to changes in a file

     Navigation:
               Ng - go to a N-th line
               g - to the beginning
               G - to the end

               /pattern - search forward
               ?pattern - search backward
               n - Repeat previous search
               N - Repeat previous search in reverse direction

               q - quit

*

     sort -n -r

     sort fileName  newSortedFile ; mv newSortedFile fileName 

*

     file ./bin - to determine type of the FILE CONTENT, not just file extension 


## <<2>> Kernel, date, time, locale

*
     uname -r  - to list a linux kernel in use
     uname -a - session information(kernel,architecture)

     lsb_release -a  - print distribution-specific information


     dpkg --list | grep linux-image - to list all installed linux kernels

     lsmod - shows which loadable kernel modules are currently loaded

     insmod - download mod into the memory by adding to the kernel 

     rmmod - simple programm to resolve a module from the Linux Kernel

*

     hostname - shows the system hostname 

     hostname -i - displays the IP address of the system

*

     modinfo - shows information about a Linux Kernel module

*

     runlevel - displays current running level of system

*

     echo 'wget -c http://www.example.com/files.iso' | at 09:00 - начать закачку в указанное время

     echo "$(tput setaf 1)Red text $(tput setab 7)and white background$(tput sgr 0)" - the way to set  a custom colour scheme for terminal output ( one time only, don't worry ) 

*

     date - show current date and time

* 

     uptime - current session duration 

* 

     timedatectl - Query and change the System clock 

*

     cal /or/ cal 7 2018 - display the current mounth or the significant month.

*

     last - displays all together reboots and system boots 

     last reboot - display the history of reboots and system loads 

* 

     systemd-analyze - display how much time takes the system for the boot.

     systemd-analyze blame - the same to the above but make a list of services 

     systemd-analyze plot > ~/logs/bootchart.svg - svg-compatible output generated by systemd-analyze command

     systemd-analyze critical-chain

*

     gnome-shell --version   - print a GNOME version in use

*

     Locale (lists locale(s) that are currently in use)

     Locale -a (displays all variables and their values)

     cat /etc/locale.gen

     sudo locale-gen ru_RU.UTF-8 (for example) 

     dpkg-reconfigure locales

*

     shutdown -h now - immediately shutdown the system

     shutdown -h 16:30 & - schedules the system for shutdown at 16:30

     shutdown -h +10 - shutting down the system after 10 min

     shutdown -c - to cancel scheduled shutdown

     shutdown -r now - system reboot

*

     sleep - suspend a script/command execution for an interval 

     sleep number[s/m/h/d] - sec, min, hours, days

     sleep 2 - sleeps for 2 seconds if suffix is not presented

     ls && sleep 2 && pwd - chaining commands with sleep

*

     at - execute a command at a later time 

*

     watch -  is used to execute a program/command periodically, showing output in fullscreen

     Options:

     -d - shows the difference between in the output
     -n - sets the interval in seconds
     -p - precise: watch attempts to run every interval seconds
     -t - no title: turns off the header showing the command, the interval etc
     -b - "beep": will give beep if the command's exit code isn't 0
     -e - exit: if error it wil freeze the execution and exit after a key press
     -g - executions stops if the output changes

*

     https://tecadmin.net/crontab-in-linux-with-20-examples-of-cron-schedule/

     Below example command will execute at 5 AM and 5 PM daily. You can specify multiple time stamps by comma-separated.

     0 5,17 * * * /scripts/script.sh

     * * * * * /scripts/script.sh; /scripts/scrit2.sh - scheduling multiple tasks in a single cron command 

     crontab -u ${username} -l (list) / -r (remove)


*

     dbus-monitor --system / or --session - display all system or session dbus logs in real time


*

Handling Cache and used space:

     1)	du -sh ~/.cache/thumbnails
          then remove

     2)	sudo du -sh /var/cache/apt
          sudo apt-get clean

     3) 	(unecessary dependencies and orphan packages)
               sudo apt autoremove --purge


     4)   (removing unused linux kernel images)

          sudo dpkg --list | grep 'linux-image-*'
          sudo dpkg --list 'linux-image-*'

               then
          sudo apt-get purge linux-image-VERSION
          sudo apt autoclean && sudo apt autoremove

*

## <<3>> USERS, GROUPS, PERMISSIONS

*

     sudo !! ( execute next commands as root )

     sudo -u richard whoami - run a sudo-ed command from a user(richard)//--> richard

###  SUDO in pipes:
          1) sudo sh -c 'echo "test" > /root/file.txt'  - running inside a new shell
          2) echo "test" | sudo tee /root/file.txt  - using tee command to redirect

### 5 ways of SUDO:  
     " He did hit on the main point, about one being a login shell and the other not.
     When running sudo -i the shell will become a login shell, and so it will read things like ~/.profile where as a non-login shell will only read ~/.bashrc.

     When chaining sudo with su (as in sudo su), neither the sudo nor the su invoke a login shell. The equivalent to sudo -i when using su would instead be sudo su -l.

     I personally consider sudo su to be along the lines of "useless use of cat" examples. You can get the same behavior with sudo -s.

     There are basically 5 common ways of invoking a root shell via sudo

###   sudo su

          non-login shell
          sets HOME to /root
          Prunes the environment

###     sudo -i

          login shell
          sets HOME to /root
          Prunes the environment

###   sudo su -l

          login shell
          sets HOME to /root
          Prunes the environment
          When invoking a shell, this is equivalent to sudo -i

###     sudo -s
          non-login shell
          sets HOME to /root
          Prunes the environment
          When invoking a shell, this is equivalent to sudo su

###    sudo -Es

     non-login shell
     Leaves HOME alone
     Leaves the environment alone (except for $PATH and $LD_LIBRARY_PATH iirc)

"



*    

     w - show who is logged on & what thery are doing
     w pulls information about the logged in users from the /var/run/utmp file.

     w [OPTIONS] [USER]

     Options:
          w -h - no header
          w -s - short          
          w -i - shows IP address instead of hostname

*

     login username 

     logout username - leave the current session  

*

     id - displays the details of the active user e.g. uid, gid and groups 

     id -gn username - which group a user belongs to
     id -u username - display user ID 
     id username

*

     !NOTE : you won't be able to use your newly created user until you provide a password for them.

     groupadd "admin" - adds the group admin 

     adduser "Sam" - adds user Sam 
     sudo passwd username - create a password for a user
 
     userdel "Sam" - deletes user Sam 

*

     usermod - used for changing modifying user information
     usermod -aG group username - add a user to a group granting sudo permissions


*

     who - shows who's logged in to the session 

     w - the same but is more informative one 

*

     whoami - displays who are you logged in as 

*

     passwd - set/change password 

*

     chroot - change root directory ( for safe sandboxing )

*

     chown - change the owner of a file or folder 

*


## <<4>> HARDWARE AND FIRMWARE

*

     sudo pacman -Sy hw-probe 

     sudo -E hw-probe -all -upload 

     https://linux-hardware.org/?probe=07b1242112 - 11.04.20 results 

* 

     sudo lshw - list all the hardware

*

     lscpu - list advanced CPU information

*

   cpu - check it out

*

     runlevel - displays current running level of system.

*

     grub-probe - probe device information for GRUB 

     grub-mkrescue - make a GRUB rescue image 

*

     df -h - displays information about mounted partitions and all, used and available space on them


     df -m - show all disk space (display in Mb)


*
     inxi -Fxz - call the list of system properies and parametrs with the using devices included(PCI  devices)

*

     dmidecode - show almost all information about hardware : motherboard,processor etc 

*

     iostat -Report Central Processing Unit (CPU) statistics and input/output statistics for devices and partitions.

*

     hostnamectl - control the system hostname also provides information about kernel, architecture, boot id, machine id 

     sudo hostnamectl set-hostname newName - to change a hostname 

*

     nproc - display number of available cores 

*

     lscpu - info about cpu

*

     cat /etc/os-release - variables for OS version, kernel, pretty name, version etc

*

     lspci - is a utility for displaying information about PCI buses in the system and devices connected to them. By default, it shows a brief list of devices. 

     lspci | grep VGA - to get my bus ID 

     lspci -k - display Kernel Drivers ( in use and loaded) for the hardware

     lspci -tv (tree like output)

*

     lsusb -tv  - displays USB devices in a tree-like diagram

     acpi - shows battery status and other ACPI information 

*
     dmesg - display all dignostic messages from tty1 into a current treminal which is running from Kernel Linux.

*

     badblocks -s /dev/xda - tests for unreadable blocks on disk

*
     prime-select query - shows which GPU is in use now

     prime-select intel|nvidia|on-demand  - switch a profile for GPU 


## <<5>> PACKAGE MANAGERS



     Package managers do : extracting, compiling(from the source to the binary code), decompressing if needed and track the changes.

*

     1) apt

          sudo apt add-apt-repository ppa:graphics-drivers/ppa
               apt policy - to list all ppas in use.

          sudo apt update

          sudo apt-get changelog PACKAGE

          sudo apt-get download PACKAGE (without installing)

          sudo apt install pkgName - to upgrade a specific package that is already installed

          sudo apt-get install packageName --only-upgrade ( do not innstall new packages but upgrade already installed )

          sudo apt-get install packageName --no-upgrade ( will prevent already installed packgaes from upgrading while installing some new )

          sudo apt update ----> sudo apt upgrade ----> sudo apt autoremove -----> 

          sudo apt-get install [a pakage]  

          apt list --installed

          grep " install " /var/log/apt/history.log - list recently installed packages

          sudo apt list --------->  apt show [a pakage] => get a full information about a pakage.


          apt-cache policy <pkg>    - shows installed & available versions for <pkg>

          apt-cache depends package - list dependencies

          apt-cache madison package - list available versions

          apt-cache rdepends --installed packagename - lists dependencies for an installed package (according to a real environment)

          sudo apt search [a pakage/string of pakage]

          apt list -a <pkg> to find out what versions are available

          !!! Preventing pkg from being upgraded &/OR dealing with Kept Back pkgs:
               Find out why it was held back:
                    a. dep conflict(see above for checking dependencies)
                    b. Marked to be held (
                         apt-mark showhold
                         sudo apt-mark hold/unhold <pkg>)
                    c. Phased Pkg(see below)

          !!! Phased packages:
               https://askubuntu.com/questions/1420969/how-to-force-packages-that-have-been-kept-back-to-be-installed-as-automat

          apt-cache policy <packagename>  - look for Phased %

          !!! Downgrades:
               apt-get install «pkg»=«version»

               or(a better option is):

               sudo aptitude install «pkg»=«version»

     2) snap

          snap list             - show installed snaps

          snap refresh --list   - display updates
          snap refresh --time   - show scheduled autoupgrades for snaps

          sudo snap set system refresh.timer=fri,21:00~23:00,,sat-sun,6:00~11:00,21:00~23:00

          snap changes          - display recent actions eg installed upgrades




     3) pacman 

          usage:  pacman <operation> [...]
          operations:
          pacman {-h --help}
          pacman {-V --version}
          pacman {-D --database} <options> <package(s)>
          pacman {-F --files}    [options] [package(s)]
          pacman {-Q --query}    [options] [package(s)]
          pacman {-R --remove}   [options] <package(s)>
          pacman {-S --sync}     [options] [package(s)]
          pacman {-T --deptest}  [options] [package(s)]
          pacman {-U --upgrade}  [options] <file(s)>

*
          sudo pacman -Sy hw-probe 

          sudo -E hw-probe -all -upload 

          https://linux-hardware.org/?probe=07b1242112 - 11.04.20 results 
*

     4) rpm

          rpm -V ${package} - to check changes in versions 
          rpm -qf /etc/passwd - check who's the owner of this file 

*

          rpm -i pkg_name.rpm  - Install an rpm package
          rpm -e pkg_name      - Removes an rpm package


     5) dpkg

          dpkg -i [package.deb] - install a package

          dpkg -r [package] - delete a package

*

          dpkg -l - lists all installed packages

          grep " install " /var/log/dpkg.log

          dpkg -l | grep httpd - outputs only lines matching an 'httpd' string

          dpkg -s [package] - show the information about a package

          dpkg -L [package] - lists all installed packages

          dpkg -S /bin/ping - find a package that owes a file or directory /bin/ping


     6) dnf 

          dnf install packageName - to install a package using dnf utility


## <<6>> FILE SYSTEM AND DISK SPACE

     GID, UID, PID, PPID - indexes 

*

/etc/fstab 

sudo mount | grep "/dev/sda" - list all mounted /dev/sda partitions

sudo mount -o rw /some/device/path - mount with Read/write permissions

sudo mount -o remount,rw /media/iarosb/device - remount with Read/Write permissions

*

     umask - DNAGEROUS ONE. Read the manual before using ( set file mode creation mask (or get))

* 

     chown - change the owner of a file or folder 

*

     chmod -  to change permissions for a file or folder 

     chmod + / - xwr ( where + means to add and - means to deny; x for execute, w for write and r for read )

     chmod R -rwx file_name/dir - to deny recursively 

*

     gzip file - to compress to a .gz file 

     unzip file1.zip - to unzip and unpack a zip-file 

     unzip -o \*.zip - to extract all files to the current directory and "-o" is used to override the existing directories(that have the same name/were created beforehand)

     for i in *.zip; do unzip "$i" -d "${i%%.zip}"; done  - extract all .zip files, each in a new folder with the same name.

     unrar x file1.rar - to unzip a rar-file

     tar -xvf archive.tar -C /tmp - to unzip a file into "/tmp"

     tar -xvfz archive.tar.gz - to unzip and unpack a compressed file


*

     gpg --ecnrypt --sign --armor -r gpgUsername some.txt --> encrypted file "some.txt.asc" in ASCII
     gpg -e -r gpgUSERNAME filename - encrypts
     gpg -c file_name - encrypts a file

     gpg -d -o ~/path/newFileName ~/path/encryptedFilename
     gpg -d ./filename > plain.txt
     gpg file_name.gpg - decrypts a file

*

     realpath - resolve a pathname (for both symbolic and hard links) 

*
     ls -S  - sort by file size, largest first
     ls -Q1  - "1" means listing one file per line; "Q" to enclose entry names in double quotes

     ls -a(All files) -R(with a tree of parents subdirectories) -i( show the I-node number of F) -l(shows as a list)  

     ls -lapt

     ls -alt ~/.local/share/Trash/files -list and sort all files in the Trash

*

     echo * - display names of all files in working directory

*

     vdir - list directory contents

*    

     sudo lsof -i -P -n | grep 22

     lsof - list open files (by all processes and users)

     lsof -p PIDnumber - display the list of files opened by the process PIDnumber

*
     cd .. 

     cd ../../(n) - up to the root <---u

     cd /**/**/(n) - down  u----> 

     cd -   - to the last used dir

     cd ~  - cd to Home 

*

     touch  newFile.whatever - creat an empty file with 

*

     mkfifo - make a FIFO special file ( a named pipe ).It's a pipe-like hole-file (check it out)

* 

     mkdir /home/bash/test/{foo,bar,baz,cat,dog}

     mkdir -p ./NewDir1/NewDir2/NewDir3

*

     ln -s(--symbolic) ./dir/or/file ./dir2/file2 - creating a symbolic link with the same PID with the origins File/Dir in selected directory/file

*

     cp seasonal/spring.csv seasonal/summer.csv backup 

     cp dir/* . - copy all files from dir/* to working directory(.)

     cp -a /tmp/dir1 . - copy dir1 and all its content recursively into the working dir(.)

     cp -a ./dir1 ./dir2 - copy dir1 into dir2 
     cp -R ./dir1 ./dir2 - copy all subdirectories and files of dir1 into dir2

*
     mv -t /dir file1 file2 file3

     mv text1.txt text2.txt ------> ls results: text2.txt only existing
     mv ./Dir1 ./Dir2 - move dir1 into dir2

     mv ./string*.jpg ./dir

     mv ./*png ./dir

     mv ./*jpg 

     mv *.png .. - move to one layer high 

*

     shred - remove files securely so that they can't be restored

*

        !  Hint: add -v (--verbose) to make it verbose or i to ignore 

     rm -rf ./(Remove Dir with all files + force)

     rm -rf dir1 dir2 - delete dir1 and dir2 directories with all theirs content recursively(including subfolders and their content)

     rm ./filename or all files in current directory also may be deleted type of files etc 

     rm ./dir/*.jpg

     rmdir ./(remove empty dir) 

*

     find . -type f -exec ls -s {} \; | sort -n -r | head -5    - find top 5 big files

     find . -type f -exec ls -s {} \; | sort -n | head -5    - find top 5 small files

     find . -maxdepth 3 -empty -not -name ".*" - lists only NOT hidden empty files in next 3 levels from ./

     find -maxdepth 4 -not -iname "NAME" - invert matching results 

     find -maxdepth 2 -iname NameOfFile  - will control the serch depth

     find -mindepth 3 -maxdepth 5 -iname NameOfFile  - (search only on 3 to 5 levels from root)

     find -iname ( will be Ignoring Case)

     find /Dir/Dir2 -name '*.jpg' - to find all files that have extansion *.jpg in target directory

     find -type f -name '*.jpg' | rename 's/\string1/string2/' 

     find ./Dir/ -name 'String*.jpg' 

     find -type f  -name '1450648861.jpg' 

     find /usr/bin -type f -atime +100 - search in /usr/bin for all files that haven't been used for more than 100 days.

     find ./'Kate <3' -type f -atime -10 - find all files are last used less than 10 days ago.
     
     find /usr/bin -type f -mtime -10 - search in /usr/bin for all files that have been created or modified in last 10 days.

     find ./dir/dir2 -name \*.jpg -print('print' is active as default option)

     find ~/1*/**/ -type f -name '*hd*' (the example of inetresting syntax)



     ? - one any symbol 

     * - any string of symbols 

     '*999*' 

     '?*999.png' 

     dir/*

     '/**' = '/*/*.../n' 

*

     rename 'y/A-Z/a-z/' *jpg 

     rename 'y/0-9/999/' *jpg 

     rename 's/\.jpeg$/.jpg/' *  (Rename any files with the extension ".jpeg" to have the extension ".jpg.")

     find -type f -name '*.jpg' | rename 's/holiday/money/' - for all files with ext. ".jpg",IF they contain the string "holiday" replace it with "money". For insance this command would rename the file "ourholiday001.jpg" to "ourmoney001.jpg". 

     rename 's/\.bak$//' *.bak - Rename all files matching "*.bak" to strip the file name of its extension. For instance, this command would rename the file "project.bak" to "project".

     rename ./Dir/'y/A-Z/a-z/' * - Rename files such that all uppercase letters are changed to their lowercase equivalents.



     https://www.computerhope.com/unix/rename.htm

*


     df -h - displays the information about mounted partitions and their total space amount (+ used and free space)

*

     du - estimate file space usage 

     du -ch 

     du -sh dir1 - calculate and displays the amount of space is used by dir1 (-h for human-readable output and -s for separating by directories)

*

     lsblk - partition manager 

     lsblk -f  - display partition type and used space in % 

*

     df -h - human readable(use with caution in scripts)

     df -m - show all disk space (display in Mb)

*

     fdisk - changing of the disk partition (it's DANGEROUS one)

     fdisk -l - display partitions 

*

     fsck - checking a file sistem for errors (it may causes some damage)

*

     parted - partition manipulation program

*

     findmnt - display target mount point for all filesystems 

*

     rsync -a /home/apps /backup - synchronize contents in /home/apps directory with /backup directory 

*

     file fileName.example - shows the information about file content(encoding type)

*

     /var/log/syslog - logs for application level information
     /var/log/dmesg  - logs for close to the hardware information

     /var/log/auth.log - logs for authentication attempts via ports open to the internet (eg using ssh)

     dmesg - command to show logs for hardware level events

     journalctl serviceName - display information about a service
     journalctl -fu serviceName - real-time log stream that outputs only specific to a service information

*

     swapon -s  -- lists the size of a swap file (usually located at /proc/swaps)

*


## <<7>> PROCESSES AND MEMORY

*

     renice 19 PID - makes a process run with very low priority (CPU time for a process)

*
     ! NOTE: both these commands can be used to restart a stopped process(no arguments)
          bg
          fg
     ! NOTE: use %[number] to specify a job


     bg - run jobs in the background (bg process can't handle stdin(from input devices) and take it to the terminal); there could be many of them using one terminal(tty)

     fg - run jobs in the foreground (fg process can handle stdin(from input devices) and take it to the terminal) There could be the only using terminal(tty) at one time 

     (ctrl + Z  to stop)

     fg %1  - bring the background job with id 1 to the foreground


     commandName -run a command bin-file (firefox for example) 

     commandName & - run a command in background 

     %n & - put a process "n" in background without stopping it 

     %n - put a command "n" in foreground 

*

     exec - execute commands and open, close, or copy file descriptors

*

     fork - create a child process (new process with a given PPID + ) 

*

     loop - loop devices (or processes ) 

*

     xargs - executes commands from standard input 

*

     pidof NAME - find the process ID of a running program

*

     cat /proc/PID/cmdline - to find a name of a process by its PID

*

     pidstat - report statistics for Linux tasks with PID,CPU,UID and name of commands are involved

*

     free -m/h - display some information about total,free and used RAM in Mb/human-readable

*

     pgrep name - get a process PID 

*

     Xorg - X server 

     xserver - X Window System display server 


*

     xdg-open - opens a file or URL in user's preferred application

     xdg-desktop-menu (1) - command line tool for (un)installing desktop menu items

*

     xterm - start X terminal in a new window 

*

     xmessage - display a message in x window 

*

     xwininfo - xproperty displayer 

     xprop - property displayer for X 

*

     xlsclients -l

*

     xinput --list 

     xinput --list-props 8 (device ID) 

     xinput --set-prop (dangerous one )

*

     xmodmap (run carefully) - show or change the current keybord shortcuts for the X environment

     setxkbmap (dangerous one)) -set a new keybord shortcuts for the X environment 

* 

     xev

     xev -id (ID) - where ID would has been taken from xwininfo output 

* 

     startx - initialize an X session

     startx - :1 ( create new X -session)

* 

     jobs - display all jobs in the current shell

     jobs -l - list jobs with their PIDs
     jobs -s - stopped jobs
     jobs -r - running jobs
     jobs -p - only PIDs of the jobs

     jobs -n - This shows the jobs that have changed their status since the last notification. For example, a job that has changed from a running to a stopped state.


     ! Note: to list a PID of a piped process use
          jobs -x echo %1
      %1 is for first job in chain, %2 for second, etc. jobs -x replaces job specifier with PID.(doesn't work quite well when the first process is done and the n-th is stopped)

*

     pstree - makes a tree of processes depends

     ps -ef -f - list all running processes
     ps -f -u iarosb - list processes running under a user
     ps -C processName - list by name
     ps -C processName -o pid,args --no-headers  - process by name output only pid + args, hide headers

     ps -f -p 1,2,3  - list information about a process by ID
     ps -p 3150 -L - display all threads which a process with "3150" ID is running on

     ps -eafw -!! ADD DETAILED EXPlANATION ABOUT FLAGS in details !!

     отобразить запущенные процессы, используемые ими ресурсы и другую полезную информацию (единожды)

     By GPU consumption:
          ps auxf | sort -nr -k 4
          ps auxf | sort -nr -k 4 | head -10

     By CPU consumption:
          ps auxf | sort -nr -k 3
          ps auxf | sort -nr -k 3 | head -10

     ps --no-headers -o comm 1 - outputs an init system that is used by OS

     ps -e -o pid,args --forest -  display all processes with their PIDs as a tree.

     ps -aj (all jobs)

     ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head -display top 10 processses by using memory and cpu 

     ps --ppid ${number} - gives us the processes running on bash shell with PID ${number}

*

     top - displays processes, RAM, CPU load and other information with live updating in a terminal 

* 

     htop - displays processes, RAM, CPU load and other information with live updating in a terminal. Pseudo-graphical 

*

     kill -STOP $(jobs -pr)  - stop currently running process (even if it's in the background)

     kill %% - kills currently running job
     kill %?gnome-calculator  - kills using a substring

     kill -9 $(jobs -p -s)  - kills all stopped jobs in the current shell

     kill -9 $(pidof NAME)     
     
     kill -9 PIDnumber /OR/ kill -kill PIDnumber - kill a process unsafelly 

     kill PIDnumber(because of the default is -TERM) /OR/ kill -TERM PIDnumber - kill a process correctly.

     kill -9 -1 - kill all processes you can kill(except the kill process itself and init)

     killall -9 Viber

*

     systemd-analyze - display how much time takes the system for the boot.

     systemd-analyze blame - the same to the above but make a list of services 

*

          WARNING! There're  differences: 
     systemctl (1)        - Control the systemd system and service manager

     sysctl (8)           - configure kernel parameters at runtime
     sysctl (2)           - read/write system parameters
     @
     
     sudo systemctl list-units --type service

     sudo systemctl list-units --type=service --state=running|active|exited|loaded

     sudo systemctl enable/disable service(with it's daemons)

     _____(List : 

     disabled: bluetooth.service (!)
     _____)   

     sudo sysctl vm.swapiness - displays a current rate of swapining

     sudo systcl vm.vfs_cashe_pressure - displays a current value of holding a cash-data

     systemctl list-dependencies some.service = lists services that some.service is configured to wait for(e.g. at boot time)

     systemctl list-dependencies --reverse some.service = lists services that are configured to wait for "some.service" to finish(e.g. at boot time)


*

     sudo sync; echo 1 > /proc/sys/vm/drop_cashes - cleaning of page cash

     sudo echo > 200 



## <<8>> NETWORKING


     /etc/networks

https://www.ubuntupit.com/useful-linux-network-commands-for-modern-sysadmins/

https://www.fosslinux.com/42935/linux-networking-commands.htm

*

     hosts - static table lookup for hostnames

*

     host example.com - resolves IP address

*

     telnet - UI to Telnet server

     telnet host - connect to host via telnet default port 23 

*

     ufw status verbose
     ufw status numbered

     ufw allow from 127.17.0.2 to 127.0.0.1 port 8080 proto tcp
     ufw allow proto tcp from any to any port 80,443

     ufw app list
     ufw allow OpenSSH 

     ufw allow port 22 (--> SSH)
     ufw allow port 443 (--> SSH)

* 

     ssh-keygen -f ./.ssh/id_rsa -p - change private passphrase for SSH

     /etc/ssh/sshd_config  - a config for ssh daemon

     ssh user_name@host(IP/Domain_name)- securely connect to host as user

     ssh -p port_number user@host - securely connect to host using a specific port

     ssh host - securely connect to the system via SHH default port 22

*
     dig facebook.com [a, any etc]
     dig @198.41.0.4 www.facebook.com // ipv4
     dig @2001:503:a83e::2:30 www.facebook.com // ipv6
     dig -x host - performs reverse lookup on a domain

*

     arp - linux address resolution protocol module

     arp -n   - show IPs instead of host names

*

     ssh - OpenSSH remote login client



*
     https://www.tecmint.com/nmap-command-examples/

     https://securitytrails.com/blog/nmap-commands

     nmap - network mapping tool that is used to scan ports (it's illegal in the US)

*

     nload - monitor a network bandwith

*

     netstat - netstat - Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships
     Netstat  prints  information about the Linux networking subsystem.  The type of information printed is controlled by the first argument.

     netstat -antu

     netstat -pnltu - displays all active listening ports

     netstat -rn -f inet - shows the default routes to diffrenet destinations stored in the Kernel IP routing table

     sudo netstat -pna | grep " 22 " - lists daemonds listening on a specific port number

*
     wpa_supplicant

*

     dhclient 

*

     rfkill - tool for enabling and disabling wireless devices 

*

     arp 192.168.0.1 - get mac address of IP

*

     ip a (all)

     ip n (replace IPs with domain names)

     ip r (routes)

     ip link show

     ip address show/ ip addr

     ip address a(add???) 192.168.102.125/24 broadcast 192.168.102.255 dev wlp3s0 - ( adding an IP after turning the state of an interface UP/DOWN)

     ip link set dev Interface up ----> ip rout add default via 192.168.102.1(an example)

     ifup/ifdown

     sudo ifconfig wlp3s0 down/up 

*

     ping -c 3 ipAddress - ping an address with 3 packets

*

     route - Kernel IP routing table lookup tool

*

     tracerout www.example.com -n


*

     telnet ipAddress 112 - a CLI interface to the communication protocol TELNET (provides a bidirectional text-based connection )

*

     ss - is  used  to  dump socket statistics. It allows showing information similar to netstat.  It can display more TCP and state informations than other tools

*

     echo 'wget -c http://www.example.com/files.iso' | at 09:00 - to schedule a download at 9:00(am)

*

     wget file_name - downloads a file from an online source 

     wget -r http://www.example.com - to dowload a content from example.com recursively
     
     wget -c http://www.example.com/file.iso - to download a file from example.com with the ability to stop it anytime you wish and then continue again later

*

     host google.com  - performs an IP lookup for the domain name 

*
     /etc/resolv.conf  - DNS resolution config

     sudo systemctl restart systemd-resolved.service

*

     whois domain - retrieves more information about a domain name 

*

     mail - send mails over SMPT from terminal (and many more) 
*

     egrep "^(ftp|http|smtp|ssh).*tcp" /etc/services 



## <<9>> VI + VIM

     https://devhints.io/vim - vim cheatsheet 

     https://devhints.io/vimscript  - integration in automation and scripting using Vim 
     :/SEARCHPATTERN
     :help  "object"

### Modes:
 	: - command mode
	/ - search forward
	? - search backward
	

### Movement:
	gg - go to the begin of the document
	G  - go to the end of the document
	^  - go to the begin of the line
	$  - go to the end of the line
 	(  - go to the begin of the sentence
	)  - go to the end of the sentence
	h  - cursor left
	l  - cursor right
	j  - cursor down
	k  - cursor up
	w  - advance a single word
	b  - go back a single word
	
### Actions:
	x - delete the character after the cursor position
     w - hop one word forward
     b - hop one word backword
	dw - delete an entire word
	dd - delete an entire line
	r - replace a single character
     	u - undone one action
	U - undone all actions to the last checkpoint
     	i - insert
     	o - open(new line + insert)
	O - open a line above for adding text
        a - append
    	c - change(for example "c)" - change all words till the begin of the current line or another example of usage: "c5w" - means change the last 5 words )
	d - delete a character
	y - yank(similar to copying)
     3yy - yank three lines down
     3yw - yank 3 words ahead
	yy - yank an entire line(including a newline character)
     yiw - yank the current word (the cursor is at)
	yw - yank an entire word
     y^ - yank to the beginning of the current line
	y$ - yank to the end of the current line
	p - put data from clipboard
	. - means the current line(where the cursor is now)	
	% - the whole document


     :w(rite) ./File_name
     :wq(write +quit
     Esc
     "Ctrl + C" = terminate  a current working command

     _________#some examples of usage:
     :s/\.$/.../ - means changing of the s(ubstitute) to value after "/" thus all symbols "." in current line are going to be replaced to "..."
     :/Eample1/,$d Enter




## <<10>> OTHER

     JUST A HINT :  rename kernels I like the most and store them into the specific folder(don't forget to suggest them custom names that will represent date, kernel version and a build source(e.g. community, cannonical or smh else )

*
     groff - front-end for the groff document formatting system

*
     make - utility to maintain and build binaries (packages)
*
     source - evaluate a file or resource as a Tcl script

*