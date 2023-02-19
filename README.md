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
    

