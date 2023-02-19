# Git-Github-documentation
## Add, Commit and log

### Introduction to Add

- The git add command is used to add file contents to the Staging Area.
- This command updates the current content of the working tree to the staging area. It also prepares the staged content for the next commit.
- Add single file `git add <file-name>`
- Add all file `git add -a` or `git add .`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/practice$ touch file6
    abhishek@sf-cpu-438:~/Desktop/practice$ git add file6
    abhishek@sf-cpu-438:~/Desktop/practice$ git status
    On branch feature
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
    	new file:   file6
    ```
    
- Delete file from stage area you have to delete from actual folder then use same command `git add <file-name>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/practice$ git status
    On branch feature
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
    	new file:   file6
    
    Changes not staged for commit:
      (use "git add/rm <file>..." to update what will be committed)
      (use "git restore <file>..." to discard changes in working directory)
    	deleted:    file6
    
    abhishek@sf-cpu-438:~/Desktop/practice$ git add file6
    abhishek@sf-cpu-438:~/Desktop/practice$ git status
    On branch feature
    nothing to commit, working tree clean
    ```
    
- Reset or undo add operation `git reset <file-name>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/practice$ touch file6
    abhishek@sf-cpu-438:~/Desktop/practice$ git add file6
    abhishek@sf-cpu-438:~/Desktop/practice$ git status
    On branch feature
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
    	new file:   file6
    
    abhishek@sf-cpu-438:~/Desktop/practice$ git reset file6
    abhishek@sf-cpu-438:~/Desktop/practice$ git status
    On branch feature
    Untracked files:
      (use "git add <file>..." to include in what will be committed)
    	file6
    
    nothing added to commit but untracked files present (use "git add" to track)
    ```
    

### Introduction to Commit

- It is used to record the changes in the repository. It is the next command after the git add.
- Every commit contains the index data and the commit message. Every commit forms a parent-child relationship.
- Commits are the snapshots of the project.
- `git commit -m “message”`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/practice$ git add file6
    abhishek@sf-cpu-438:~/Desktop/practice$ git commit -m "added file6"
    [feature 48e2696] added file6
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 file6
    ```
    
- See all the commits `git log`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/practice$ git log
    commit 48e2696c7d8cd95c4af8e2a91409fa2e3d6a2dc9 (HEAD -> feature)
    Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    Date:   Wed Feb 15 10:22:34 2023 +0530
    
        added file6
    
    commit fa3b2c25d067127f8eeff224ba6d8b8b084a3b19 (master)
     Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    Date:   Wed Feb 15 10:24:39 2023 +0530
    
        Make names folder and file
    
    commit 42d3b834a171653024f36d8fa8b23250af063e9d
   Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    Date:   Wed Feb 15 10:26:46 2023 +0530
    
        Created 5 files
    ```
    
- When we create new file and update one file then we have to commit direct then use `git commit -a` or `git commit -am “message”` Command to commit only modified file.
- New file still remain untracked.
    
    ```
    abhishek@sf-cpu-438:~/Desktop/practice$ touch file7
    abhishek@sf-cpu-438:~/Desktop/practice$ git status
    On branch feature
    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git restore <file>..." to discard changes in working directory)
    	modified:   file6
    
    Untracked files:
      (use "git add <file>..." to include in what will be committed)
    	file7
    
    no changes added to commit (use "git add" and/or "git commit -a")
    
    abhishek@sf-cpu-438:~/Desktop/practice$ git commit -a "file6 update"
    fatal: paths 'file6 update ...' with -a does not make sense
    
    abhishek@sf-cpu-438:~/Desktop/practice$ git commit -am "Updated file6"
    [feature 9edab1a] Updated file6
     1 file changed, 1 insertion(+)
    
    abhishek@sf-cpu-438:~/Desktop/practice$ git status
    On branch feature
    Untracked files:
      (use "git add <file>..." to include in what will be committed)
    	file7
    
    nothing added to commit but untracked files present (use "git add" to track)
    ```
    
- To update or change last commit message use `git commit -amend`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/practice$ git commit --amend  
    [feature 8f6cebb] Updated file6 - Commit message updated
     Date: Wed Feb 15 10:33:24 2023 +0530
     1 file changed, 1 insertion(+)
    
    abhishek@sf-cpu-438:~/Desktop/practice$ git log
    commit 8f6cebb1870acfed79ae29b69366e4f17baed951 (HEAD -> feature)
    Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    Date:   Wed Feb 15 10:33:24 2023 +0530
    
        Updated file6 - Commit message updated
    ```
    

### Introduction to Log

- Git log - Display the most recent commits and the status of the head.
    
    `git log`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/practice$ git log
    commit 8f6cebb1870acfed79ae29b69366e4f17baed951 (HEAD -> feature)
    Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    Date:   Wed Feb 15 10:33:24 2023 +0530
    
        Updated file6 - Commit message updated
    
    commit 48e2696c7d8cd95c4af8e2a91409fa2e3d6a2dc9
    Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    Date:   Wed Feb 15 10:22:34 2023 +0530
    
        added file6
    
    commit fa3b2c25d067127f8eeff224ba6d8b8b084a3b19 (master)
    Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    Date:   Tue Feb 14 11:30:53 2023 +0530
    
        Make names folder and file
    
    commit 42d3b834a171653024f36d8fa8b23250af063e9d
    Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    ```
    
- Display the output as one commit per line - `git log —oneline`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/practice$ git log --oneline
    8f6cebb (HEAD -> feature) Updated file6 - Commit message updated
    48e2696 added file6
    fa3b2c2 (master) Make names folder and file
    42d3b83 Created 5 files
    ```
    
- Displays the files that have been modified - `git log --stat`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/practice$ git log --stat
    commit 8f6cebb1870acfed79ae29b69366e4f17baed951 (HEAD -> feature)
    Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    Date:   Wed Feb 15 10:33:24 2023 +0530
    
        Updated file6 - Commit message updated
    
     file6 | 1 +
     1 file changed, 1 insertion(+)
    
    commit 48e2696c7d8cd95c4af8e2a91409fa2e3d6a2dc9
    Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    Date:   Wed Feb 15 10:22:34 2023 +0530
    
        added file6
    
     file6 | 0
     1 file changed, 0 insertions(+), 0 deletions(-)
    ```
    
- Display the modified files with location - `git log -p`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/practice$ git log -p
    commit 8f6cebb1870acfed79ae29b69366e4f17baed951 (HEAD -> feature)
    Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    Date:   Wed Feb 15 10:33:24 2023 +0530
    
        Updated file6 - Commit message updated
    
    diff --git a/file6 b/file6
    index e69de29..ffc38a8 100644
    --- a/file6
    +++ b/file6
    @@ -0,0 +1 @@
    +Abhishek
    
    commit 48e2696c7d8cd95c4af8e2a91409fa2e3d6a2dc9
    Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    Date:   Wed Feb 15 10:22:34 2023 +0530
    
        added file6
    
    diff --git a/file6 b/file6
    new file mode 100644
    index 0000000..e69de29
    
    commit fa3b2c25d067127f8eeff224ba6d8b8b084a3b19 (master)
    Author: abhishek-simform-v1 <abhishek.v@simformsolutions.com>
    Date:   Tue Feb 14 11:30:53 2023 +0530
    
        Make names folder and file
    
    diff --git a/Names/name1 b/Names/name1
    new file mode 100644
    index 0000000..0985f4a
    --- /dev/null
    +++ b/Names/name1
    @@ -0,0 +1 @@
    +Abhishek Vaghela
    ```
