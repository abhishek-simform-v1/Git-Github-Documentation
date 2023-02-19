# Git-Github-documentation
    
## Push, Pull, Fetch and Remote

### Basics of fetch

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
