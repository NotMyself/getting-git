# Local Source Control Basics

Using git, a set of changes to a set of files is maintained in a *repository*. 

- [Creating your first repository](#creating-your-first-repository)
- [Commit your first file to the repository](#commit-your-first-file-to-the-repository)
- [Commit your first edits to the repository](#commit-your-first-edits-to-the-repository)
- [Understanding branches in the repository](#understanding-branches-in-the-repository)
- [Create your first branch in the repository](#create-your-first-branch-in-the-repository)

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

**Consider this scenario:** You have been working on your files for an hour. You have made many non-related changes to many files. You want to be able to commit related changes to the repository in discrete sets. You can stage a subset of files and commit them, then stage another subset of files and commit them. You can even stage specific lines with in a given file, but that is a topic for another day.

There are some variations on the add command that are worth noting.

- To stage all the changes to all files at once, execute `git add .`.
- To stage all the changes to files in a given directory, execute `git add /directory-name/`
- You can even stage changes using a file glob, `git add **/*.txt` which will stage all changes to all text files in all directories!

5. To commit the staged files to the repository, execute the command `git commit -m "adding food-jokes"`.
    - This commits the staged changes supplying the commit message "adding food-jokes".
    
6. Execute the command `git status` again.
    - You will see a status message indicating that there are no changes or new files detected in the dadjokes directory.

![clean status](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/Screen-Shot-2020-10-15-at-6.01.23-PM.png)

## Commit your first edits to the repository

1. Add a joke to the file by executing `echo "Why don't eggs tell jokes? They'd crack each other up." > food-jokes.txt`.
    - This will add the joke to the text file, using bash commands.

2. We can look at the contents of the file by executing `cat food-jokes.txt`.
    - Once again, nothing to do with git. This is just s simple way to look at the file from the command line without opening it in a text editor.

3. Check the status again by executing `git status`.
    - You will see a status message for the repository indicating that the file **food-jokes.txt** is a _modified_ file.

4. Stage and commit the changes using a single command by executing `git commit -am "adding a egg joke to food-jokes"`.
    - This approach is a nice shortcut. Use it in cases where you want to commit _**a**ll_ changes and supply the commit _**m**essage_ in one command.
        
![Commit changes](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/Screen-Shot-2020-10-16-at-5.52.36-AM.png)


## Understanding branches in the repository

Before we jump into creating branches, let's step back and discuss what a branch is and why you might want to use one. Imagine if you will, that the commits you have made so far into the repository as a liniar set of of changes through time.

![Commits](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/

.png)

We call this the **master** branch. Think of a branch as a tag that is added to a specific commit in the liniar set of changes.

![Master Branch](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/main-tag.png)

**Consider this scenario:** You want to work on a new joke to add to the food-jokes.txt file. But you are not sure if the joke is going to work, or you want to try some variations and see how they feel. At some point you are going to decide if this new joke is worth keeping around. You do not want the **food-jokes.txt** file in the **master** branch to be modified until you are certain the new joke is perfect.

To handle this in git, we create a new branch to perform the work of creating the new joke. Creating a branch simply adds a new tag to the set of commits.

![New Joke Branch](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/new-joke-branch.png)

We can now commit new changes to the new-joke branch.

![New Joke Butter](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/new-joke-butter.png)

Notice that the butter joke commit simply continues the liniar set of changes but the **new-joke** branch points to the _butter joke commit_ and the **master** branch points at the _egg joke commit_.

Once we are satisfied with the butter joke, we can **merge** the _new-joke branch_ into the _master branch_.

![Merge New Joke to Master](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/merge-new-joke-to-main.png)

Notice here the _master branch_ tag is moved forward in the linear set of changes to the same place as the _new-joke branch_.

**Question:** Why are they called branches instead of tags or pointers?

**Consider this scenario:** While working on the butter joke in the _new-joke branch_, a bug report comes in saying there is a fatal flaw in the egg joke.

Using git, you can switch to the _master branch_ and correct the problem by adding a commit fixing it to the _master branch_.

![New Commit to Master Branch](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/new-commit-main-branch-1.png)

Here we have introduced a divergence in the liniar set of changes. This divergence consists of two commits with a common ancestor commit. And our branches point to the head of each divergent commit.

Now when we merge the _new-joke branch_ into the _master branch_, we create a new merge commit to the _master branch_ tag.

![Merge](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/merge-new-joke-to-main-1.png)

Now both branch tags are pointing to the same commit. We no longer need the _new-joke branch_ and can delete it.

![Delete Branch](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/delete-new-joke-branch-1.png)

## Create your first branch in the repository

Now let's put that theory into practice.

1. List the branches that currently exist in the repository by executing the command `git -P branch`.
    - This will show a list of branches in the repository.

Notice that _master_ is the only branch listed. It has an asterisk to the left of it to show that this is the current working branch.

2. Create a new branch by executing the command `git branch new-joke`.

3. List the branches again by executing `git -P branch`.
    - You will see the list of branches again showing two branches.

Notice that the _master_ branch is still the current working branch, but we have successfully created a _new-joke_ branch.

4. Switch to the new-joke branch by executing the command `git checkout new-joke`.

5. List the branches again by executing `git -P branch`.
    - You will see the list of branches again showing two branches.

This time the new-joke branch has the asterisk indicating it is the active working branch.

6. Add a new joke to the food-jokes.txt file by executing the command `echo "Did you hear the rumor about butter? Well, I'm not going to spread it\!" >> food-jokes.txt`

7. Verify the new joke is in the _food-jokes.txt_ file, `cat food-jokes.txt`.
    - You will see both jokes are contained in the file.
    
![Creating New Joke Branch](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/Screen-Shot-2020-10-16-at-8.45.00-AM.png)

8. Check the status of the repository by executing the command `git status`.
    - You will see a status message for the repository indicating that the file **food-jokes.txt** is a _modified_ file.

Notice that the status message also tells us what branch is currently active.

9. Stage and commit the new joke by executing the command `git commit -am "adding a butter joke"`.

10. Once again check the status, `git status`.
    - You will see a status message indicating that there are no changes or new files detected in the dadjokes directory.

![Adding Commit to New Joke Branch](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/Screen-Shot-2020-10-16-at-9.01.02-AM.png)

11. Switch to the _master_ branch, `git checkout master`.

12. Look at the contents of the _food-jokes.txt_ file, `cat food-jokes.txt`
    - You should see the original contents of the file with a single joke.

13. Switch back to the _new-joke_ branch, `git checkout new-joke`.

14. Look at the contents of the _food-jokes.txt_ file again, `cat food-jokes.txt`.
    - You should see the new butter joke has returned.

The change that adds the butter joke to the _food-jokes.txt_ file only exists in the set of changes in the _new-joke_ branch.

![Switching between Branches](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/Screen-Shot-2020-10-16-at-9.08.33-AM.png)

Now, let's merge the _new-joke_ branch into the _master_ branch.

15. Switch back to the _master_ branch, `git checkout master`.

16. Merge the new-joke branch into the master branch, `git merge new-joke  -m "merging butter joke"`
    - This command will create a new commit that merges the changes from the _new-joke_ branch to the _master_ branch providing an inline commit _**m**essage_.
    
17. Check the content of the _food-jokes.txt_ file, `cat food-jokes.txt`.
    - You will see the file contains the new butter joke.
    
![Successfully Merged File](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/Screen-Shot-2020-10-16-at-9.41.01-AM.png)

Now that we have successfully merged the _new-joke_ branch, we no longer need it.

18. List the branches again by executing `git -P branch`.
    - You should see both _master_ and _new-joke_ branches listed with master marked as the currently active branch.

19. Delete the new-joke branch by executing the command `git branch -d new-joke`.

20. List the branches again by executing `git -P branch`.
    - The _new-joke_ branch is gone!

![Delete New Joke Branch](https://s3-us-west-1.amazonaws.com/iamnotmyself-com/2020/10/Screen-Shot-2020-10-16-at-9.45.50-AM.png)
