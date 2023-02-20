# Git-Github-documentation

## 1. Pull and Merge difference

- Make example of pull request and two branch merge event.

### Push,Pull,Merge,Fetch

#### Basics of fetch

- The "**git fetch**" **command** is used to pull the updates from remote-tracking branches. Additionally, we can get the updates that have been pushed to our remote branches to our local machines.
- We can fetch a specific branch from a repository - `git fetch url b-name`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project$ git fetch origin master
    remote: Enumerating objects: 4, done.
    remote: Counting objects: 100% (4/4), done.
    remote: Compressing objects: 100% (2/2), done.
    remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
    Unpacking objects: 100% (3/3), 720 bytes | 720.00 KiB/s, done.
    From https://github.com/abhishek-simform-v1/project1
     * branch            master     -> FETCH_HEAD
       6a294eb..e192d41  master     -> origin/master
    ```
    
- Then merge, `git merge`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project$ git merge origin/master
    Merge made by the 'ort' strategy.
     hotel.txt | 1 +
     1 file changed, 1 insertion(+)
     create mode 100644 hotel.txt
    ```
    
- Fetch all the branches and objects - `git fetch`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project$ git fetch
    remote: Enumerating objects: 12, done.
    remote: Counting objects: 100% (12/12), done.
    remote: Compressing objects: 100% (6/6), done.
    remote: Total 8 (delta 2), reused 0 (delta 0), pack-reused 0
    Unpacking objects: 100% (8/8), 1.93 KiB | 657.00 KiB/s, done.
   From https://github.com/abhishek-simform-v1/project1
       e192d41..b6e8075  master     -> origin/master
       36b1ee2..d4bdccc  feature1   -> origin/feature1
       45c1c65..86aac13  newb       -> origin/newb
    abhishek@sf-cpu-438:~/Desktop/project$ git merge
    Merge made by the 'ort' strategy.
     hotel.txt | 2 +-
     1 file changed, 1 insertion(+), 1 deletion(-)
    abhishek@sf-cpu-438:~/Desktop/project$ ls
    def.txt  git-practice  hotel.txt  name.txt  text.txt
    abhishek@sf-cpu-438:~/Desktop/project$ cat hotel.txt
    Real Preparika
    ```
    

### Basics of Pull

- Pull request is a process for a developer to notify team members that they have completed a feature. Once their feature branch is ready, the developer files a pull request via their remote server account.
- Pull request announces all the team members that they need to review the code and merge it into the master branch.
    
    ![https://static.javatpoint.com/tutorial/git/images/git-pull.png](https://static.javatpoint.com/tutorial/git/images/git-pull.png)
    
- We can pull a remote repository by just using the git pull command - `git pull`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project$ git pull
    remote: Enumerating objects: 10, done.
    remote: Counting objects: 100% (10/10), done.
    remote: Compressing objects: 100% (4/4), done.
    remote: Total 6 (delta 2), reused 0 (delta 0), pack-reused 0
    Unpacking objects: 100% (6/6), 1.24 KiB | 422.00 KiB/s, done.
    From https://github.com/abhishek-simform-v1/project1
       d4bdccc..46c6a02  feature1   -> origin/feature1
       86aac13..52785fc  newb       -> origin/newb
    There is no tracking information for the current branch.
    ```
    
- For specified branch - `git pull url <b-name>`

### Basics of push

- Push local repo to remote - `git push origin <b-name>`
- Upstream remote - `git push -u origin <b-name>`

<aside>
💡 git pull = git fetch + git merge

</aside>

| git fetch | git pull |
| --- | --- |
| Fetch downloads only new data from a remote repository. | Pull is used to update your current HEAD branch with the latest changes from the remote server. |
| Fetch is used to get a new view of all the things that happened in a remote repository. | Pull downloads new data and directly integrates it into your current working copy files. |
| Fetch never manipulates or spoils data. | Pull downloads the data and integrates it with the current working file. |
| It protects your code from merge conflict. | In git pull, there are more chances to create the merge conflict. |
| It is better to use git fetch command with git merge command on a pulled repository. | It is not an excellent choice to use git pull if you already pulled any repository. |

### Some extra:

