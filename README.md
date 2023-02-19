# Git-Github-documentation
## Reset, Revert and Restore

### Basics of reset

- A mixed option is a default option of the git reset command. If we would not pass any argument, then the git reset command considered as **--mixed** as default option.
- A mixed option updates the ref pointers. The staging area also reset to the state of a specified commit. The undone changes transferred to the working directory. - `git reset —mixed <c-id>`
- The soft option does not touch the index file or working tree at all, but it resets the Head as all options do.
- When the soft mode runs, the refs pointers updated, and the resets stop there. It will act as git amend command. `git reset —soft <c-id>`
- Reset from all stage - `git reset —hard <c-id>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project$ cd files
    abhishek@sf-cpu-438:~/Desktop/project/files$ touch file1
    abhishek@sf-cpu-438:~/Desktop/project/files$ touch file2
    abhishek@sf-cpu-438:~/Desktop/project/files$ touch file3
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git add file1
    abhishek@sf-cpu-438:~/Desktop/project/files$ git commit -m "added file1"
    [fmain 31ab1df] added file1
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 files/file1
    abhishek@sf-cpu-438:~/Desktop/project/files$ git add file2
    abhishek@sf-cpu-438:~/Desktop/project/files$ git commit -m "added file2"
    [fmain db2efaf] added file2
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 files/file2
    abhishek@sf-cpu-438:~/Desktop/project/files$ git add file3
    abhishek@sf-cpu-438:~/Desktop/project/files$ git commit -m "added file3"
    [fmain fc0191a] added file3
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 files/file3
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git log --oneline
    fc0191a (HEAD -> fmain) added file3
    db2efaf added file2
    31ab1df added file1
    ca067ab (feature1) Merge remote-tracking branch 'refs/remotes/origin/feature1' into feature1
    d4bdccc Create tech.txt
    8559da4 xyz
    36b1ee2 clang file again modified
    4d14a8a git-practice added
    9501ea1 modified clang
    9520234 Created clang.txt file
    4b879cf Stash Pop and create new file
    49e5034 Restore from last commit  text.txt file
    3918b6b Modified text.txt file
    9b6c33d Created text.txt file
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git log HEAD~3 --oneline
    ca067ab (feature1) Merge remote-tracking branch 'refs/remotes/origin/feature1' into feature1
    d4bdccc Create tech.txt
    8559da4 xyz
    36b1ee2 clang file again modified
    4d14a8a git-practice added
    9501ea1 modified clang
    9520234 Created clang.txt file
    4b879cf Stash Pop and create new file
    49e5034 Restore from last commit  text.txt file
    3918b6b Modified text.txt file
    9b6c33d Created text.txt file
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git reset --hard db2efaf
    HEAD is now at db2efaf added file2
    abhishek@sf-cpu-438:~/Desktop/project/files$ git reset --mixed 31ab1df
    abhishek@sf-cpu-438:~/Desktop/project/files$ git reset --soft ca067ab
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ ls
    file1  file2
    abhishek@sf-cpu-438:~/Desktop/project/files$ git ls-files
    file1
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git log
    commit ca067abdb0fa348013b90576efe0e29939598f21 (HEAD -> fmain, feature1)
    Merge: 8559da4 d4bdccc
    Author: abhishekvaghela <abhishek.v@simformsolutions.com>
    Date:   Thu Feb 16 16:20:40 2023 +0530
    
        Merge remote-tracking branch 'refs/remotes/origin/feature1' into feature1
    ```
    

### Basics of Revert

- In Git, the term revert is used to revert some changes. The git revert command is used to apply revert operation. It is an undo type command. However, it is not a traditional undo alternative.
- git revert is a commit.
- Created 5 files and and make two modification in f1 and f2.
- Add Abhishek to f1 and Vaghela to f2.
- Do 7 commits with suitable name.
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project/files$ git add file1
    abhishek@sf-cpu-438:~/Desktop/project/files$ git commit -m "Modified f1"
    [dev d3f5320] Modified f1
     1 file changed, 1 insertion(+)
    abhishek@sf-cpu-438:~/Desktop/project/files$ git add file2
    abhishek@sf-cpu-438:~/Desktop/project/files$ git commit -m "Modified f2"
    [dev 6b4da92] Modified f2
     1 file changed, 1 insertion(+)
    abhishek@sf-cpu-438:~/Desktop/project/files$ git log --oneline
    6b4da92 (HEAD -> dev) Modified f2
    d3f5320 Modified f1
    cad1235 Created f5
    995b7a8 Created f4
    fccedf5 Created f3
    dfe51f6 Created f2
    dfa9074 Created f1
    ```
    
- Then delete f1 and make commit for that.
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project/files$ rm -rf file1
    abhishek@sf-cpu-438:~/Desktop/project/files$ git add .
    abhishek@sf-cpu-438:~/Desktop/project/files$ git commit -m "deleted file1"
    [dev 1cb9686] deleted file1
     1 file changed, 1 deletion(-)
     delete mode 100644 files/file1
    ```
    
