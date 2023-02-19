# Git-Github-documentation
## Rebase

### Basics

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
    
