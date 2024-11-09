
Name: Noppanat Sripan  
Student ID: A01373963  

Assignment 2 contains the following folders:
- project 1
- project 2  

To run the following scripts inside these folders, users are required to:
1. Use the Arch Linux operating system with Bash.
2. Have `sudo` privileges.
3. Have execute permission for the scripts.

### Project 1
Project 1 contains 4 files:
- autoSymbolicLink
- installpackage
- main
- packagelist

Before running the scripts in Project 1:
1. Clone `2420-as2-starting-files` from https://gitlab.com/cit2420/2420-as2-starting-files.git.
2. Move the files to the home directory:  
   `/home/user/2420-as2-starting-files`

#### autoSymbolicLink

**NAME**  
autoSymbolicLink - creates symbolic links from the `2420-as2-starting-files` directory.

**SYNOPSIS**
```bash
sudo ./autoSymbolicLink <username>
```

**DESCRIPTION**  
This script sets up a user’s environment by creating links to important configuration files. It first checks if a "2420-as2-starting-files" directory exists and confirms that the provided username is valid. If both checks pass, the script creates links from the starter files to the user’s home directory.
```bash
.bashrc -> /home/username/2420-as2-starting-files/home/bashrc
bin -> /home/username/2420-as2-starting-files/bin
.config -> /home/username/2420-as2-starting-files/config
```

**EXAMPLE**  
To create symbolic links for the user `tom`:
```bash
sudo ./autoSymbolicLink tom
```

### installpackage
installpackage is a script that allows users to install packages from a file containing the names of the packages they want to install. The installpackage script reads the provided file and installs each package listed.

**NAME**  
installpackage - installs packages from a file containing a list of package names.

**DESCRIPTION**  
The script identifies package names in the file that are missing (i.e., not yet installed), checks their availability in the repositories, and then installs them. Additionally, it can install a predefined set of default packages. It provides output on the status of each package installation.

**EXAMPLE**  
To install packages listed in the file `mypackage`:
```bash
sudo ./installpackage mypackage
```

> [!IMPORTANT]  
> The file must contain one package name per line, as shown in the example below:

Example:
```text
nvim
git
bob
```

### main
**NAME**  
main - runs autoSymbolicLink and installpackage using flags.

**SYNOPSIS**
```bash
sudo ./main [Option]... [File]...
```

**DESCRIPTION**  
This script uses flags to run commands from autoSymbolicLink and installpackage, allowing users to install packages and create symbolic links to configuration files.

`-s <username>` : Creates symbolic links from the starter file to the user’s configuration:
- Creates a symbolic link from the starter file pointing to `bin`.
- Creates a symbolic link from the starter file pointing to `.bashrc`.
- Creates a symbolic link from the starter file pointing to `.config`.
- NOTE: To use this command, you need to have a folder named `2420-as2-starting-files` in the home directory.

`-p <filename>` : Installs packages (including default packages) from a file containing package names.
- NOTE: The file must contain one package name per line.

**EXAMPLE**  
To create symbolic links using the autoSymbolicLink script:
```bash
sudo ./main -s tom
```

To install packages from a file:
```bash
sudo ./main -p packagelist
```

note: In the GitHub repository, there is an example that can be used as the packagelist file.
### Project 2
Project 2 contains one file:
- userset

users are required to:
1. Use the Arch Linux operating system with Bash.
2. Have `sudo` privileges.
3. Have execute permission for the scripts.
#### userset

**NAME**  
userset - creates a new user.

**SYNOPSIS**
```bash
sudo ./userset [OPTION]...
```

**DESCRIPTION**  
This script generates a unique user ID and group ID, creates a home directory for the user, and updates essential system files like `/etc/passwd` and `/etc/group` with the user’s information.

`-m <username>` : Creates a user with a home directory (required).  
`-s <shellpath>` : Specifies the shell path for the user (optional).  
`-g <groupname>` : Adds the user to an existing group (optional).  
`-c <comment>` : Adds a comment to the user’s details (optional).

Note: The script always requires users to use the `sudo` command and specify flag `-m`. If the user doesn’t provide a specific shell path, it will default to `/bin/bash`.

**EXAMPLE**

To create a user:
```bash
sudo ./userset -m tom
```

To create a user with a specified shell path and add them to groups "arch" and "wheel" with a comment:
```bash
sudo ./userset -m tom2 -s /bin/bash -g "arch wheel" -c "mysecondGroup"
```