- Add new file f6 and commit.
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project/files$ touch file6
    abhishek@sf-cpu-438:~/Desktop/project/files$ git add .
    abhishek@sf-cpu-438:~/Desktop/project/files$ git commit -m "Created f6"
    [dev 142bab8] Created f6
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 files/file6
    ```
    
- Current scenario
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project/files$ git log --oneline
    142bab8 (HEAD -> dev) Created f6
    1cb9686 deleted file1
    6b4da92 Modified f2
    d3f5320 Modified f1
    cad1235 Created f5
    995b7a8 Created f4
    fccedf5 Created f3
    dfe51f6 Created f2
    dfa9074 Created f1
    ```
    
- Now we thought that **1cb9686 deleted file1** have to undo, We want to undo commit so we can use revert and old commit remain in list.
    
    `git revert <c-id>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project/files$ git revert -e 1cb9686
    [dev 8eaf1b2] Revert "deleted file1"
    1 file changed, 1 insertion(+)
    create mode 100644 files/file1
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git log --oneline
    8eaf1b2 (HEAD -> dev) Revert "deleted file1"
    142bab8 Created f6
    1cb9686 deleted file1
    6b4da92 Modified f2
    d3f5320 Modified f1
    ```
    
- Revert is also used to revert merge of two branchs.
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project/files$ git log --oneline --graph
    *   0f11fbb (HEAD -> dev) Merge branch 'fea' into dev
    |\  
    | * 2385564 (fea) edited f6
    |/  
    * 8eaf1b2 Revert "deleted file1"
    * 142bab8 Created f6
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git revert -e 0f11fbb -m 1
    [dev 9d05fd0] Revert "Merge branch 'fea' into dev"
     1 file changed, 10 deletions(-)
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git log --oneline --graph
    * 9d05fd0 (HEAD -> dev) Revert "Merge branch 'fea' into dev"
    *   0f11fbb Merge branch 'fea' into dev
    |\  
    | * 2385564 (fea) edited f6
    |/  
    * 8eaf1b2 Revert "deleted file1"
    * 142bab8 Created f6
    * 1cb9686 deleted file1
    ```
    
- Remove file from stage area - `git rm <file-name>`
- Remove from stage but not from local - `git rm —cached <file-name>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project/files$ git rm --cached file5
    rm 'files/file5'
    abhishek@sf-cpu-438:~/Desktop/project/files$ git ls-files
    file1
    file2
    file3
    file4
    abhishek@sf-cpu-438:~/Desktop/project/files$ ls
    file1  file2  file3  file4  file5
    ```
    

### Basics of Restore

- Likewise, We have modified file 5 and add line → “Hiiii!!!”
- Then add into stage area using `git add file5`
- Now, We know that we have to write Heyyaaaaa!! instead of that.
- Then we again modified. So, now one is untracked and one is tracked. So, We have to restore from staged and then add new modified.
- Used to unstage - `git restore —staged <file-name>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project/files$ git status
    On branch fea
    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git restore <file>..." to discard changes in working directory)
    	modified:   file5
    
    no changes added to commit (use "git add" and/or "git commit -a")
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git add file5
    abhishek@sf-cpu-438:~/Desktop/project/files$ git log -p
    commit e4177105ecb847cf6cbc5495bd9fe6690289000c (HEAD -> fea)
    Author: abhishek <abhishek.v@simformsolutions.com>
    Date:   Fri Feb 17 13:28:14 2023 +0530
    
        changes f
    
    diff --git a/files/file5 b/files/file5
    index e69de29..fa3728e 100644
    --- a/files/file5
    +++ b/files/file5
    @@ -0,0 +1 @@
    +Hellooooo!!!
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git diff
    diff --git a/files/file5 b/files/file5
    index 2f0d940..d6ea221 100644
    --- a/files/file5
    +++ b/files/file5
    @@ -1,3 +1,3 @@
     Hellooooo!!!
     
    -Hiii!!
    +Heyyaaaaa!!
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git diff --staged
    diff --git a/files/file5 b/files/file5
    index fa3728e..2f0d940 100644
    --- a/files/file5
    +++ b/files/file5
    @@ -1 +1,3 @@
     Hellooooo!!!
    +
    +Hiii!!
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git status
    On branch fea
    
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
    	modified:   file5
    
    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git restore <file>..." to discard changes in working directory)
    	modified:   file5
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git restore --staged file5
    abhishek@sf-cpu-438:~/Desktop/project/files$ git add file5
    abhishek@sf-cpu-438:~/Desktop/project/files$ git diff --staged
    diff --git a/files/file5 b/files/file5
    index fa3728e..d6ea221 100644
    --- a/files/file5
    +++ b/files/file5
    @@ -1 +1,3 @@
     Hellooooo!!!
    +
    +Heyyaaaaa!!
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git commit -m "Restored and Modified"
    [fea dc32b0c] Restored and Modified
     1 file changed, 2 insertions(+)
    ```
