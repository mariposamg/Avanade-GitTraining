# My Git Cheat Sheet
## Initialize your repository
- git init
git init is the simplest way to start with git.

Open a shell, and move to a folder you want to transform into a git repository:

- mkdir ~/src/gitcheatsheet -p
- cd ~/src/gitcheatsheet
Shell
Once in the folder, you can run the git init command. That's it, your folder is now a git repository !

- git init
Shell
Initialized empty Git repository in ~/src/gitcheatsheet/.git/
Shell
Take five minutes to initialize your own repo, wherever you want on your machine

## git clone
git clone is another way to get a working git repository. The major difference with git init is that you get an existing repository with its historic.

There are two main ways to clone a repository for daily use:

- git clone <url of the repo> (ex: git clone https://github.com/git/git.git). Git will create a folder with the name of the repo (git in the example) and get a copy of the repository in it with all the necessary stuff to make it a valid git repo.
- git clone <url of the repo> <folder where to clone the repo> (ex:git clone https://github.com/git/git.git ~/src/gitrepo). Git will do the same than with the previous command except you control the folder in which git will operate.
We won't use this option right now, but let's keep it in mind.

Starting here, all the commands will have to be executed inside your git repo or one of its subfolder.

## git status
This command is one of the most important ones when you use git from the command line. It indicates you the state of your git repository and what can be the next step.

git status

Shell
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
Shell

If you run it from your new repo, you should get an output similar to this one.

Let's initialize our Cheat Sheet and see what changes:

New-Item "git-cheat-sheet.md" -ItemType File
PowerShell
or

- touch "git-cheat-sheet.md"
 
 Shell
Then check the status of the repository:

git status
Shell
You should obtain something similar to this output:

On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        git-cheat-sheet.md

nothing added to commit but untracked files present (use "git add" to track)
Shell
G
it detects a new file was added inside the repository but git is not managing it. git status is making suggestions for the next step.

- git add
git add is the next step as mentioned by the git status command. Before you can validate a snapshot of your code (a commit), you have to prepare it. This is the role of the git add command and what we call staging in git

Think of it a little bit like a Warehouse. Before sending the orders to their customer, the storekeeper is preparing each order, whether it is a box or a pallet. This is the staging phase.

So let's continue with our previous example and let's stage the file we have just created:

- git add git-cheat-sheet.md
Shell
git status
Shell
Here is the result you should obtain:

On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   git-cheat-sheet.md
$
Shell
Our file is now ready to be committed. Once again, the status command indicates possible actions you execute once there.
## State of the repository
-  git status

Output  : On branch master
No commits yet

nothing to commit (create/copy files and use "git add" to track)
## git commit

- git commit -m 'commit message'

[master (root-commit) 24fcfbe] commit message
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 git-cheat-sheet.md

 ## Create your own branch
When you start working on a feature or just want to test something without impacting the whole repo, create a branch

The simplest way is using git checkout this way:

- git checkout -b features/1234-new-killing-feature

Switched to a new branch 'features/1234-new-killing-feature'

- git status

On branch features/1234-new-killing-feature

This commands are somehow a shortcut that creates a new branch and move to it.

The same action could have been achieved this way:

- git branch features/1234-new-killing-feature
git status

On branch master
...

- git checkout features/1234-new-killing-feature

- git status

On branch features/1234-new-killing-feature
  
In both case, a call to git checkout has to be made to change the branch you are working on.


## Delete a branch
A branch is not expected to live forever. Once a feature is complete or abandoned, you should delete the associated branch to keep your repo clear.

You achieve it using the delete switch:

- git branch -d features/1234-new-killing-feature

Deleted branch features/1234-new-killing-feature (was 3e60269).

Like on Linux File System, the case is once again important. -d or --delete is a standard Delete and -D is the equivalent of '-d --force' to ensure the branch is deleted.


## Other branching commands and options
There are lot more capabilities for branch management with git. Some require us to dive a little bit more into other git topics.

- git merge
Separate features or bug fixes in branches is a very good practice that increases your chances to deliver. That's true. But how do we get a source code that contains features developed on a branch? Here comes git merge !

git merge is a way to integrate modifications from one branch into another.

For example, to merge the changes from our features/1234-new-killing-feature branch into master, here is the command you should use:

- git checkout master

Shell
Switched to branch 'master'
Shell
- git merge features/1234-new-killing-feature

Shell
Updating 3e60269..2ba53cb
Fast-forward
 .gitignore | 3 ++-
 toto.md    | 4 +++-
 2 files changed, 5 insertions(+), 2 deletions(-)