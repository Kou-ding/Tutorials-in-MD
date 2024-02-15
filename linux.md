# Linux Essentials

## Path
$ export PATH=$PATH:/home/avinash/Desktop/raj
>adds raj in the path

$ export PATH=${PATH%:/home/avinash/Desktop/raj}
>removes raj from the path

or just reset Path to the previous paths excluding the one ou want to remove
$ export PATH=/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games


While installation is complete, your system will need to be able to find the julia executable. This can be done by adding the full path of Julia’s bin directory to the PATH environment variable ~/.bashrc. This is one of the locations Linux allows adjustments to your PATH. Open it using nano or your preferred text editor:

	$ nano .bashrc

Add this line to the bottom of the file, using the julia directory you installed Julia to as the basis:

	$ export PATH="$PATH:/home/sammy/julia-1.8.1/bin"

You are required to use the absolute path to your bin folder. In this example, the home directory is used, so be sure to update the directory name accordingly if you chose a different location for your julia directory.

Once you are done, save and exit by pressing CTRL+O then CTRL+X.

In order for this change to go into effect, you have to source your .bashrc file:

	source .bashrc

Now your system can find the julia executable.

## Place matlab resides to delete
~/.local/share/applications
## Change Directory (cd)

    The cd command changes your current directory. 
    In other words, it moves you to a new place in the filesystem.
    If you are changing to a directory that is within your current directory, 
    you can simply type cd and the name of the other directory.

    $ cd Downloads

    If you are changing to a directory elsewhere within the filesystem directory tree, 
    provide the path to the directory with a leading /.

    $ cd /usr/local/bin

    To quickly return to your home directory, use the ~ (tilde) character as the directory name.

    $ cd ~ or $ cd

    You can use the double dot symbol .. 
    to represent the parent of the current directory. 
    You can type the following command to go up a directory:

    $ cd ..

## List Directories (ls)
    To list the files and folders in the current directory:

    $ ls

    To list the files and folders in the current directory with a 
    detailed listing use the -l (long) option:

    $ ls -l

    To use human-friendly file sizes include the -h (human) option:

    $ ls -lh

    To include hidden files use the -a (all files) option:

    $ ls -lha

## Change mode (chmod)
    This command sets the user permissions so that you can run and edit the file.

    $ sudo chmod +x <filename>

    Replace "<filename>" with the actual name of the file (it cannot contain any spaces). 

    To run the app

    $ sudo ./<filename>

## Exit terminal (exit)
    The exit command will close a terminal window, end the execution 
    of a shell script, or log you out of an SSH remote access session.

    $ exit

## Find (find)
    Use the find command to track down files that you know exist 
    if you can’t remember where you put them. 
    You must tell find where to start searching from 
    and what it is looking for. In this example, the . matches the current folder 
    and the -name option tells find to look for files with a name that matches the search pattern.

    You can use wildcards, where * represents any sequence of characters 
    and ? represents any single character. We’re using *ones* to match any file name 
    containing the sequence “ones.” This would match words like bones, stones, and lonesome.

    $ find . -name *ones*

    As we can see, find has returned a list of matches. 
    One of them is a directory called Ramones. 
    We can tell find to restrict the search to files only. 
    We do this using the -type option with the f parameter. 
    The f parameter stands for files.

    $ find . -type f -name *ones*

    If you want the search to be case insensitive use the -iname (insensitive name) option.

    $ find . -iname *wild*

## User Info (finger)
    The finger command gives you a short dump of information about a user,
    including the time of the user’s last login, 
    the user’s home directory, and the user account’s full name.

    $ finger

## Memory usage (free)
    The free command gives you a summary of the memory usage
    with your computer. It does this for both the main 
    Random Access Memory (RAM) and swap memory. The -h (human) option 
    is used to provide human-friendly numbers and units. 
    Without this option, the figures are presented in bytes.

    $ free -h

## Gnu Zip (gzip)
    To compress a single file invoke the gzip command followed by the filename:

    $ gzip filename

    If you want to keep the input (original) file, use the -k option:

    $ gzip -k filename
 
    To decompress a .gz file , use the -d option: (-d:decompress)

    $ gzip -d filename.gz	

