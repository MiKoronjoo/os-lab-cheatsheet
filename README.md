# OS LAB cheat sheet

### Lesson 1
1. **ls** - list directory contents \
    ls [OPTION]... [FILE]... \
    List information about the FILEs (the current directory by default).
    1. **ls**: displays files in a bare format
    ```
    $ ls
    README.md
    ```
    2. **ls -l**: long format, displaying Unix file types, permissions, number of hard links, owner, group, size, last-modified date and filename
    ```
    $ ls -l
    total 0
    -rw-r--r-- 1 hassan hassan 0 Aug   13 23:55 README.md
    ```
2. **pwd** - print name of current/working directory \
    pwd [OPTION]... \
    Print the full filename of the current working directory.
    ```
    $ pwd
    /home/hassan/os-lab-cheatsheet
    ```
3. **cd** - change directory \
    cd DIRECTORY... \
    Change the current working directory to given directory (home directory by default).
4. **mkdir** - make directories \
    mkdir [OPTION]... DIRECTORY... \
    Create the DIRECTORY(ies), if they do not already exist.
    ```
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
    ```
    $ touch file.txt
    ```
7. **cp** - copy files and directories \
    cp [OPTION]... [-T] SOURCE DEST \
    Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.
    ```
    $ cp README.md test
    ```
##### Note: You should use `sudo` before your commad when you want to run the command under the root permission. Also switch to root user with `sudo -i`. Use `exit` or CTRL+D to exit from root shell.
