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
- A **Subnet** is a subset of the overall VPC network and it only exists in a single availability zone, unlike its parent network, the VPC. 
  - A subnet contains resources, and can be assigned access rights that apply to all resources within that subnet. Subnets can be public or private. 
  - Public subnets are accessible to external users. Private subnets are only accessed internally by other resources within your cloud container.
- A **Route table** is a set of entries or rules associated with one or more of your subnets inside your VPC.
  - These rules allow or deny traffic to/from the address ranges that you specify.
  - Rules can be as open as the entire world or restricted to a single IP address.
- Use IP addresses for **routing traffic**. We can route traffic to stay within the VPC, or within a particular subnet, for security reasons.
- An **Internet Gateway (IGW)** is a resource thaat enables inbound and outbound traffic from the internet to your VPC. 
  - An Internet Gateway allows external users to communicate with parts of your VPC.
  - You **don't need an Internet Gateway** if you create a private VPC for an application that is internal to your company.
- **Network Address Translation (NAT) Gateway** provides outbound-only Internet Gateway for private services to access the Internet. This keeps the private service protected from inbound connections, but allows it to connect to the Internet in order to perform functions such as downloading software updates.
  - The NAT Gateway serves as an intermediary to take a private resource's request, connect to the Internet, and then relay the response back to the private resource without exposing that private resource's IP address to the public.
  - NAT Gateways must be placed inside the public subnets and not the private subnets. NAT Gateways need to be in the public subnet so that they can communicate with the public Internet, and handle requests from resources that are in a private subnet.
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

## Security in the cloud
- Cloud security protects data, applications that access the data, and the infrastructure that the applications run on. The way security is delivered depends on the cloud security options provided by the cloud service company.
- **AWS Shield** is a managed **DDoS (Distributed Denial of Service)** protection service that safeguards web applications using AWS.
  - AWS Shield Standard is always on, using techniques to detect malicious traffic.
  - AWS Shield Advanced provides enhanced detection.
  - A **DDoS attack** is an attempt to make a website or an application unavailable by overwhelming it with traffic from multiple sources.
- **AWS WAF (Web Application Firewall)** provides a firewall that protects your web applications.
  - WAF can stop common web attacks by **reviewing the data being sent to your application** and stop well-known attacks.
  - WAF helps protect your website from common attack techniques such as **SQL injection** and **Cross-Site Scripting (XSS)**.
  - **SQL injection** attacks are a type of injection attack, in which SQL commands are injected into data-plane input in order to effect the execution of predefined SQL commands.
  - **XSS** attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites.
- **IAM (Identity & Access Management)** is an AWS service that allows us to configure who can access our AWS account, services, or even applications running in our account. IAM is a global service and is automatically available across all regions.
  - **User/Entity** is a person or service that interacts with services or applications running in your AWS account.
  - **IAM Group** is a collection of users.
  - **IAM Role** is an identity with permissions or a set of privileges.
  - **Policy** defines granular level permissions.
  - IAM Policies are written in JSON.

## Networking & Elasticity in the cloud
- Networks reliably carry loads of data around the globe allowing for the delivery of content and applications with high availability. The network is the foundation of your infrastructure. 
- **Route 53** is a cloud domain name systems (DNS) service that has servers distributed around the globe used to translates human-readable names like [Google](www.google.com) into the numeric IP addresses like 74.125.21.147.
  - Scales automatically to manage spikes in DNS queries.
  - Allows you to register a domain name (or manage an existing).
  - Routes internet traffic to the resources for your domain.
  - Checks the health of your resources.
  - Allows you to route users based on the user's geographic location.
- With **elasticity**, your servers, databases and application resources can automatically scale up or down based on your load.
- **EC2 Auto Scaling** is a service that monitors your EC2 instances and automatically adjusts by adding or removing EC2 instances based on conditions you define in order to maintain application availability and provide peak performance to your users.
  - Automatically scale in and out based on needs.
  - Included automatically with Amazon EC2.
  - Automate how your Amazon EC2 instances are managed.
  - EC2 predictive scaling removes the need for manual adjustment of auto scaling parameters over time.
- **Elastic Load Balancer** automatically distributes incoming application traffic accross multiple servers.
  - Balances load between two or more servers.
  - Stands in front of a web server.
  - Provides **redundancy** and **performance**.
    - Redundancy maintains continuous operations in an emergency. It means that if you lose a server, the load balancer will send requests to other working servers. 
    - Performance: If a server starts having issues or bottlenecks, the load balancer will add more servers to the pool of available servers. Auto scaling automatically adjusts capacity to maintain a steady state.

## Messaging & Containers
- **Messaging** typically occurs between Internet-based applications and devices. One system can send message to another system.
- **SNS (Simple Notification Service)** is a cloud service that allows you to send notifications to the users of your applications. SNS allows you to **decouple the notification logic** from being embedded in your applications and allows notifications to be **published to a large number of subscribers**.
  - SNS uses a publish/subscribe model.
  - SNS can publish messages to Amazon SQS queues, AWS Lambda functions, and HTTP/S webhooks.
  - A notification can only contain 1 message.