## History (history)
    The history command lists the commands you have previously 
    issued on the command line. You can repeat any of the commands 
    from your history by typing an exclamation point ! and the number 
    of the command from the history list.

    !188

    Typing two exclamation points repeats your previous command.

    !!

## Kill program (kill)
    The kill command allows you to terminate a process from the command line. 
    You do this by providing the process ID (PID) of the process to kill. 
    Don’t kill processes willy-nilly. You need to have a good reason to do so. 
    In this example, we’ll pretend the shutter program has locked up.

    To find the PID of shutter we’ll use our ps and grep trick from the section 
    about the alias command, above. We can search for the shutter process and obtain its PID as follows:

    $ ps -e | grep shutter.

    Once we have determined the PID—1692 in this case—we can kill it as follows:

    $ kill 1692

## Manual (man)
    The man command displays the “man pages” for a command in less . The man pages 
    are the user manual for that command. Because man uses less to display the man 
    pages, you can use the search capabilities of less.

    For example, to see the man pages for chown, use the following command:

    $ man chown

    Use the Up and Down arrow or PgUp and PgDn keys to scroll through the 
    document. Press q to quit the man page or pressh for help.

## Make directory (mkdir)
    To create a new directory in the current directory

    $ mkdir <directory_name>

## Move (mv)
    The mv command allows you to move files and directories 
    from directory to directory. It also allows you to rename files.

    To move a file you must tell mv where the file is and where you want it to be moved to. 
    In this example, we’re moving a file called apache.pdf 
    from the “~/Document” directory and placing it 
    in the current directory, represented by the single . character.

    $ mv ~/Documents/this_document.pdf .

    To rename the file, you “move” it into a new file with the new name.

    $ mv this_document.pdf this_document(renamed).pdf

    The file move and rename action could have been achieved in one step:

    $ mv ~/Documents/this_document.pdf ./this_document(renamed).pdf

## Copy (cp)
    $ cp source_file target_directory

## Remove (rm)
    Removing one file at a time
    $ rm a.txt

    Removing an empty directory using the rm command

    $ rm -d <directory_name>

    Using the -r flag removes the entire directory, including subdirectories and files, 
    while the -v flag lists each step of the process as the output:

    $ rm -r -v <directory_name>

## Passwaord (passwd)
    The passwd command lets you change the password for a user. 
    Just type passwd to change your own password.

    You can also change the password of another user account, 
    but you must use sudo. You will be asked to enter the new password twice.

    $ sudo passwd mary

## Ping (ping)
    The ping command lets you verify that you have network connectivity 
    with another network device. It is commonly used to help troubleshoot 
    networking issues. To use ping, provide the IP address or machine name of the other device.

    $ ping 192.168.4.18

    The ping command will run until you stop it with Ctrl+C.

    Here’s what’s going on here:

    The device at IP address 192.168.4.18 is responding to our ping requests and is sending back packets of 64 bytes.
    The Internet Control Messaging Protocol (ICMP) sequence numbering allows us to check for missed responses (dropped packets).
    The TTL figure is the “time to live” for a packet. Each time the packet goes through a router, it is (supposed to be) decremented by one. If it reaches zero the packet is thrown away. The aim of this is to prevent network loopback problems from flooding the network.
    The time value is the duration of the round trip from your computer to the device and back. Simply put, the lower this time, the better.

    To ask ping to run for a specific number of ping attempts, use the -c (count) option.

    ping -c 5 192.168.4.18

    To hear a ping, use the -a (audible) option.

    ping -a 192.168.4.18

## Print working directory (pwd)
    Nice and simple, the pwd command prints the working directory 
    (the current directory) from the root / directory.

    $ pwd

## Shutdown (shutdown)
    The shutdown command lets you shut down or reboot your Linux system.

    Using shutdown with no parameters will shut down your computer in one minute.

    $ shutdown

    To shut down immediately, use the now parameter.

    $ shutdown now

    You can also schedule a shutdown and inform any logged in users of the pending shutdown. To let the shutdown command know when you want it to shut down, you provide it with a time. This can be a set number of minutes from now, such as +90 or a precise time, like 23:00. Any text message you provide is broadcast to logged in users.

    shutdown 23:00 Shutdown tonight at 23:00, save your work and log out before then!

    shutdown 23:00 with message

    To cancel a shutdown, use the -c (cancel) option. Here we have scheduled a shutdown for fifteen minutes time from now—and then changed our minds.

    shutdown +15 Shutting down in 15 minutes!

    shutdown -c

    Shutdown -c cancel command

