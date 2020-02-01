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
  - `j` or `↓` or **Space bar** to move down one line at a time.
  - `d` to move down by half the page screen.
  - `f` to move down by a whole page screen.
  - `k` or `↑` to move up one line at a time.
  - `u` to move up by half the page screen.
  - `b` to move up by a whole page screen. 
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
- **Globbing** crash course:
  - Blank lines can be used for spacing.
  - `#`: marks line as a comment.
  - `*`: matches 0 or more characters.
  - `?`: matches 1 character.
  - `[abc]`: matches a, b, _or_ c.
  - `**`: matches nested directories (e.g. `a/**/z` matches `a/z`, `a/b/z`, `a/b/c/z`).
- Combining branches together is called **merging**. Git can automatically merge the changes on different branches together. There are 2 main types of merges in Git: a **regular merge** and a **fast-forward merge**. A **fast-forward merge** will move the currently checked out branch *forward* until it points to the same commit that the other branch is pointing to.
- When a merge fails, we have a **merge conflict**. Git will pause mid-merge telling you that there is a conflict and will tell you in what file or files the conflict occurred. To resolve the conflict in a file, you need to:
  - Locate and remove all lines with merge conflict indicators.
  - Determine what to keep.
  - Save the file(s). Stage the file(s). Make a commit.
- Use `git init` command to create a new empty repo in the current directory.
- Use `git clone <path-to-repo-to-clone> <new-repo-name>` to clone the repo into a directory under a different name. 
- Use `git status` command to know what's going on with a repo.
- Use `git log` command to display all of the commits of a repo. By default, this command displays the SHA, the author, the date, and the message of every commit in the repo. 
- Use `git log --oneline` command to list one commit per line, the first 7 characters of the commit's SHA, and the commit message.
- Use `git log --stat` command to display the file(s) that have been modified, the number of lines that have been added/removed, and a summmary line with the total number of modified files and lines that have been added/removed.
- Use `git log --patch` or `git log -p` command to display the files that have been modified, the location of the lines that have been added/removed, and the actual changes that have been made.
- Use `git log -p <first-7-characters-of-SHA>` or `git show <first-7-characters-of-SHA>` command to show only the patch information of one commit.
- Use `git add` command to move files from the **Working directory** to the **Staging index**.
- Use `git commit`command to move files from the **Staging index** to the repo.
- Use `git diff` command to see changes that have been made but haven't been commited yet.
- The `.gitignore` file tells Git about the files that Git should not track. This file should be placed in the same directory that the `.git` file is.
- Use `git tag -a <SHA>` command to add a marker to the most recent commit or a specific commit. The tag doesn't move around as new commits are added.
- Use `git branch` command to list all branch names in the repo, create new branches, or delete branches. 
- Use `git branch <new_branch_name> <SHA>` command to create the new branch and have it point to the commit with the provided SHA.
- Use `git branch -d <branch_name>` command to delete a branch. Note that you can't delete the active branch so you have to switch to a different branch before you can delete the previously active branch. This command can't be used to delete a branch with commits that are not on any other branch. This helps prevent deleting new commits by accident. Use `git branch -D <branch_name>` command to force delete in that case.
- Use `git checkout <branch>` command to switch between branches. Use `git checkout -b <new_branch>` to create a new branch and switch to that branch.
- Use `git merge <name-of-branch-to-merge-in>` command to combine branches in Git.
- Use `git commit --amend` command to alter the most recent commit. You can either fix the commit message, include missed files (or changes to files), or do all of those.
- Use `git revert <SHA-of-commit-to-revert>` command to undo the changes that were made by the provided commit and create a new commit to record the change.
- Use `git reset <reference-to-commit>` command to:
  - Move the `HEAD` and current branch pointer the the referenced commit.
  - Erase commits with the `--hard` flag.
  - Move committed changes to the staging index with the `--soft` flag.
  - Unstage committed changes with `--mixed` flag (default).
- Ancenstry references are used to indicate previous commits. The ancestry references are:
  - `^`: indicates the parent commit.
  - `~`: indicates the first parent commit.
  - E.g. `HEAD^`/`HEAD~`/`HEAD~1` indicate parent commit. `HEAD^^`/`HEAD~2` indicate grandparent commit.

