# Git-Github-documentation
## Working Area, Stashing

### Basics:

- There are mainly three part where git is divided: Working Area, Staging area and repository.
- Working area means we are working on folder locally.
- Staging area means we have use `git add` Command.
- When we add then modified file tracked and ready for next commit.
- Sometimes you want to switch the branches, but you are working on an incomplete part of your current project. You don't want to make a commit of half-done work.
- Git stashing allows you to do so. The **git stash command** enables you to switch branches without committing the current branch.
- Generally, the stash's meaning is "**store something safely in a hidden place**."
- Create xyz.txt and efg.txt files and then add to staging area.
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project$ touch xyz.txt
    abhishek@sf-cpu-438:~/Desktop/project$ git add .
    abhishek@sf-cpu-438:~/Desktop/project$ git status
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
    	new file:   xyz.txt
    ```
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project$ touch efg.txt
    abhishek@sf-cpu-438:~/Desktop/project$ git status
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
    	new file:   xyz.txt
    
    Untracked files:
      (use "git add <file>..." to include in what will be committed)
    	efg.txt
    ```
    
- Stashing xyz file using `git stash` or `git stash save “Message”`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project$ git stash save "back stash xyz"
    Saved working directory and index state On newb: back stash xyz
    ```
    
- Check stash list using `git stash list`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project$ git stash list
    stash@{0}: On newb: back stash xyz
    ```
    
- Add efg.txt to stage area and then back stage with previous command.
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project$ git add .
    abhishek@sf-cpu-438:~/Desktop/project$ git stash save "back stash efg"
    Saved working directory and index state On newb: back stash efg
    abhishek@sf-cpu-438:~/Desktop/project$ git stash list
    stash@{0}: On newb: back stash efg
    stash@{1}: On newb: back stash xyz
    ```
    
- `git stash apply` Command is used for taking last stash value from stashing area to staging area. It will remain in both area. Where `git stash pop` Command is used to pop last stash from stashing to staging area.
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project$ git stash pop
    On branch newb
    
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
    	new file:   efg.txt
    
    Dropped refs/stash@{0} (26ca6e18409ac9523dbac5dd8adea4e8125c784b)
    
    abhishek@sf-cpu-438:~/Desktop/project$ git stash list
    stash@{0}: On newb: back stash xyz
    ```
    
    ```
    abhishek@sf-cpu-438:~/Desktop/project$ git stash apply
    On branch newb
    
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
    	new file:   xyz.txt
    
    abhishek@sf-cpu-438:~/Desktop/project$ git stash list
    stash@{0}: On newb: back stash xyz
    ```
    
- When there are multiple stash then you can use `git stash apply stash@{index}`
- To see what changes happend so used `git stash show`.
- To see details which things changed in file use partial stash. `git stash show -p`
- Delete most recent stash from queue used `git stash drop`
- Drop with stash index `git stash drop stash@{index}`
- Clear stash `git stash clear`
- Create new branch with all the things in stash. `git stash branch <name>`

## Difference

### Basics

- Track the changes that have not been staged - `git diff`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git diff
    diff --git a/README.md b/README.md
    index 29e1836..4b7719e 100644
    --- a/README.md
    +++ b/README.md
    @@ -235,3 +235,381 @@ Following are the types of VCS:
         - BLOB identifiers.
         - Path names.
         - Metadata of all files in that directory.
    +    ^M
    +## Git Configuration^M
    +^M
    +### Git Configuration^M
    +^M
    diff --git a/README.md b/README.md
    index 29e1836..4b7719e 100644
    --- a/README.md
    +++ b/README.md
    @@ -235,3 +235,381 @@ Following are the types of VCS:
         - BLOB identifiers.
         - Path names.
         - Metadata of all files in that directory.
    +    ^M
    +## Git Configuration^M
    +^M
    +### Git Configuration^M
    +^M
    +- **Git config**^M
    +    ^M
    +    Get and set configuration variables that control all facets of how Git looks and operates.^M
    ```
    
- Track the changes that have staged but not committed - `git diff --staged`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git add .
    abhishek@sf-cpu-438:~/Desktop/notes$ git diff --staged
    diff --git a/README.md b/README.md
    index 29e1836..4b7719e 100644
    --- a/README.md
    +++ b/README.md
    @@ -235,3 +235,381 @@ Following are the types of VCS:
         - BLOB identifiers.
         - Path names.
         - Metadata of all files in that directory.
    +    ^M
    +## Git Configuration^M
    +^M
    +### Git Configuration^M
    +^M
    +- **Git config**^M
    +    ^M
    +    Get and set configuration variables that control all facets of how Git looks and operates.^M
    +    ^M
    +- **Set the name**^M
    +    ^M
    ```
    
- Git Diff Branches - `git diff <branch 2>`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git diff master feature
    ```
- Track the changes between two commits - `git diff c1 c2`
    
    ```
    abhishek@sf-cpu-438:~/Desktop/notes$ git diff 974553a6c20e7416e34e4cf34b984727bf4e0eb9 3e39ef51fc1f84de8b605f3c78cc1935b34dab1e
    diff --git a/README.md b/README.md
    index 29e1836..c1657e1 100644
    --- a/README.md
    +++ b/README.md
    
    +    ^M
    +## Git Configuration^M
    +^M
    +### Git Configuration^M
    +^M
    +- **Git config**^M
    +    ^M
    +    Get and set configuration variables that control all facets of how Git looks and operates.^M
    +    ^M
    +- **Set the name**^M
    +    ^M
    +    `$ git config --global user.name "abhishekvaghela"`^M
    +    ^M
    +- **Set the email**^M
    +    ^M
    +    `$ git config --global user.email "abhishek.v@simformsolutions.com"`^M
    +    ^M
    +^M
    +### **Starting a project**^M
    +^M
    +- **Git initCreate a local repository**^M
    +    ^M
    +    `$ git init`^M
    +    ^M
    +- **Clone repository from url**^M
    +    ^M
    +    `$ git clone url`^M
    ```
