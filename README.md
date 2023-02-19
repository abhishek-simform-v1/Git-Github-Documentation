# Git-Github-documentation

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