## Working with Remotes
- **Git vs. GitHub**: **Git** is a version control tool, while **GitHub** is a service to host Git projects.
- The `git remote` command allows you to manage and interact with remote repos.
  - It's possible to have links to multiple different remote repos.
  - A shortname is the name that's used to refer to a remmote repo's location. Typically, the location is a URL, but it could be a file path on the same computer.
  - Use `git remote add` command to add a connection to a new remote repo.
  - Use `git remote -v` to see the details about a connection to a remote.
- Use `git push <remote-shortname> <branch>` command to send local commits to a remote repo.
  - The shortname of the remote repo you want to send commits to.
  - The name of the branch that has the commits you want to send.
- Use `git pull <remote-shortname> <branch>` command to pull remote commits to a local repo. The following things happen after the command is run:
  - The commit(s) on the remote branch are copied to the local repo.
  - The local tracking branch (`origin/master`) is moved to point to the most recent commit.
  - The local tracking branch (`origin/master`) is merged into the local branch (`master`).
- Use `git fetch <remote-shortname> <branch>` command to retrieve commits from a remote repo's branch. Nonetheless, the command doesn't automatically merge the local branch with the remote tracking branch after those commits have been received. The following things happen after the command is run:
  - The commit(s) on the remote branch are copied to the local repo.
  - The local tracking branch (`origin/master`) is moved to point to the most recent commit.
- **Forking** a repo means making an identical copy of the existing repo. **Forking** is different from **cloning** in the sense that the forked remote repo remains a remote repo, whereas a cloned repo exists in the local machine.
- Use `git shortlog` command to see the number of commits made by each contributor.
- Use `git log --author="<Name>"` command to filter commits made by a specific author.
- Use `git log --grep="<String>"` command to filter commits with specific commit message.
- Before you start doing any work, you should look for the project's **CONTRIBUTING.md** file.
- Look at the GitHub issues for the project.
  - Look at the existing issues to see if one is similar to the change you want to contribute.
  - If necessary, create a new issue.
  - Communicate the changes you'd like to make to the project maintainer in the issue.
- When you start developing, commit all of your work on a topic branch:
  - **DO NOT** work on the master branch.
  - Make sure to give the topic branch clear and descriptive name.
- As a general best practice for writing commits:
  - Make frequent small commits.
  - Use clear and descriptive commit messages.
  - Update the README.md file.
- A **pull request** is a request to the *original* or *source repo*'s maintainer to include changes in their project that you made in your fork of their project. You're requesting that they *pull* the changes you've made.
- To create a **pull request**, a few things need to happen:
  - You must **fork** the source repo.
  - Clone your fork to your local machine.
  - Make some commits to a topic branch (advisable).
  - Push the commits back to **your fork**.
  - Create a new pull request and choose the branch that has your new commits.
- The maintainers of the original project will continue adding changes to their project - the one that you have forked. Thus, you should keep your fork in sync with their project so that you can include any changes that they make.
- To get commits from a source repo, you need to:
  - Get the cloneable URL of the source repo.
  - Create a new remote with the `git remote add` command.
    - Use the shortname `upstream` to point to the source repo.
    - Provide the URL of the source repo.
  - Fetch the new `upstream` remote.
  - Merge the `upstream`'s branch into a local branch.
  - Push the newly updated local branch to your `origin` repo.
- Taking a number commits and combining them into one single commit is called **squashing**.
- **Rebase commands** are the different commands you can do with `git rebase` command:
  - Use `p` or `pick` to keep the commit as is.
  - Use `r` or `reword` to keep the commit's content but alter the commit message.
  - Use `e` or `edit` to keep the commit's content but stop before commiting so that you can add new content/files, remove content/files, or alter the content that was going to be commmitted.
  - Use `s` or `squash` to combine this commit's changes into the previous commit (the commit above it in the list).
  - Use `f` or `fixup` to combine this commit's change into the previous one but drop the commit message.
  - Use `x` or `exec` to run a shell command.
  - Use `d` or `drop` to delete the commit.
- You should create a `backup` branch before rebasing so that it's easy to return to your previous state. Once you're happy with the rebase, you can delete the `backup` branch.

## Cloud Computing
- **Cloud computing** is the delivery of IT resources over the Internet. The cloud is like a virtual data centre accessible via the Internet that allows you to manage:
  - Storage services like databases.
  - Servers, compute power, networking.
  - Analytics, AI, augmented reality.
  - Security services for data and applications.
