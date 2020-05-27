CONTENTS:
1)Bash
2)Session
3)Hardware and firmware
4)Package managers(rpm, atp, dpkg, pacman)
5)File system and disk space
6)Processes and memory
7)Networking
8)Vi + Vim
9)Other


**/ BASH /**


* 

     stty - changes and prints terminal line settings (for the control sequences)
     stty -a  - prints all 


     bind -l - lists all readlines in Bash session 
     bind -p  - displays all control sequences' keys and their meanings (.inputrc)

     +


     ctrl + R - to redraw (when control sequences 

     ctrl + U - to delete a whole line in terminal 

     ctrl + W - to delete a word (from right to left)

     crtl + Z - to stop a process 

     crtl + C  - to abort from a process 

     ctrl + D - to send an interrupt message 

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

     alias (show all alias)

     alias neWname='someCommand'

     unalias commandName

     unalias -a ( "-a" means all)

     alias lf='ls -alF | sort'

*

     pwd - print working directory 

*

     whereis (object or bash-file)

     which commandName - show a full path to binaries of the command 

*

     clear - clear a terminal screen

*

     history - list all used commands ( their number is limited and they are stored in )

* 

     dmesg - display all dignostic messages from tty1 into a current treminal which is running from Kernel Linux.

*

     commandName -run a command bin-file (firefox for example) 

     commandName & - run a command in a background 

     +

     %jobName & - put a job in background  (not stopping it)

     %jobName - put a job in foreground 

*

     yes - output a string repeatedly until killed 

*

     look - display lines beginning with a given string (look up for a given string or a word in a file)

*

     tee  - duplicate stnd input / duplicate pipe content / read from standard input and write into output and        files 

*

     dircolors - colour setup for ls (perhaps it's useless)

*

     grep linux file*.{txt,htm*} - search for all strings that contain "linux" in a current directory

     grep -h -v 2017-07  - print lines matching a pattern 

          ‘-v’
          ‘--invert-match’
               Invert the sense of matching, to select non-matching lines.  (‘-v’
               is specified by POSIX.)

          ‘-w’
          ‘--word-regexp’
               Select only those lines containing matches that form whole words.
               The test is that the matching substring must either be at the
               beginning of the line, or preceded by a non-word constituent
               character.  Similarly, it must be either at the end of the line or
               followed by a non-word constituent character.  Word-constituent
               characters are letters, digits, and the underscore.  This option
               has no effect if ‘-x’ is also specified.

          ‘-L’
          ‘--files-without-match’
               Suppress normal output; instead print the name of each input file
               from which no output would normally have been printed.  The
               scanning of each file stops on the first match.

          ‘-l’
          ‘--files-with-matches’
               Suppress normal output; instead print the name of each input file
               from which output would normally have been printed.  The scanning
               of each file stops on the first match.  (‘-l’ is specified by
               POSIX.)

          ‘-n’
          ‘--line-number’
               Prefix each line of output with the 1-based line number within its
               input file.  (‘-n’ is specified by POSIX.)

          ‘-q’
          ‘--quiet’
          ‘--silent’
               Quiet; do not write anything to standard output.  Exit immediately
               with zero status if any match is found, even if an error was
               detected.  Also see the ‘-s’ or ‘--no-messages’ option.  (‘-q’ is
               specified by POSIX.)


          ‘-s’
          ‘--no-messages’
               Suppress error messages about nonexistent or unreadable files.
               Portability note: unlike GNU ‘grep’, 7th Edition Unix ‘grep’ did
               not conform to POSIX, because it lacked ‘-q’ and its ‘-s’ option
               behaved like GNU ‘grep’’s ‘-q’ option.(1)  USG-style ‘grep’ also
               lacked ‘-q’ but its ‘-s’ option behaved like GNU ‘grep’’s.
               Portable shell scripts should avoid both ‘-q’ and ‘-s’ and should
               redirect standard and error output to ‘/dev/null’ instead.  (‘-s’
               is specified by POSIX.)

          ‘-H’
          ‘--with-filename’
               Print the file name for each match.  This is the default when there
               is more than one file to search.

          ‘-h’
          ‘--no-filename’
               Suppress the prefixing of file names on output.  This is the
               default when there is only one file (or only standard input) to
               search.

               
*    

     wc - word calculator 
     - w (words
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

     diff -r - to compare one dir to another (recursively any subdirs found ) 
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

     sed - stream editor for filtering and transforming text


     https://www.geeksforgeeks.org/sed-command-in-linux-unix-with-examples/

     https://www.geeksforgeeks.org/sed-command-linux-set-2/?ref=rp

     *

     shred - overwrite a file to hide its contents, and optionally delete it 

     *

     string - shows only those lines that can be read as text (plain, probably)

     hexdump  - similar to the above one 

     *

     cat - concatenate files and and print on the standard output 

     cat /dev/null > file.txt - purge file's content 

     *

     tac - reversed output from cat 

     *

     head -n 5 ./dir/name.txt

     *

     tail -n 7 ./dir/name.txt

     *

     less ./dir/file
     
     less seasonal/spring.csv seasonal/summer.csv - to view those two files in that order. Press spacebar to page down, :n to go to the second file, and :q to quit.

     *

     sort -n -r 

     sort < file > newSortedFile ; mv newSortedFile file 

     *
     file  

     file ./bin - to determine type of the FILE CONTENT, not just file extension 

     *






     You can add an attribute by using "$" 

     The variable "$?" keeps last used command's exit-code (0, 1 etc) 
     ___1 example :

     LEVEL="1 ; 2 ; 3 ; 4"
     printf "$i" $LEVEL ( use "$s" for a string of values) 

     "0; 1; 2; 3; ;4"  - is output of this 

     NOTE! Hence printf didn't interpretered 0,1,2,3,4 as distinct values. The solution is to put the Variable( $LEVEL ) under quotes like this : 
     printf "$s" "$LEVEL" 

     ____2 example : 

     LEVEL=5
     FLAG_MESSAGE="I've done with ""$LEVEL"".I deserve appreciation" ( or ${$LEVEL} to get the "LEVEL 5" as output) 
     printf "$s" "$FLAG_MESSAGE" 

     "I've done with LEVEL5. I deserve appreciation" - is the output 

     also "$q" to ensure every space between words in output and "%c" for a single character : printf "$c" "\" 



     export PATH="$PATH:/sbin" - set default directory for futher searching of binaries.

     A= 5 
     B= 3 

     *
     !!! important one 

     https://stackoverflow.com/questions/4651437/how-do-i-set-a-variable-to-the-output-of-a-command-in-bash?noredirect=1&lq=1

     * 

     VARIABLES: NAME="John" 
     
     call a variable : 
     echo "I'm $NAME" 
          !!!   but '' single quotes override it with a "I'm $NAME" output 
          !!!  `` acute or back quotes serve only for functions (thus commands also) 
     
     call a function :  
     1)echo "I'm in $(pwd)" 
     2) echo "I'm in `pwd`"

     BRACE EXPANSION:  //  https://wiki.bash-hackers.org/syntax/expansion/brace
     echo {A,B}.js  ---> "A.js  B.js"
     echo {1..5} ---> "1 2 3 4 5" // for ranges 
     echo {A, B} ---> "A B" 
     echo {str1,...,str2,str3} // for string list
     
     echo {{A..Z},{a..z}} ---> The whole latin alphabet 

     mkdir /home/bash/test/{foo,bar,baz,cat,dog}

     for i in {0..10}; do printf "%s\n"  "$i"; done  -->
     1
     2
     3
     4
     ...
     10





**/ SESSION /**
     
     ctr + alt + Fn - open the virtual console number n
     

*

     sudo SuperUser execution for an entering comand (1)

     sudo su (after that all commands will be execute from SUPERUSER/mounted(?))

     sudo !! ( execute next commands as root )


*

     echo 'wget -c http://www.example.com/files.iso' | at 09:00 - начать закачку в указанное время

     echo "$(tput setaf 1)Red text $(tput setab 7)and white background$(tput sgr 0)" - the way to set  a custom colour scheme for terminal output ( one time only, don't worry ) 

     *

     login username 

     logout username - leave the current session  

*

     id - displays the details of the active user e.g. uid, gid and groups 

*

     groupadd "admin" - adds the group admin 

     adduser "Sam" - adds user Sam 

     userdel "Sam" - deletes user Sam 

*

     usermod - used for changing modifying user information 

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

     uname -a - session information(kernel,architecture)

*

     hostname - shows the system hostname 

     hostname -i - displays the IP address of the system 


*

     modinfo - shows information about a Linux Kernel module

*

     runlevel - displays current running level of system

* 

     lsmod - shows which loadable kernel modules are currently loaded

     insmod - download mod into the memory by adding to the kernel 

     rmmod - simple programm to resolve a module from the Linux Kernel 

*

     systemd-analyze - display how much time takes the system for the boot.

     systemd-analyze blame - the same to the above but make a list of services 

*

     Locale

     Locale -a 

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

     sleep - suspend execution for an interval 

*

     at - execute a command at a later time 

* 

     https://tecadmin.net/crontab-in-linux-with-20-examples-of-cron-schedule/

     Below example command will execute at 5 AM and 5 PM daily. You can specify multiple time stamps by comma-separated.

     0 5,17 * * * /scripts/script.sh

     * * * * * /scripts/script.sh; /scripts/scrit2.sh - scheduling multiple tasks in a single cron command 

     crontab -u ${username} -l (list) / -r (remove)


*

     dbus-monitor --system / or --session - display all system or session dbus logs in real time 


*


 

 
 





**/ HARDWARE AND FIRMWARE /**

*

     sudo pacman -Sy hw-probe 
     
     sudo -E hw-probe -all -upload 
     
     https://linux-hardware.org/?probe=07b1242112 - 11.04.20 results 
     
* 

     sudo lshw - list all the hardware

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












**/ PACKAGE MANAGERS /**

*

     Package managers do : extracting, compiling(from the source to the binary code), decompressing if needed and track the changes.

*

     1) apt 

          sudo apt add-apt-repository ppa:graphics-drivers/ppa 

          sudo apt update

          sudo apt-get changelog PACKAGE

          sudo apt-get download PACKAGE (without installing)

          sudo apt-get install packageName --only-upgrade ( do not innstall new packages but upgrade already installed )

          sudo apt-get install packageName --no-upgrade ( will prevent already installed packgaes from upgrading while installing some new ) 

          sudo apt update ----> sudo apt upgrade ----> sudo apt autoremove -----> 

          Usage: apt command [options]
               apt help command [options]

          Commands:
          add-repository   - Add entries to apt sources.list
          autoclean        - Erase old downloaded archive files
          autoremove       - Remove automatically all unused packages
          build            - Build binary or source packages from sources
          build-dep        - Configure build-dependencies for source packages
          changelog        - View a package's changelog
          check            - Verify that there are no broken dependencies
          clean            - Erase downloaded archive files
          contains         - List packages containing a file
          content          - List files contained in a package
          deb              - Install a .deb package
          depends          - Show raw dependency information for a package
          dist-upgrade     - Upgrade the system by removing/installing/upgrading packages
          download         - Download the .deb file for a package
          edit-sources     - Edit /etc/apt/sources.list with your preferred text editor
          dselect-upgrade  - Follow dselect selections
          full-upgrade     - Same as 'dist-upgrade'
          held             - List all held packages
          help             - Show help for a command
          hold             - Hold a package
          install          - Install/upgrade packages
          list             - List packages based on package names
          policy           - Show policy settings
          purge            - Remove packages and their configuration files
          recommends       - List missing recommended packages for a particular package
          rdepends         - Show reverse dependency information for a package
          reinstall        - Download and (possibly) reinstall a currently installed package
          remove           - Remove packages
          search           - Search for a package by name and/or expression
          show             - Display detailed information about a package
          showhold         - Same as 'held'
          source           - Download source archives
          sources          - Same as 'edit-sources'
          unhold           - Unhold a package
          update           - Download lists of new/upgradable packages
          upgrade          - Perform a safe upgrade
          version          - Show the installed version of a package

          sudo apt-get install [a pakage]  

          sudo apt list --------->  apt show [a pakage] => get a full information about a pakage.

          sudo apt search [a pakage/string of pakage]


     2) pacman 

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

     3) rpm

          rpm -V ${package} - to check changes in versions 
          rpm -qf /etc/passwd - check who's the owner of this file 

*

          rpm -i pkg_name.rpm  - Install an rpm package
          rpm -e pkg_name      - Removes an rpm package


     4) dpkg 


          dpkg -i [package.deb] - install a package

          dpkg -r [package] - delete a package

*

          dpkg -l - lists all installed packages

          dpkg -l | grep httpd - outputs only lines matching an 'httpd' string

          dpkg -s [package] - show the information about a package

          dpkg -L [package] - lists all installed packages

          dpkg -S /bin/ping - find a package that owes a file or directory /bin/ping


     5) dnf 

          dnf install packageName - to install a package using dnf utility 



**/ FILE SYSTEM AND DISK SPACE /**

     GID, UID, PID, PPID - indexes 

*

     umask - DNAGEROUS ONE. Read the manual out before use ( set file mode creation mask (or get)) 

* 

     chown - change the owner of a file or folder 

*

     chmod -  to change permissions for a file or folder 

     chmod + / - xwr ( where + means to add and - means to deny; x for execute, w for write and r for read )

     chmod R -rwx file_name/dir - to deny recursively 

*

     gzip file - to compress to a .gz file 

     unzip file1.zip - to unzip and unpack a zip-file 

     unrar x file1.rar - to unzip a rar-file
     
     tar -xvf archive.tar -C /tmp - to unzip a file into "/tmp"
     
     tar -xvfz archive.tar.gz - to unzip and unpack a compressed file


*

     gpg -c file_name - encrypts a file 

     gpg file_name.gpg - decrypts a file

*

     realpath - resolve a pathname (for both symbolic and hard links) 

*

     ls -a(All files) -R(with a tree of parents subdirectories) -i( show the I-node number of F) -l(shows as a list)  

     ls -lapt

     ls -alt ~/.local/share/Trash/files -list and sort all files in the Trash

*

     echo * - display names of all files in working directory

*

     vdir - list directory contents

*

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

     mv text1.txt text2.txt ------> ls results: text2.txt only existing
     mv ./Dir1 ./Dir2 - move dir1 into dir2

     mv ./string*.jpg ./dir

     mv ./*png ./dir

     mv ./*jpg 

     mv *.png .. - move to one layer high 

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

     du -sh dir1 - calculate and displays the amount of space is used by dir1 

*

     lsblk - partition manager 

     lsblk -f  - display partition type and used space in % 

*

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









**/ PROCESSES AND MEMORY /**

*

     renice 19 PID - makes a process run with very low priority (CPU time for a process)

*

     bg - run jobs in the background (bg process can't handle stdin(from input devices) and take it to the terminal); there could be many of them using one terminal(tty)

     fg - run jobs in the foreground (fg process can handle stdin(from input devices) and take it to the terminal) There could be the only using terminal(tty) at one time 

     (ctrl + Z  to stop) 


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

     jobs - display working programms

*

     pstree - makes a tree of processes depends

     ps ux - to check all the processes running under a user 





     ps -eafw -!! ADD DETAILED EXPlANATION ABOUT FLAGS in details !!

     отобразить запущенные процессы, используемые ими ресурсы и другую полезную информацию (единожды) 






     ps -e -o pid,args --forest -  display all processes with their PIDs as a tree.

     ps -f - display full running processes with their PID's and PPD's and also UID's

     ps -aj (all jobs)

     ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head -display top 10 processses by using memory and cpu 

     ps --ppid ${number} - gives us the processes running on bash shell with PID ${number}

*

     top - displays processes, RAM, CPU load and other information with live updating in a terminal 

* 

     htop - displays processes, RAM, CPU load and other information with live updating in a terminal. Pseudo-graphical 

*
     
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

     sudo systemctl enable/disable service(with it's daemons)

     _____(List : 

     disabled: bluetooth.service (!)
     _____)   

     sudo sysctl vm.swapiness - displays a current rate of swapining

     sudo systcl vm.vfs_cashe_pressure - displays a current value of holding a cash-data

*

     sudo sync; echo 1 > /proc/sys/vm/drop_cashes - cleaning of page cash

     sudo echo > 200 



**/ NETWORKING /**

*

     hosts - static table lookup for hostnames

*

     telnet - UI to Telnet server

     telnet host - connect to host via telnet default port 23 

*

     ssh user_name@host(IP/Domain_name)- securely connect to host as user

     ssh -p port_number user@host - securely connect to host using a specific port 

     ssh host - securely connect to the system via SHH default port 22 

*

     dig 

*

     tracerout 

*

     ssh - OpenSSH remote login client


*

     nmap

*

     netstat - netstat - Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships
     Netstat  prints  information about the Linux networking subsystem.  The type of information printed is controlled by the first argument.

     netstat -antu

     netstat -pnltu - displays all active listening ports 

*
     wpa_supplicant 

*

     dhclient 

*

     rfkill - tool for enabling and disabling wireless devices 

*

     ip a

     ip n 

     ip r

     ip link show

     ip address show 

     ip link set dev Interface up ----> ip rout add default via 192.168.102.1(an example)

     ifup/ifdown 

     sudo ifconfig wlp3s0 down/up 

*
     ping c1(not a "L" letter) 192.186.1.1(an example) - display the reachability of the IP address

*

     tracerout www.ru -n 


*

     ip address a(add???) 192.168.102.125/24 broadcast 192.168.102.255 dev wlp3s0 - (an example of adding the IP after turning the state of an interface UP/DOWN)

*

     telnet 192.168.102.1 112(an example)

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

     whois domain - retrieves more information about a domain name 

*

     dig domain - retrieves DNS information about the domain name 

     dig -x host - performs reverse lookup on a domain 

*

     egrep "^(ftp|http|smtp|ssh).*tcp" /etc/services 



**/ VI + VIM /**

     https://devhints.io/vim - vim cheatsheet 

     https://devhints.io/vimscript  - integration in automation and scripting using Vim 

     :help  "object"
     set "option" (set showmode)
     i - insert
     a - append
     o - open(new line + insert)
     :w(rite) ./File_name
     :wq(write +quit
     Esc
     "Ctrl + C" = terminate  a current working command
     gg - go to the begin of the text
     G - go to the end of the text
     ^ - go to the begin of the line 
     $ - go to the end of the line 
     ( - go to the begin of the sentence
     ) - go to the end of the sentence
     / - search straight directed from the cursor position 
     ? - search back directed from the cursor position 
     c - change(for example "c)" - change all words till the begin of the current line or another example of usage: "c5w" - means change the last 5 words )
     d - delete (has the same usage in manner like above)
     dd - delete  the current line 
     y - yank (kinda like a copy).It has the same usage like was described above.
     p - put (a data was copied ) 
     . - means the current line (where's the cursor now)
     $ - the last line 
     % - a whole document 

     _________#some examples of usage:
     :s/\.$/.../ - means changing of the s(ubstitute) to value after "/" thus all symbols "." in current line are going to be replaced to "..."
     :/Eample1/,$d Enter




 **/ OTHER /**

     JUST A HINT :  rename kernels I like the most and store them into the specific folder(don't forget to suggest them custom names that will represent date, kernel version and a build source(e.g. community, cannonical or smh else )

*
     groff - front-end for the groff document formatting system

*
     make - utility to maintain and build binaries (packages)
*
     source - evaluate a file or resource as a Tcl script
