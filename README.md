# OS LAB cheat sheet

### Lesson 1
1. **ls** - list directory contents \
    ls [OPTION]... [FILE]... \
    List information about the FILEs (the current directory by default).
    1. **ls**: displays files in a bare format
    ```sh
    $ ls
    README.md
    ```
    2. **ls -l**: long format, displaying Unix file types, permissions, number of hard links, owner, group, size, last-modified date and filename
    ```sh
    $ ls -l
    total 0
    -rw-r--r-- 1 hassan hassan 0 Aug   13 23:55 README.md
    ```
2. **pwd** - print name of current/working directory \
    pwd [OPTION]... \
    Print the full filename of the current working directory.
    ```sh
    $ pwd
    /home/hassan/os-lab-cheatsheet
    ```
3. **cd** - change directory \
    cd DIRECTORY... \
    Change the current working directory to given directory (home directory by default).
4. **mkdir** - make directories \
    mkdir [OPTION]... DIRECTORY... \
    Create the DIRECTORY(ies), if they do not already exist.
    ```sh
    $ mkdir test
    $ ls
    README.md  test
    ```
5. **rm** - remove files or directories \
    rm [OPTION]... [FILE]... \
    rm removes each specified file.  By default, it does not remove directories.
    1. **rm -r**: remove directories and their contents recursively
    2. **rm -f**: ignore nonexistent files and arguments, never prompt
    3. **rm -rf**: remove directories and their contents recursively, by force
6. **touch** - change file timestamps \
    touch [OPTION]... FILE...
    1. **touch**: a FILE argument that does not exist is created empty
    ```sh
    $ touch file.txt
    ```
7. **cp** - copy files and directories \
    cp [OPTION]... [-T] SOURCE DEST \
    Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.
    ```sh
    $ cp README.md test
    ```
##### Note:
1. You should use `sudo` before your commad when you want to run the command under the root permission. Also switch to root user with `sudo -i`. Use `exit` or `CTRL+D` to exit from root shell.
2. In terminal, `.` means current working directory and `..` means parent of current directory.
    ```sh
    $ pwd
    /home/hassan/os-lab-cheatsheet
    $ cd ../..
    $ pwd
    /home
    ```