- **Characteristics** of cloud computing:
  - **Pay as you go** - You pay only for what you use and only when your code runs.
  - **Autoscaling** - The number of active servers can grow or shrink based on demands.
  - **Serverless** - Allows you to write and deploy code without having to worry about the underlying infrastructure.
- **Types** of cloud computing:
  - **Infrastructure-as-a-Service (IaaS)**: The provider supplies virtual server instances, storage, and mechanisms for you to manage servers.
  - **Platform-as-a-Service (PaaS)**: A platform of development tools hosted on a provider's infrastructure.
  - **Software-as-a-Service (SaaS)**: A software application that runs over the Internet and is managed by the service provider.
- Cloud **Deployment Models**:
  - A **Public Cloud** makes resources (databases, application development services, etc.) available over the Internet to the general public.
  - A **Private Cloud** called On-premises, is a proprietary network that supplies services to a limited number of people.
  - A **Hybrid Cloud** is a combination of both a public and a private cloud. The hybrid model is a growing trend in the industry for those organisations that have been slow to adopt the cloud due to being in a heavily regulated industry. The hybrid model gives organisations the flexibility to slowly migrate to the cloud.
- **Benefits** of Cloud:
  - Ability to innovate quickly.
  - Scale globally in minutes.
  - Deliver faster.
  - Pay for only what you use.
  - Avoid huge capital investments up front.
  - Stop guessing about capacity.
- **Global infrastructure**.
  - A **Region** is considered a geographic location or an area on a map.
  - An **Availability zone** is an isolated location within a geographic region and is a physical data centre within a specific region.
  - An **Edge location** is as a mini-data centre used solely to cache large data files closer to a user's location.
  - Additional information:
    - There are Availability Zones (AZs) than there are Regions.
    - There should be at least two AZs per Region.
    - Each region is located in a separate geographic area.
    - AZs are distinct locations that are engineered to be isolated from failures.
- **Shared resonsibility model**: AWS is responsible for security **of** the cloud, while we are responsible for security **in** the cloud. Examples include:
  - Securing edge locations (AWS).
  - Monitoring physical device security (AWS).
  - Providing physical access control to hardware/software (AWS).
  - Database patching (AWS).
  - Discarding physical storage devices (AWS).
  - Managing AWS Indentity and Access Management (User).
  - Encrypting data (User).
  - Preventing or detecting when an AWS account has been compromised (User).
  - Restricting access to AWS services to only those users who need it (User).
- **Servers in the Cloud** have revolutionised the IT industry.
  - Scale capacity up and down based on demands.
  - Storage, more memory and computing power can be added as needed.
  - Obtain servers in minutes.
  - No need for onsite hardware or capital expenses.

## AWS Foundation & Compute Service
- **EC2 (Elastic Cloud Compute)** is a foundational piece of AWS' cloud computing platform and is a service that provides servers for rent in the cloud. EC2 is **NOT considered serverless**.
- **Instances** are phyiscal servers in an AZ / data centre.
- There are several **pricing options** for EC2.
  - **On demand** - Pay as you go, no contract.
  - **Dedicated hosts** - You have your own dedicated hardware and don't share it with others.
  - **Spot** - You place a bid on an instance price. If there is extra capacity that falls below your bid, an EC2 instance is provisioned. If the price goes above your bid while the instance is running, the instance is terminated.
  - **Reserved instances** - You earn huge discounts if you pay up front and sign a 1-year or 3-year contract.
- **EBS (Elastic Block Store)** is a storage solution for EC2 instances and is a physical hard drive that is attached to the EC2 instance to increase storage.
- There are 2 types of memory for an EC2 instance:
  - In memory (instance store).
  - EBS.
- EBS is able to **persist data** after EC2 is terminated and is **automatically replicated** in its AZ.
- **Security** in the cloud allows you to have complete control over your virtual networking environment.
  - Configure your virtual network with public or private facing subnets.
  - Launch your servers in the selected networks to secure access.
- **VPC (Virtual Private Cloud)** allows you to create your own private network in the cloud. You can launch services, like EC2, inside of that private network. A VPC spans all the AZ's in the region.
- **Compute power in the cloud** is a faster way to build applications, providing:
  - No servers to manage (i.e. serverless).
  - Ability to continuously scale.
  - Ability to run code on demand in response to events.
  - Pay only when your code runs.
