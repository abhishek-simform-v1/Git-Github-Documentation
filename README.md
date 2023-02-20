# Git-Github-documentation
## Git Basics

### **What is Version Control System?**

**Version Control System (VCS)** is a software that helps software developers to work together and maintain a complete history of their work.

Following are the types of VCS:

1. Centralized version control system (CVCS):
    - Store all files and enables team collaboration.
    - Drawback of CVCS is its single point of failure.
    - Disk of the central server gets corrupted and proper backup has not been taken, then you will lose the entire history of the project.
2. Distributed/Decentralized version control system (DVCS):
    - Latest snapshot of the directory but they also fully mirror the repository.
    - You can commit changes, create branches, view logs, and perform other operations when you are offline.

### **What is Git & It's Advantages?**

- Free and open source
- Fast and Small
- Implicit Backup
- Security
- Easier branching

## Git Objects

### What is Blob?

- BLOB stands for **Binary Large Object.**
- Each version of a file in Git is represented as a BLOB. A BLOB holds a file’s data but doesn’t contain any metadata about the file or even its name.
- **Example:**
    - Created new directory called practice.
        
        ```
        abhishek@sf-cpu-438:~/Desktop$ mkdir practice
        abhishek@sf-cpu-438:~/Desktop$ cd practice
        ```
        
    - Initialized practice.
        
        ```
        abhishek@sf-cpu-438:~/Desktop/practice$ git init
        Initialized empty Git repository in /home/abhishek/Desktop/practice/.git/
        ```
        
    - Remove hooks and see tree.
        
        ```
        abhishek@sf-cpu-438:~/Desktop/practice$ rm -rf .git/hooks
        abhishek@sf-cpu-438:~/Desktop/practice$ rm -rf .git/hooks
        ```
        
        Output:
        
        ```
        .git
        |-- HEAD
        |-- branches
        |-- config
        |-- description
        |-- info
        |   `-- exclude
        |-- objects
        |   |-- info
        |   `-- pack
        `-- refs
            |-- heads
            `-- tags
        
        8 directories, 4 files
        ```
        
    - Created three files: file1 - Hello, file2 - Hello and file3 - Hello World
    - Add to stage area. Whenever we are adding to stage area then blobs are created for each n every distinct file.
        
        ```
        abhishek@sf-cpu-438:~/Desktop/practice$ touch file1
        abhishek@sf-cpu-438:~/Desktop/practice$ touch file2
        abhishek@sf-cpu-438:~/Desktop/practice$ touch file3
        abhishek@sf-cpu-438:~/Desktop/practice$ git add .
        abhishek@sf-cpu-438:~/Desktop/practice$ tree .git
        ```
        
        Output:
        
        ```
        abhishek@sf-cpu-438:~/Desktop/practice$ cd .git
        abhishek@sf-cpu-438:~/Desktop/practice/.git$ cd objects
        abhishek@sf-cpu-438:~/Desktop/practice/.git/objects$ ls
        55  e9  info  pack
        ```
        
    - Add two empty file. It will add blobs for empty file also.
        
        ```
        abhishek@sf-cpu-438:~/Desktop/practice$ touch file4
        abhishek@sf-cpu-438:~/Desktop/practice$ touch file5
        abhishek@sf-cpu-438:~/Desktop/practice$ git add .
        abhishek@sf-cpu-438:~/Desktop/practice$ tree .git
        ```
        
        Output:
        
        ```
        .git
        |-- HEAD
        |-- branches
        |-- config
        |-- description
        |-- index
        |-- info
        |   `-- exclude
        |-- objects
        |   |-- 55
        |   |   `-- 7db03de997c86a4a028e1ebd3a1ceb225be238
        |   |-- e6
        |   |   `-- 9de29bb2d1d6434b8b29ae775ad8c2e48c5391
        |   |-- e9
        |   |   `-- 65047ad7c57865823c7d992b1d046ea66edf78
        |   |-- info
        |   `-- pack
        `-- refs
            |-- heads
            `-- tags
        
        11 directories, 8 files
        ```
