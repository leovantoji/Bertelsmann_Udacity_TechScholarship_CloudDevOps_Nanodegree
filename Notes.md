## Shell Workshop
- A **shell** is simply the outermost layer of an operating system. It's designed to provide a way for you to interact with the tools and services that your operating system provides. One of the most widely used shells is called **BASH**, and it is a **case sensitive** language.
- **Graphical User Interface (GUI)** is a user interface where you give instructions to the computer by interacting with things like windows, menus, icons, and buttons. **GUI** is pronounced as "gooey".
- **Command-Line Interface (CLI)** is a user interface where you give instructions to the computer by entering lines of text. 
- Double exclamation mark (**!!**) substitutes in whatever your last command was. An example:
  - Enter `echo hello` command.
  ```
  ~$ echo hello
  hello
  ```
  - Then, enter `!!` by itself.
  ```
  ~$ !!
  echo hello
  echo
  ```
  - The `!!` command replaces itself with the last command and execute the last command.
- Assign a number to a variable in BASH: 
  ```
  ~$ x=100
  ~$ echo $x
  100
  ```
- Size of the terminal: `~$ echo $COLUMNS x $LINES`
- **Navigating directories** with:
  - `ls`: lists the contents of the current directory.
  - `cd Downloads`: moves to the `Downloads` directory.
  - `cd ..`: goes up one directory (move to the parent directory).
  - `ls ..`: lists the contents of the parent directory.
  - `;`: allows commands to be written in the same line. The shell will just run them in order.
  - `pwd`: shows the name of the **working directory**.
  - `ls ~`: lists the contents of the home directory.
- Directory terminologies:
  - `.` or **working directory** is the directory you're currently inside.
  - `..` or **parent directory** is the directory immediately above your current directory. 
  - `~` (tilde) or **home directory** is the current user's top-level directory (the directory that has all that user's other directories inside it).
- **Absolute vs. relative path**:
  - A *partial path*, which is **relative** to *wherever you're currently located*, can be given to the directory you want to go, as long as the partial path includes all the steps needed to get there.
  - An **absolute** path is a full path all the way from the **home** directory.
- **Organizing files** with `mkdir` (make directory) and `mv` (move).
  - Make a new directory called `Photos`.
  - Move all of the `.jpg` files into the `Photos` directory.
  - Make a new directory called `Animations`.
  - Move all of the `.gif` files into the `Animations` directory.
  ```
  ~$ mkdir Photos
  ~$ mv ./*.jpg ./Photos/
  ~$ mkdir Animations
  ~$ mv ./*.gif ./Animations/
  ```
- **Download files** with `curl` (C URL → See URL). `curl` is very useful for downloading files or pages by URL. An example: 
  ```
  ~$ curl -o google.html -L 'http://google.com'
  ```
- When you put a URL into the address bar of your browser, you're essentially reaching out to a server somewhere and asking for it to send back the Web page for that address. A **redirect (-L)** is when, instead of sending back the page you asked for, the server redirects you to a different address.
- By default, `curl` will output whatever it downloads directly to the terminal. This typically results in a big mess of code filling up your terminal window. As this is not particularly useful, you can tell `curl` to output the data to a file by adding the `-o` option.
- Use `curl` to download the data and output it to a file name `dictionary.txt`.
  ```
  ~/Desktop$ curl -L -o dictionary.txt 'https://tinyurl.com/zeyq9vc'
  ```
- **Viewing files** with `cat` and `less`. The `cat` command displays the full contents of the file. Nonetheless, texts in files often can't fit on the screen at once. In such scenario, the `less` command becomes useful.
- Different keys to move around while in `less` program:
  - Scroll down with **Spacebar** or **down arrow**.
  - Scroll up with `b` key or **up arrow**.
  - Search with **Forward slash** `/`.
  - Exit `less` with `q` key.
- **Remove files** with `rm` and `rmdir` with caution as these 2 commands **permanently delete** files. `rmdir` only deletes *empty* directory.
  - `~$ rm example`: permanently delete a file named `example` without double-checking.
  - `~$ rm -i example`: permanently delete a file named `example`, but double-check first.
  - `~$ rmdir example`: permanently delete a directory named `example`.
