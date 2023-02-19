# Git-Github-documentation
    
## Branching & Checkout

### Basics

- Create branch - `git branch <branch-name>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git branch f1
    abhishek@sf-cpu-438:~/Desktop/notes$ git branch
      f1
      feature
    * master
    ```
    
- List all the branch - `git branch` or `git branch list`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git branch
      feature
    * master
    abhishek@sf-cpu-438:~/Desktop/notes$ git branch --list
      feature
    * master
    ```
    
- List all branch along with remote - `git branch -a`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git branch -a
      feature
    * master
      remotes/origin/master
    ```
    
- Checkout branch - `git checkout <branch-name>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git checkout f1
    M	README.md
    Switched to branch 'f1'
    abhishek@sf-cpu-438:~/Desktop/notes$ git branch
    * f1
      feature
      master
    ```
    
- Delete branch - `git branch -d <branch-name>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git branch -d f1
    Deleted branch f1 (was cdb408c).
    ```
    
- Create and switch to another branch - `git checkout -b <branch-name>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git checkout -b f2
    Switched to a new branch 'f2'
    abhishek@sf-cpu-438:~/Desktop/notes$ git branch
    * f2
      feature
      master
    abhishek@sf-cpu-438:~/Desktop/notes$ git add .
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m "first"
    [f2 208ceb8] first
     1 file changed, 1 insertion(+), 1 deletion(-)
    abhishek@sf-cpu-438:~/Desktop/notes$ git push origin f2
   abhishek for 'https://github.com': abhishek-simform-v1
    Password for 'https://abhishek-simform-v1@github.com': 

    Enumerating objects: 5, done.
    Counting objects: 100% (5/5), done.
    Delta compression using up to 8 threads
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (3/3), 278 bytes | 278.00 KiB/s, done.
    Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
    remote: Resolving deltas: 100% (1/1), completed with 1 local object.
    remote: 
    remote: Create a pull request for 'f2' on GitHub by visiting:
    remote:      https://github.com/abhishek-simform-v1/Git-Github-Docmentation/pull/new/f2
    remote: 
    To https://github.com/abhishek-simform-v1/Git-Github-Docmentation.git
     * [new branch]      f2 -> f2
    ```
    
- Delete remote branch - `git push origin -d <branch-name>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git push origin -d f2
    abhishek for 'https://github.com': abhishek-simform-v1
    Password for 'https://abhishek-simform-v1@github.com': 
    To https://github.com/abhishek-simform-v1/Git-Github-Docmentation.git
     - [deleted]         f2
    ```
    
## Merge

### Basics of merge

- There are two branches **master** and **feature.**
- We can see that we made some commits in both functionality and master branch, and merge them. It works as a pointer.
- It will find a common base commit between branches. Once Git finds a shared base commit, it will create a new "merge commit." It combines the changes of each queued merge commit sequence.
- To merge the specified commit to currently active branch - `git merge <commit-id>`
- To merge the specified branch to currently active branch - `git merge <branch-name>`
- **Fast Forward merge:** When f1 and f2 branch have same base point, then create 4 new file in f1 and do 4 commit for individual file created. then checkout f2 branch. f1,f2 → c1←c2←c3←c4  (head→f1).
- Apply `git merge f1` , So it will not created new commit and do fast forward merge so now f1 and f2 points at same base point of c4 commit.
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git merge f1
    Updating 208ceb8..e972ef1
    Fast-forward
     file1 | 0
     file2 | 0
     file3 | 0
     file4 | 0
     4 files changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 file1
     create mode 100644 file2
     create mode 100644 file3
     create mode 100644 file4
    abhishek@sf-cpu-438:~/Desktop/notes$ git diff f1 f2
    ```
    
- To prevent fast forward merge then use `—no-ff`
- It’s prevent ff and create new commit like “merge f1 and f2”
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ touch file5
    abhishek@sf-cpu-438:~/Desktop/notes$ git add .
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m "created file5"
    [f2 78c2398] created file5
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 file5
    
    abhishek@sf-cpu-438:~/Desktop/notes$ touch file6
    abhishek@sf-cpu-438:~/Desktop/notes$ git add .
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m "created file6"
    [f2 d730cb7] created file6
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 file6
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git checkout f1
    Switched to branch 'f1'
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git merge f2 --no-ff
    Merge made by the 'ort' strategy.
     file5 | 0
     file6 | 0
     2 files changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 file5
     create mode 100644 file6
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git show
    commit 45f8b39ce377db25590a0811e233e22224ace001 (HEAD -> f1)
    Merge: e972ef1 d730cb7
    Author: abhishek <abhishek.v@simformsolutions.com>
    Date:   Wed Feb 15 18:45:40 2023 +0530
    
        Merge branch 'f2' into f1
    ```
    
- Merge all commits then merge branch use `—squash`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git merge --squash f2
    Squash commit -- not updating HEAD
    ```
