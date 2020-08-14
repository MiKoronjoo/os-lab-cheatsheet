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
1. You should use `sudo` before your commad when you want to run the command under the root permission. Also switch to root user with `sudo -i`. Use `exit` or CTRL+D to exit from root shell.
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
