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