### Lesson 2
1. File permissions in Linux/Unix: \
    The first set of three permissions, after the place for d, applies to the **owner** of the file \
    The second set of three permissions applies to the all users who are members of the **group** of the file \
    The third set of three permissions applies to **others** \
    ![alt tag](https://helpdeskgeek.com/wp-content/pictures/2017/02/file-permissions-explanation.png.webp)
    1. **Read**: This permission give you the authority to open and read a file. Read permission on a directory gives you the ability to lists its content.
    2. **Write**: The write permission gives you the authority to modify the contents of a file. The write permission on a directory gives you the authority to add, remove and rename files stored in the directory.
    3. **Execute**: In Unix/Linux, you cannot run a program unless the execute permission is set. If the execute permission is not set, you might still be able to see/modify the program code(provided read & write permissions are set), but not run it.
2. Number of each permission:
    | Number | Permission Type | Symbol |
    |:-------------:|:-------------:|:-----:|
    | 0 | No Permission | --- |
    | 1 | Execute | --x |
    | 2 | Write | -w- |
    | 3 | Execute + Write | -wx |
    | 4 | Read | r-- |
    | 5 | Read + Execute | r-x |
    | 6 | Read + Write | rw- |
    | 7 | Read + Write + Execute | rwx |

3. **chmod** - change file mode bits \
    chmod [OPTION]... MODE[,MODE]... FILE... \
    chmod changes the file mode bits of each given file according to mode, which can  be  either  a  symbolic representation of changes to make, or an octal number representing the bit pattern for the new mode bits.
    ```sh
    $ chmod 755 README.md
    ``` 
    ![alt tag](https://files.virgool.io/upload/users/57785/posts/ci1wifitikyz/emwv6xwxrd74.png)
4. **groupmod** - modify a group definition on the system \
    groupmod [options] GROUP \
    The groupmod command modifies the definition of the specified GROUP by modifying the appropriate entry in the group database.
    ```sh
    $ groupadd new_group
    ```
5. **groups** - print the groups a user is in \
    groups [OPTION]... [USERNAME]... \
    Print group memberships for each USERNAME or, if no USERNAME is specified, for the current process (which may differ if the groups database has changed).
    ```sh
    $ groups hassan
    hassan : hassan adm cdrom sudo dip plugdev lpadmin sambashare
    ```
6. **useradd** - create a new user or update default new user information \
    useradd [options] LOGIN
    useradd is a low level utility for adding users. On Debian, administrators should usually use adduser(8) instead.
7. **adduser**, **addgroup** - add a user or group to the system \
    adduser [options] user group \
    adduser and addgroup add users and groups to the system according to command line options and configuration information in /etc/adduser.conf. They are friendlier front ends to the low  level  tools like  **useradd**,  **groupadd**  and  **usermod**  programs.
    ```sh
    $ adduser new_user
    ```
7. **usermod** - modify a user account \
    usermod [options] LOGIN \
    The usermod command modifies the system account files to reflect the changes that are specified on the command line.
    1. **usermod -G GROUP1[,GROUP2,...[,GROUPN]]]**: new list of supplementary GROUPS
    2. **usermod -a USER**: add the USER to the supplementary group(s). Use only with the -G option
    ```sh
    $ usermod -G new_group -a new_user
    ```

### Lesson 3
1. **ps** - report a snapshot of the current processes. \
    ps [options] \
    ps displays information about a selection of the active processes.
    ```sh
    $ ps
      PID TTY          TIME CMD
    18920 pts/3    00:00:00 zsh
    18968 pts/3    00:00:00 ps
    ```
    1. **ps -l**: long format
    ```sh
    F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
    0 S  1000 19749 19738  0  80   0 -  6679 sigsus pts/2    00:00:00 zsh
    4 R  1000 19962 19749  0  80   0 -  5709 -      pts/2    00:00:00 ps
    ```
    2. **ps -f**: full-format, including command lines
    ```sh
    $ ps -f
    UID        PID  PPID  C STIME TTY          TIME CMD
    hassan   18920 18534  7 16:04 pts/3    00:00:00 zsh
    hassan   18956 18920  0 16:04 pts/3    00:00:00 ps -f
    ```
    3. **ps -t**: all processes on this terminal
    ```sh
    $ ps -t
      PID TTY      STAT   TIME COMMAND
    18920 pts/3    Ss     0:00 zsh
    19193 pts/3    R+     0:00 ps -t
    ```
    4. **ps -r**: only running processes
    ```sh
    $ ps -r
      PID TTY      STAT   TIME COMMAND
    19245 pts/3    R+     0:00 ps -r
    ```
    5. **ps -e**: all processes
    6. **ps aux**: \
        a = show processes for all users \
        u = display the process's user/owner \
        x = also show processes not attached to a terminal \
        use **grep** for searching from command output
    ```sh
    $ ps aux | grep zoom
    hassan   13232 33.9  3.9 5151328 484560 tty2   SLl+ 14:41  43:40 /opt/zoom/zoom
    hassan   22290  0.0  0.0  20476  2900 pts/3    S+   16:50   0:00 grep --color=auto --exclude-dir=.bzr --exclude-dir=CVS --exclude-dir=.git --exclude-dir=.hg --exclude-dir=.svn zoom
    ```

### Lesson 4
1. **kill** - send a signal to a process \
    kill [options] <pid> [...] \
    The  default  signal  for kill is TERM. Use -l or -L to list available signals.
    ```sh
    $ kill -l
    HUP INT QUIT ILL TRAP ABRT BUS FPE KILL USR1 SEGV USR2 PIPE ALRM TERM STKFLT CHLD CONT STOP TSTP TTIN TTOU URG XCPU XFSZ VTALRM PROF WINCH POLL PWR SYS
    ```
    1. **kill PID**: terminate a process with PID
    ```sh
    $ kill 13232
    ```
    2. **killall PNAME**: terminate all processes with PNAME
    ```sh
    $ killall zoom
    ```
2. **xkill** - kill a client by its X resource \
    xkill is a utility used for force-quitting GUI apps. It is handy when some app isn't responding or is causing your system to work abnormally.
3. **pstree** - display a tree of processes \
    pstree shows running processes as a tree.
4. **ping** - send ICMP ECHO_REQUEST to network hosts \
    ping uses the ICMP protocol's mandatory ECHO_REQUEST datagram to elicit an ICMP ECHO_RESPONSE from a host or gateway. 
    ```sh
    $ ping api.telegram.org
    PING api.telegram.org (149.154.167.220) 56(84) bytes of data.
    64 bytes from 149.154.167.220 (149.154.167.220): icmp_seq=1 ttl=50 time=12.9 ms
    64 bytes from 149.154.167.220 (149.154.167.220): icmp_seq=2 ttl=50 time=13.6 ms
    64 bytes from 149.154.167.220 (149.154.167.220): icmp_seq=3 ttl=50 time=13.1 ms
    64 bytes from 149.154.167.220 (149.154.167.220): icmp_seq=4 ttl=50 time=12.10 ms
    64 bytes from 149.154.167.220 (149.154.167.220): icmp_seq=5 ttl=50 time=13.1 ms
    64 bytes from 149.154.167.220 (149.154.167.220): icmp_seq=6 ttl=50 time=12.10 ms
    ```

### Lesson 5
1. **Foreground** and **Background** Processes: \
    Foreground processes refer to applications you are running that you are currently interacting with, and which applies equally to graphical user interfaces as it does to the command line. Background processes refer to applications that are running but not being interacted with by the user.
2. **nano** - Nano's ANOther editor, an enhanced free Pico clone \
    nano is a small and friendly editor.
    1. **nano FILE**: open FILE with nano (create the FILE if is not exists)
    ```sh
    $ nano script.sh
    ```
3. **cat** - concatenate files and print on the standard output \
    cat [OPTION]... [FILE]... \
    Concatenate FILE(s) to standard output.
    ```sh
    $ cat script.sh
    ping google.com > res.out
    ```
4. **jobs** - display the status of jobs in the current shell
    ```sh
    $ jobs
    [1]  + suspended  ./script.sh
    ```
5. **bg** - move jobs to the background \
    1. **bg %jobID**
    ```sh
    $ bg %1
    [1]  + 28975 continued  ./script.sh
    ```
6. **fg** - move jobs to the foreground \
    1. **fg %jobID**
    ```sh
    $ fg %1
    [1]  + 28975 running    ./script.sh
    ```
#### Note:
1. You can suspend a job with `CTRL+Z`
2. You can end a job with `CTRL+C`

