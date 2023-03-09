# My Git Cheat Sheet
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