## Reboot (reboot)
    $ reboot
    to reboot immidiately use
    $ reboot now

## Secure Shell (SSH)
    Use the ssh command to make a connection to a remote Linux computer and log into your account. To make a connection, you must provide your user name and the IP address or domain name of the remote computer. In this example, the user mary is logging into the computer at 192.168.4.23. Once the connection is established, she is asked for her password.

    $ssh mary@192.168.4.23

    Mary issues the w command to list the current users on the remote access system. She is listed as being connected from pts/1, which is a pseudo-terminal slave. That is, it is not a terminal directly connected to the computer.

    To close the session, mary types exit and is returned to the shell on her own computer.

    $w

    $exit

## Super user do (sudo)
    The sudo command is required when performing actions that require root or superuser permissions, such as changing the password for another user.

    $ sudo passwd mary

## Tape archive (tar)
    A tar.gz file is a combination of a .tar file and a .gz file. It is an archive file 
    with several other files inside it, which is then compressed.
    You can unzip these files the same way you would unzip a regular zipped file:

    tar –xvzf documents.tar.gz

## Top (top)
    The top command shows you a real-time display of the data relating to your Linux machine. The top of the screen is a status summary.

    The first line shows you the time and how long your computer has been running for, how many users are logged into it, and what the load average has been over the past one, five, and fifteen minutes.

    The second line shows the number of tasks and their states: running, stopped, sleeping and zombie.

    The third line shows CPU information. Here’s what the fields mean:

    us: value is the CPU time the CPU spends executing processes for users, in “user space”
    sy: value is the CPU time spent on running system “kernel space” processes
    ni: value is the CPU time spent on executing processes with a manually set nice value
    id: is the amount of CPU idle time
    wa: value is the time the CPU spends waiting for I/O to complete
    hi: The CPU time spent servicing hardware interrupts
    si: The CPU time spent servicing software interrupts
    st: The CPU time lost due to running virtual machines (“steal time”)

    The fourth line shows the total amount of physical memory, and how much is free, used and buffered or cached.

    The fifth line shows the total amount of swap memory, and how much is free, used and available  (taking into account memory that is expected to be recoverable from caches).

    The user has pressed the E key to change the display into more humanly digestible figures instead of long integers representing bytes.

    The columns in the main display are made up of:

    PID: Process ID
    USER: Name of the owner of the process
    PR: Process priority
    NI: The nice value of the process
    VIRT: Virtual memory used by the process
    RES: Resident memory used by the process
    SHR: Shared memory used by the process
    S: Status of the process. See the list below of the values this field can take
    %CPU: the share of CPU time used by the process since last update
    %MEM: share of physical memory used
    TIME+: total CPU time used by the task in hundredths of a second
    COMMAND: command name or command line (name + options)

    (The command column didn’t fit into the screenshot.)

    The status of the process can be one of:

    D: Uninterruptible sleep
    R: Running
    S: Sleeping
    T: Traced (stopped)
    Z: Zombie

    Press the Q key to exit from top.

## Unix name (uname)
    Unix is a family of multitasking, multiuser computer operating systems that derive from the original AT&T Unix, whose development started in 1969 at the Bell Labs research center. 
    You can obtain some system information regarding the Linux computer you’re working on with the uname command.

    Use the -a (all) option to see everything.
    Use the -s (kernel name) option to see the type of kernel.
    Use the -r (kernel release) option to see the kernel release.
    Use the -v (kernel version) option to see the kernel version.

    uname -a

    uname -s

    uname -r

    uname -v

## What (w)
    The w command lists the currently logged in users.

    $ w

## Logged in accounts (whoami)
    Use whoami to find out who you are logged in as or who is logged into an unmanned Linux terminal.

    $ whoami