- Other resources:
  - [The Bash Academy](https://www.bash.academy/)
  - [Bash Beginners Guide](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/)
  - [Bash Programming HOWTO](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
  - [Corey Schafer: Customize the terminal](https://www.youtube.com/watch?v=LXgXV7YmSiU)
  - [Ubuntu Bash Colors](https://wiki.ubuntuusers.de/Bash/Prompt/)

## Version Control
- **Version Control System (VCS)** or **Source Code Manager (SCM)** allows you to:
  - Revert files to a previous state.
  - Revert the entire project to a previous state.
  - Review changes made over time.
  - See who last modified something that might be causing a problem.
  - Identify when an issue was introduced.
  - Do many more things.
- [Wikipedia](https://en.wikipedia.org/wiki/Version_control): **Version Control** also known as *revision control* or *source control*, is the management of changes to documents, computer programs, large web sites, and other collections of information.
- Common version control systems are **Git**, *Subversion*, and *Mercurial*.
- 2 main types of version control system models:
  - **Centralized model**: all users connect to a central, master repository.
  - **Distributed model**: each user has the entire repository on their computer.
- **Git** is the version control tool, while **GitHub** is the service that hosts Git projects.
- Key terminologies:
  - **Commit (snapshot)**: Git thinks of its data like a set of snapshots of a mini file system. Every time you commit, or save the state of your project in Git, it basically takes a picture of what all your files look like at that moment and stores a reference to that snapshot. When a commit is made, only the changes that are in the **Staging index** are saved in the repo.
  - **Repository (repo)**: A directory that contains your project work, as well as a few files (hidden by default in Mac OS X) which are used to communicate with Git. Repositories can exist either locally on your computer or as a remote copy on another computer.
  - **Working directory**: The files that you see in your computer's file system. 
  - **Checkout**: When content in the repository has been copied to the **Working directory**. It is possible to checkout many things from a repo. These include a file, a commit, a branch, etc.
  - **Staging area**, **Staging index**, or **Index**: A file in the Git directory that stores information about what will go into your next commit. You can think of the staging area as a prep table where Git will take the next commit. Files on the **Staging Area** are poised to be added to the repo.
  - **SHA**: is a 40-character ID number for each commit. SHA is composed of numbers (0-9) and latin characters (a-z), and calculated based on the contents of a file or directory structure in Git. An example of SHA: *e2adf8ae3e2e4ed40add75cc44cf9d0a869afeb6*.
  - **Branch**: When a new line of development is created and diverges from the main line of development, a branch is created. This alternative line of development can continue without altering the main line.
  
## Git Repo
- `.git` directory contents:
  - **config file**: project specific configuration settings are stored here.
  - **description file**: only used by GitWeb program.
  - **hooks directory**: this is where we could place client-side or server-side scripts that we can use to hook into Git's different lifecycle events.
  - **info directory**: contains the global excludes file.
  - **objects directory**: stores all of the commits we make.
  - **refs directory**: holds pointers to commits (i.e. branches and tags).
- Other resources:
  - [Git Internals - Plumbing and Porcelain](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain)
  - [Customizing Git - Git Hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)
- Use `git init` command to create a new empty repo in the current directory.
- Use `git clone <path-to-repo-to-clone> <new-repo-name>` to clone the repo into a directory under a different name. 
- Use `git status` command to know what's going on with a repo.
- Use `git log` command to display all of the commits of a repo. By default, this command displays the SHA, the author, the date, and the message of every commit in the repo. 
- Use `git log --oneline` command to list one commit per line, the first 7 characters of the commit's SHA, and the commit message.
- Use `git log --stat` command to display the file(s) that have been modified, the number of lines that have been added/removed, and a summmary line with the total number of modified files and lines that have been added/removed.
- Use `git log --patch` or `git log -p` command to display the files that have been modified, the location of the lines that have been added/removed, and the actual changes that have been made.
- Use `git log -p <first-7-characters-of-SHA>` or `git show <first-7-characters-of-SHA>` command to show only the patch information of one commit.
- Useful keys to navigate the log:
  - `j` or `↓` to move down one line at a time.
  - `d` to move down by half the page screen.
  - `f` to move down by a whole page screen.
  - `k` or `↑` to move up one line at a time.
  - `u` to move up by half the page screen.
  - `b` to move up by a whole page screen.
  - `q` to quit the log.
