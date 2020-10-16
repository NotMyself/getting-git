# Getting Git

Using the git cli can be intimidating at times. It is not uncommon for beginners to get bewildered. It is also not uncommon for beginners to attempt to use a graphical application to attempt to simplify the complexity. Many of these applications assume an understanding of git upfront and use common concepts and language from the cli. This can also be a huge source of confusion as well but now you are one step removed from what is going on!

A better approach is to learn the basics of the cli and get comfortable using it for normal day to day tasks. You can then fallback to apps when a task becomes a burden from the command line. Common tasks like commiting changes, creating branches, obtaining changes from others and merging are a snap on the command line but resolving merge conflicts can be painful and visual apps can make it much easier to accomplish.

## What is Git?

Git is a distributed source control system. That is a mouthful isn't it? But what does that mean? Let's unpack the phrase just a bit.

**Source control** is a process that maintains a set of changes over time applied to a set of files. These files can be a software application, web site or simple text files. It allows you to reverse course and go back to a previous version of your files. For example, creating a copy of your **recipies** folder on your desktop called **recipies-2** and making changes there is a kind of source control.

A **source control system** typically is a piece of software that is designed to do pretty much what was just described. But it tracks the changes for you over time so that you do not need to duplicate files over and over on your drive. They also allow you to go back in time to any point in the past to recover a specific version of your files.

A source control system is typically a centralized server that is considered the single point of truth for the current state of your files. A user submits their changes to the source control system and they are made available to other users from there.

A **distributed source control system** is a kind of source control system breaks the dependance on a centralized server by maintaining all the changes to a given set of files in a cloned instance of the source control system. In this way, you can happily work locally with no connection to any central server and push your changes between cloned instances of the source control system.

At any given time you can have the source control system on your local machine, hosted by a provider like GitHub or Bitbucket, or even stored on a shared drive on a network. Each of these locations share a common set of historical changes to the files but may not have all the changes at time same time. These changes can be distributed to all as needed.

## Let's get started learning

We will start with a set of exercises that will get you working locally with the git commandline interface. We will then progress to working with a remote source control system on GitHub.

## The Path to Enlightenment

1. [Local source control basics](local-basics.md) - In this set of exercises you will create and work with a git repository on your local machine.
2. [Remote source control basics](remote-basics.md) - In this set of exercises you will create and work with a git repository hosted on GitHub.
3. [Quiz](quiz.md) - The quiz will present common scenarios and ask you to write the cli command to accomplish a goal.