- Check the configuration of the remote server - `git remote -v`
- Add a remote for the repository - `git remote add <url>`
- Remove a remote connection from the repository - `git remote rm`
- Change remote url - `git remote set-url <url>`

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


## 2. Rebase

- Try to rebase feature branch with master branch 

### Rebase

#### Basics

- **Rebasing** is a process to reapply commits on top of another base trip. It is used to apply a sequence of commits from distinct branches into a final commit.
- It is an alternative of git merge command. It is a linear process of merging.
- Like, Do c1 and c2 commit on f3 then, Created new branch f4 and checkout same. then commit f1 and f2 on that bracnh.
- Move to f3 branch and do c3 and c4 commit.
- Then move to f4 branch and do rebase - `git rebase <branch-name>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git checkout f3
    Switched to branch 'f3'
    
    abhishek@sf-cpu-438:~/Desktop/notes$ touch file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git add file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m **"c1"**
    [f3 3062c0b] c1
     1 file changed, 1 insertion(+)
     create mode 100644 file.txt
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git add file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m **"c2"**
    [f3 e49fe30] c2
     1 file changed, 1 insertion(+)
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git checkout -b f4
    Switched to a new branch 'f4'
    abhishek@sf-cpu-438:~/Desktop/notes$ git diff f3 f4
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git add file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m **"f1"**
    [f4 5580812] f1
     1 file changed, 1 insertion(+)
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git add file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m **"f2"**
    [f4 40c86aa] f2
     1 file changed, 1 insertion(+)
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git checkout f3
    Switched to branch 'f3'
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git add file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m **"c3"**
    [f3 de1bd0d] c3
     1 file changed, 1 insertion(+)
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git add file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m **"c4"**
    [f3 33ea32e] c4
     1 file changed, 1 insertion(+)
    
    **abhishek@sf-cpu-438:~/Desktop/notes$ git diff f3 f4
    diff --git a/file.txt b/file.txt
    index e649d90..3b73725 100644
    --- a/file.txt
    +++ b/file.txt
    @@ -1,4 +1,4 @@
     c1
     c2
    -c3
    -c4
    +f1
    +f2**
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git checkout f4
    Switched to branch 'f4'
    
    **abhishek@sf-cpu-438:~/Desktop/notes$ git rebase f3
    Auto-merging file.txt
    CONFLICT (content): Merge conflict in file.txt**
    ```
    
- If there are some conflicts in the branch, resolve them, and perform below commands to continue changes -
    
    `git status`
    
    `git rebase —continue`
    