- **AWS Lambda** provides you with computing power in the cloud by allowing you to execute code without standing up or managing servers. 
  - Lambdas have a time limit of 15 minutes.
  - The code you run on AWS Lambda is called **Lambda function**.
  - **Event-driven**: Lambda code can be triggered by other AWS services. 
  - Application developed using Lambda is considered **serverless**.
- **Elastic Beanstalk** is an orchestration service that allows you to deploy a web application at the touch of a button by spinning up (or provisioning) all of the services that you need to run your application.

## Storage & Content delivery
- Storage and database services in the cloud provide a place for companies to collect, store, and analyse the data they have collected over the years at a massive scale. Below are some storage & database services:
  - Amazon S3 (Simple Storage Service).
  - Amazon S3 Glacier.
  - DynamoDB.
  - Relational Database Service (RDS).
  - Redshift.
  - ElastiCache.
  - Neptune.
  - Amazon DocumentDB.
- **Benefits** of storage services include:
  - **Durability**: No data loss.
  - **Availability**: Fast and reliable access to the data stored in the cloud.
  - **Scalability**: Meet demand seamlessly and maintain a steady state through automatic modification.
    - **Vertical** (Scaling up): Modify the server to meet demand (e.g. add more memory or capacity to a single server, etc.)
    - **Horizontal** (Scaling out): Add or remove servers to meet demand.
    - **Diagonal** scaling is a combination of vertical and horizontal scaling.
- Amazon S3 is an **object storage system** in the cloud.
- **S3 use cases**:
  - Hosting static websites.
  - Content delivery.
  - Backup and recovery.
  - Archiving and big data.
  - Application data.
  - Hybrid cloud storage.
- S3 offers several **storage classes**, which are different data access levels for your data at certain price points. For example, S3 Glacier is a secure, durable, and low-cost storage class for data archiving.
- **DynamoDB** is a NoSQL document database service that is fully managed. Unlike traditional databases, NoSQL databases, are schema-less, which means that the database doesn't contain a fixed (rigid) data structure.
  - DynamoDB can handle more than 10 trillion requests per day.
  - DynamoDB is serverless as there are no servers to provision, patch, or manage.
  - DynamoDB supports key-value and document data models.
  - DynamoDB synchronously replicates data across three AZs in an AWS region.
  - DynamoDB supports GET/PUT operations using a primary key.
  - Data is stored in DynamoDB in JSON or JSON-like format.
- **RDS** (Relational Database Service) is a service that aids in the administration and management of databases. RDS assists with database administrative tasks that include upgrades, patching, installs, backups, monitoring, performance checks, security, etc. Nonetheless, RDS doesn't allow you to access your database via secure shell (SSH).
  - Database Engine support includes: Oracle, PostgreSQL, MySQL, MariaDB, SQL Server.
- **Redshift** is a cloud data warehousing service to help companies manage big data. Redshift allows you to run fast queries against your data using SQL, ETL, and BI tools. Redshift stores data in a column format to aid in fast querying.
  - Redshift stores data in columnar format (not a row store) which aids in fast query and analysis.
  - Redshift automates administrative and maintenance tasks.
  - Redshift delivers great performance by using machine learning.
  - Redshift Spectrum is a feature that enables you to run queries against data in Amazon S3.
  - Redshift encrypts and keeps your data secure in transit and at rest.
  - Redshift clusters can be isolated using Amazon VPC.
  - Redshift is **NOT** used for processing day-to-day transactions.
- **CDN (Content Delivery Network)** speeds up delivery of your static and dynamic web content by caching content in an Edge location close to your user base. The **benefits of CDN** include:
  - Low latency.
  - Decreased server load.
  - Better user experience.
- **CloudFront** is used as a global CDN. CloudFront speeds up the delivery of your content through Amazon's worldwide network of mini-data centers called Edge locations.
  - Amazon countinously adds new Edge Locations.
  - CloudFront ensures that end-user requests are served from the closest edge location.
  - CloudFront works with non-AWS origin sources.
  - GeoIP blocking can be used to serve content (or not serve content) to specific countries.
  - Cache control headers determine how frequently CloudFront needs to check the origin for an updated version your file.
  - The maximum size of a single file that can be delivered through Amazon CloudFront is 20 GB.




