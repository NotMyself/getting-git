# Local Source Control Basics

Using git, a set of changes to a set of files is maintained in a *repository*. 

## Creating your first repository

It is pretty easy to create a repository using git.

1. Open your terminal application.
2. Create a new directory on your local file system to hold our source files, execute the command `mkdir dadjokes`.
3. Change directories into the one you just created, execute the command `cd dadjokes`.
4. Verify there are no files in the directory, execute the command `ls -a` to show any files, even hidden ones, in the directory.
    - You should see none.
5. Create a new empty repository, execute the command `git init`.
    - This will _**init**ialize_ a new repositorying with no changesets.
6. Execute the command `ls -a` again.
    - You will see a hidden directory named **.git**. This is where the changesets and the source control system will live locally on your machine.

![Create a new repository](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/Screen-Shot-2020-10-15-at-5.32.18-PM.png)

## Commit your first file to the repository

1. Create a new file in the dadjokes directory, you can do this from the command line by executing the command `touch food-jokes.txt`.
    - This will create a new empty text file named **food-jokes.txt**.

Currently, the repository is unaware it should be tracking this file. We can check with the repository with the **status** command.

2. Execute the command `git status`.
    - You will see a status message for the repository indicating that the file **food-jokes.txt** is an _untracked_ file.

![Untracked Status](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/Screen-Shot-2020-10-15-at-5.36.45-PM.png)

Making the repository begin tracking a new file is a two step process. First you stage the changes, and then you commit the current staged changes to the repository.

3. Stage the changes by executing the command `git add food-jokes.txt`.
4. Execute the command `git status` again.
    - you will see the status message has changed to refelect that you have a single file staged to be added to the repository.
    
![Staged Status](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/Screen-Shot-2020-10-15-at-5.45.10-PM.png)

This might seem silly at first. Why do I need to stage the file and then commit it? 

Consider this scenario: You have been working on your files for an hour. You have made many non-related changes to many files. You want to be able to commit related changes to the repository in discrete sets. You can stage a subset of files and commit them, then stage another subset of files and commit them. You can even stage specific lines with in a given file, but that is a topic for another day.

There are some variations on the add command that are worth noting.

- To stage all the changes to all files at once, execute `git add .`.
- To stage all the changes to files in a given directory, execute `git add /directory-name/`
- You can even stage changes using a file glob, `git add **/*.txt` which will stage all changes to all text files in all directories!

5. To commit the staged files to the repository, execute the command `git commit -m "adding food-jokes"`.
    - This commits the staged changes supplying the commit message "adding food-jokes".
    
6. Execute the command `git status` again.
    - You will see a status message indicating that there are no changes or new files detected in the dadjokes directory.

![clean status](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/Screen-Shot-2020-10-15-at-6.01.23-PM.png)