- The above command is used to continue with the changes you made. If you want to skip the change, you can skip as follows -
    
    `git rebase —skip`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git add file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git rebase --continue
    [detached HEAD 95b3209] f1
     1 file changed, 1 insertion(+)
    Successfully rebased and updated refs/heads/f4.
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git log --oneline
    2838537 (HEAD -> f4) f2
    95b3209 f1
    33ea32e (f3) c4
    de1bd0d c3
    e49fe30 c2
    3062c0b c1
    ```
    

![https://wac-cdn.atlassian.com/dam/jcr:c34c17d8-22fd-4df8-9ac6-474ae80bf0e0/02%20Usage.svg?cdnVersion=789](https://wac-cdn.atlassian.com/dam/jcr:c34c17d8-22fd-4df8-9ac6-474ae80bf0e0/02%20Usage.svg?cdnVersion=789)

![https://wac-cdn.atlassian.com/dam/jcr:4e576671-1b7f-43db-afb5-cf8db8df8e4a/01%20What%20is%20git%20rebase.svg?cdnVersion=789](https://wac-cdn.atlassian.com/dam/jcr:4e576671-1b7f-43db-afb5-cf8db8df8e4a/01%20What%20is%20git%20rebase.svg?cdnVersion=789)

- Merge commits, So use `git rebase -i <commit-id>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git add file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m "c1"
    [f4 73a6d63] c1
     1 file changed, 1 insertion(+), 6 deletions(-)
    abhishek@sf-cpu-438:~/Desktop/notes$ git add file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m "c2"
    [f4 7556dfb] c2
     1 file changed, 1 insertion(+)
    abhishek@sf-cpu-438:~/Desktop/notes$ git add file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m "c3"
    [f4 1e37cb3] c3
     1 file changed, 1 insertion(+)
    abhishek@sf-cpu-438:~/Desktop/notes$ git add file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m "c4"
    [f4 625ac3d] c4
     1 file changed, 1 insertion(+)
    abhishek@sf-cpu-438:~/Desktop/notes$ git add file.txt
    abhishek@sf-cpu-438:~/Desktop/notes$ git commit -m "c5"
    [f4 e1a7942] c5
     1 file changed, 1 insertion(+)
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git log --oneline
    e1a7942 (HEAD -> f4) c5
    625ac3d c4
    1e37cb3 c3
    7556dfb c2
    73a6d63 c1
    
    **abhishek@sf-cpu-438:~/Desktop/notes$ git rebase -i 2838
    [detached HEAD 7f279b3] Merged c2,c3,c4
     Date: Thu Feb 16 11:24:15 2023 +0530
     1 file changed, 3 insertions(+)
    Successfully rebased and updated refs/heads/f4.**
    
    abhishek@sf-cpu-438:~/Desktop/notes$ git log --oneline
    0748f68 (HEAD -> f4) c5
    7f279b3 Merged c2,c3,c4
    73a6d63 c1
    ```
## 3. Change commit message

- Commit push on commit in feature branch and then change commit message

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
    
### To update or change last commit message use `git commit -amend`
    
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
    
    
## 4. cherry pick

- Pick some commits from feature branch to master branch

### Basics of Cherry-pick

- Cherry-picking in Git stands for applying some commit from one branch into another branch.
- In case you made a mistake and committed a change into the wrong branch, but do not want to merge the whole branch.
- **You can revert the commit and apply it on another branch.**
- Cherry-pick is a useful tool, but always it is not a good option. It can cause duplicate commits and some other scenarios where other merges are preferred instead of cherry-picking.
- It is a useful tool for a few situations. It is in contrast with different ways such as **merge** and **rebase** command.
- **Use**
    - Scenerio1: Accidently make a commit in a wrong branch.
    - Scenario2: Made the changes proposes by another team member.
- Like we are in branch dev and make some changes and then commit. But If we want this commit in fea branch, So used `git cherry-pick <commit-id>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project/files$ git checkout dev
    Switched to branch 'dev'
    abhishek@sf-cpu-438:~/Desktop/project/files$ git log --oneline
    27b9a5b (HEAD -> dev) okayyy f6
    408155c added restore .
    ac6afc2 added restore
    ```
    
- Pick 27b9a5b (HEAD -> dev) okayyy f6, So…
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project/files$ git checkout fea
    Switched to branch 'fea'
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git cherry-pick 27b9a5b
    Auto-merging files/file6
    CONFLICT (content): Merge conflict in files/file6
    error: could not apply 27b9a5b... okayyy f6
    
    abhishek@sf-cpu-438:~/Desktop/project/files$ git add .
    abhishek@sf-cpu-438:~/Desktop/project/files$ git commit -m "picked f6"
    [fea b214155] picked f6
     Date: Fri Feb 17 12:08:13 2023 +0530
     1 file changed, 1 insertion(+), 10 deletions(-)
    ```
## 5. Drop commit

- Remove some commit from feature branch.
 
```jsx
abhishek@sf-cpu-438:~/Desktop/practice$cat file3.txt
hey there
abhishek@sf-cpu-438:~/Desktop/practice$ git commit -am "file 3 edited"
[feature 5769bda] file 3 edited
 1 file changed, 1 insertion(+)
abhishek@sf-cpu-438:~/Desktop/practice$ git push origin feature
Username for 'https://github.com': abhishek-simform-v1
Password for 'https://abhishek-simform-v1@github.com': 
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 259 bytes | 259.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/abhishek-simform-v1/Practicals.git
   7c19b86..5769bda  feature -> feature
```

- Now to drop the commit we will use reset —hard

 

```jsx
abhishek@sf-cpu-438:~/Desktop/project/files$ git reset --hard 7c19
HEAD is now at 7c19b86 Merge remote-tracking branch 'refs/remotes/origin/feature' into feature
abhishek@sf-cpu-438:~/Desktop/project/files$ cat file3.txt
abhishek@sf-cpu-438:~/Desktop/project/files$
```