- **SQS (Simple Queue Service)** is a fully managed message queuing service that allows you to integrate queuing functionality in your application. SQS offers two types of message queues: Standard and FIFO.
  - FIFO should be used when message order is critial, while Standard can be used when messages arrive more than once and can be processed out of order.
  - FIFO queuses guarantee the order of messages.
  - Standard queues offer best-effort ordering but no guarantees.
  - Standard queues deliver a message at least once, but occasionally more than one copy of a message is delivered.
- A **container** consists of everything an application needs to run: the application itself and its dependencies (e.g. libraries, utilities, configuration files), all bundled into one package. Each container is an independent component that can run on its own and be moved from environment to environment.
- **ECS (Elastic Container Service)** is an orchestration service used for automating deployment, scaling, and managing of your containerised applications. ECS works well with Docker containers by:
  - Launching and stopping Docker containers.
  - Scaling your application.
  - Querying the state of your applications.
- Docker is the only container platform supported by Amazon ECS.

## AWS Management
- **Logging** provides visibility into your cloud resources and applications. For applications that run in the cloud, you will need access to logging and auditing services to help you proactively monitor your resources and applications. Logging helps answer important questions like:
  - How is the server performing?
  - What is the current load on the server?
  - What is the root cause of an application error that a user is seeing?
  - What is the path that leads to this error?
- **Cloud Trail** allows you to audit (or review) everything that occurs in your AWS account. Cloud Trail does this by recording all the AWS API calls occuring in your account and delivering a log file to you.
- **Cloud Watch** is a service that monitors resources and applications that run on AWS by collecting data in the form of logs, metrics and events.
  - Collect and track metrics.
  - Collect and monitor log files.
  - Set alarms and create triggers to run your AWS resources.
  - React to changes in your AWS resources.
- **Infrastructure as Code** allows you to describe and provision all the infrastructure resources in your cloud environment. You can stand up servers, databases, runtime parameters, resources, etc. based on scripts that you write. Infrastructure as Code is a time-saving feature because it allows you to provision (or stand up) resources in a reproducible way.
- **AWS Cloud Formation** allows you to model entire infrastructure in a text file template allowing you to provision AWS resources based on the scripts you write.
  - Cloud Formation templates are written using JSON or YAML.
  - AWS resources which are part of a Cloud Formation stack can still be individually managed.
- **AWS CLI** allows you to access and control services running in your AWS account from the command line.

## Cloud DevOps
- Issues that DevOps tries to solve:
  - Unpredictable deployments.
  - Mismatched environments (development doesn't match production).
  - Configuration drift.
- **Benefits** of DevOps:
  - Predictable deployments because it's done via an automated script.
  - Enable **CI/CD (Continuous Integration Continuous Deployment)** so that new features are automatically deployed with all the required dependencies.
    - **CI (Continuous integration)** is the process flow of testing any change made to the deployment flow.
    - **CD (Continuos deployment)** tracks those changes made to the deployment flow through to staging and production systems.
- CloudFormation script should be **split into several files based on type of resources**. For example, you would have a file for network resources, another for database resources and so on. This allows expert to work on, and become familiar with, their resources and leverage their existing knowledge.
- YAML and JSON file formats are both supported in CloudFormation, but **YAML is the industry preferred version** that's used for AWS and other cloud providers (Azure, GCP).

## Servers and Security Group
- **Security groups** are specific to individual resources (EC2 servers, databases) and not to subnets.
- In cloud, traffic is **blocked by default**, so you have to explicitly open ports to allow traffic in and out. This is a general networking concept.
- **Ingress rules** are for inbound traffic, and **egress rules** are for outbound traffic.
- Ingress rules restrict or allow traffic trying to reach our resources on specific ports.
- Egress rules restrict or allow traffic originating from our server -- typically we are ok allowing all outbound traffic without restrictions as this doesn’t pose a risk for a security breach.
- For **ingress rules**, we want to limit inbound traffic, for security, to a single port or just a handful of ports required by the application we are running.
  - If it's a public server, for example, it will require `port 80` open to the world (World = `0.0.0.0/0`).
  - Should you need the SSH port open, restrict this port only to your specific IP address.
- For **egress rules**, we want to give the resources full access to the Internet, so we give egress access to all ports from `0` to `65535`.

## Storage and Databases
- **Relational Database Service (RDS)**: AWS service for creating databases.
  - Most applications need their data to persist and not be lost, which requires a database.
  - We don't want a database to be a single point of failure, so we'll use resources that are designed for reliability. For example, RDS for the database, and S3 for the filestore.
  - AWS Aurora and MySQL have no additional licensing costs. Microsoft SQL Server will have additional licensing costs.
  - A single RDS server can host multiple databases.
  - A database should have a read replica if you want to accommodate statistical reporting and other read-only queries.
- Use **Filestores** instead of databases for large files, such as videos and text documents.
- Configuration files and sensitive encrypted data are best stored in specific filestores rather than inside the servers. Autoscaling groups may create or destroy servers, so keep data that you want to persist in separate resources such as filestores.
- S3 can be used to store your config files, media or log files. Your servers don't need credentials to access S3 provided they have a role assigned.
- We recommend you choose RDS as opposed to installing a database in your own servers that you have to manage and back up yourself.
