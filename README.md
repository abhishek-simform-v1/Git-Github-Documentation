# Git-Github-documentation
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
