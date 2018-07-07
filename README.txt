# "Kevin's Guide to Git"

Table of Contents:
Topic 0. Introduction to Git and this Guide.
Topic 1. What Git is.
Topic 2. The difference between Git and Github
Topic 3. Introduction to Branches and Commits
Topic 4. Crafting commits
Topic 5. A typical workflow example
Topic 6. Resolving conflicts
Topic 7. Rebase and amend
Topic 8. Other software built on top of Git
Topic 9. Aliases and Auto-Complete

Topic A: Commands you should know.

Topic B: Other resources



## Topic 0. Introduction to Git and this Guide.

Git is the name of a "Version Control” (or "revision control") program that many computer programmers use to help them write software. Version control software helps programmers write software by allowing programs to save multiple versions of their projects at the same time, and then combine those versions later. It also helps teams of programmers to work together while writing the a piece of software.

Programmers who are Git experts can use Git to more quickly and more easily write code. Unfortunately, learning to use Git is very difficult and intimidating. The purpose of this guide is to help people get better at using git. It will be helpful for both beginners and experienced users. Because git is so difficult to use, many experienced git users still have a lot to learn.

There are lots of resources online that can help you learn about how to use git. However, I'm writing this guide to make it easier to learn. For one thing, those guides can be very difficult to understand. Another thing, those resources sometimes do a poor job of explaining the core concepts of git. Instead they often focus on the Git commands without giving them context. They can leave out a lot of information that if you knew you would have a much easier time learning and using Git. If you understand the core concepts of git you will be better prepared to make proper use of the commands.

But once you've read my guide and understand the core concepts of Git, you'll be ready to start mastering it. At that point, you will get much more out of the tutorials and references that others have created.

This guide is stored in a public Github repository. You can read this guide online there. You can also see how it changed over time using the history of committed changes. https://github.com/KevinVerre/kevins-guide-to-git

Towards the end of this guide is section of Commands You Should Know. Feel free to skip to that section if you already know a lot about git and just want to learn some new tricks.



## Topic 1. What Git is.

Imagine you are creating a software project. It could be a software application, a website, a mobile app, a script, or anything. You have a folder that contains all of the files relevant to that project: code files, image files, subfolders, maybe some data files, etc. Git is a tool to let you save different versions of that folder. Then you can switch back to older versions if needed. You can also work on multiple different versions (called branches) at the same time and combine them later. The changes between two versions are stored as a list of committed changes called a "commit".

Git is a piece of software. In order to use git, it must be installed on your computer. Computers with Git installed can communicate with and send commands to other computers with Git installed. Of course, the other computer you are interacting with using your computer needs to know it can trust you, so it usually requires a password or a secret key. However, you can also use git just on a single computer. Git is a command line only program, which means you use it by typing in commands to the terminal or command prompt rather than using a graphical user interface. However, there are other programs that allow you to use Git with a graphical user interface. There are even websites that allow you to use git, such as GitHub and BitBucket.

Git was created by Linus Torvalds, a famous programmer from Finland (but now living in the United States). Torvalds became famous for writing and managing the Linux kernel, the open source code that powers Linux operating systems. Git was created by Torvalds to help further development of the Linux kernel. The name “git" comes from British English, where it’s used as an insulting slang word. If you call someone a git, you are calling them idiotic, annoying, or unlikable. The official documentation for the git software jokingly and humbly refers to git as “git — the stupid content tracker”. The Git software was written in the C programming language. It's open source and you can look at the C code that Git is made out of.

Once git is installed on your computer, you can use it to create git projects called repositories. A repository, in computer science, is a place where code and data are stored. A git repository is simply a folder (“directory”) on your machine. We’ll call this the project folder or repository folder. Inside that folder is all of your project’s files and subfolders.

Inside of the repository folder there is also a special subfolder called “.git”. The hidden .git folder is what makes your directory a Git repo. The .git folder is created when you create a new git repository. As you use the git program to make changes to your project, the git program will save information inside the .git folder. You can look around inside the .git folder if you want, but it is not necessary to know much about it in order to use Git. It is simply a place for the .git program to store information without it getting in the way of your project’s files and folders. Whenever you run a Git command, the Git program will look for that hidden .git folder and use the files and folders inside of it to find information about commits, branches, etc.

In Unix, files and folders whose name starts with a period are not shown by default when using the “ls” command to list the contents of a folder. Instead you have to use “ls -a”, which will list all of the contents of a folder, including files and folders that begin with a period. So if you do “ls -a” inside of a git repository folder, you should see the .git subdirectory.

The repository folder contains the .git subdirectory but will also contain a tree of other subfolders and files. Any folder or file that is inside of the repository is considered to be part of the git repository. However, the special .git subfolder only appears in one place: inside of the top-level repository folder. This means that the other subfolders in the repository do not contain a special .git subfolder.

You can have multiple different git projects/repositories on your computer at one time. So when you perform a git command, the program git needs to know which git project you are trying to perform the command on. It will use your current location in the directory structure (your Present Working Directory or ‘pwd’) to know which git repository you are working on. When you run a command from inside of a git repository, the command will be performed on the git repository you are currently in. It figures out which repository you are in by looking for the special .git folder. It finds by the .git folder by looking for it in your current directory, and if it is not there, looking for it in each of the parent directories of your current directory. It uses retrieves information stored inside the .git folder when commands are executed.

If you try to run a git command while you are not somewhere inside of a git repository you will see this error message:
"fatal: Not a git repository (or any of the parent directories): .git"
That means that, based on the folder you ran the command in, it couldn’t find a .git folder in the current folder or any of the parent folders, so you are not in a git repository.

To create a git repository, you use the command “git init” along with the name you want to give to your project. So “git init super_marlin_bros” will tell git to create a new subdirectory called “super_marlin_bros” inside whatever directory you are currently in. This new directory “super_marlin_bros” is your repository folder. And as part of the initialization process, the program git will create a .git folder inside of your repository folder. You can also use “git init” to initialize a git repository based on an existing folder rather than creating a new folder. In that case, just give the name or path of the folder you want to turn into a git repository folder, and “git init” will create a .git subfolder inside of it.

Another way to create a git repository folder on your computer is by “cloning" a git repository that already exists somewhere else. This is a very common way of creating a git project. And we’ll talk more about it later.

Different git repositories can interact with each other using the git program. So if you and I are both working together on a project, I can have a git repository that contains the project’s code on my computer and you can have your own git repository folder that contains the project’s code on your computer. Then you could use the git program to update the files in your folder on your computer based on the changes I made on my computer.

In practice, it is uncommon to have two team members’ repositories interact directly. Instead, it is typical to create an extra repository somewhere that all of the team members can access. This is usually called the “origin” repository. It exists on a computer that all of the team members have permission to interact with. And it’s usually hosted on a server computer that is turned on at all times so that at any time a team member can push their work to the origin repository. And any time later, the other team members can pull those changes from the origin repository to their own repository. The repository that you are working out of on your own computer is called the “local” repository. The origin repository and the repository folders belonging to other team members are “remote” repositories from your point of view because they (almost always) don’t exist on the same computer as yours.

The git program can use the special .git folder to store information not just about your local repository but also information about the files and folders in remote repositories that you have permission to view. In practice, there is typically only one remote repository that you care about (“origin”), but in theory you can have information about any number of remote repositories stored in your .git subfolder. The process of downloading updates from a remote repository and storing the content of those updates into your .git subfolder is called fetching. If you fetch a remote repository, you can see the code that was on that remote repository at the time you fetched even if you are not connected to the Internet or to that remote repository!

Git is sometimes called a “distributed revision control system”. Git is “decentralized” because the git software is written in such a way that all of the git repositories for a particular project are peers (equals). For example, let’s say we have three git repositories for the same project. One is on my computer, one is on your computer, and one is on a server that we can both push changes to via Git. All three of these computers are running the same git software. Even though we are choosing to treat one of those repositories (the one on the server) as special, there is nothing about the way its git software or .git subfolder is set up is different than the other repositories.

In practice, you typically have a central git server running all of the time that allows you to fetch from an origin repo. But even if it were to go offline, you can save all of your changes locally and push your changes at a later time.



## Topic 2. The difference between Git and Github

It's common for beginners to mix up Git and Github. Git is a program that you can install on your computer. By default, it is a command line program without a user interface. Git allows you to share code files that are on your computer with other computers, such as your teammates or your company's server.

Github is a website (and the company behind the website). You can almost think of Github as a program running on top of Git that adds additional features. Because Github has Git running on their servers, you can share your code back and forth between your computer and the Github servers. There are a few reasons why you might want to do so. For one, storing your code on their servers is convenient. Their servers are always running and are safe because your stuff is protected by your usernames and passwords. That way, anyone on your team can always access the repository stored on Github through the Internet. While Git does not require a "central" repository, teams use Github as a central repository for convenience. When they want to share new code they've written, they push to Github. And when you want to see new code that someone else has written, you pull it from Github rather than pulling it directly from your teammate's computer.

Github offers a free version and a paid version. If you use the free version, all of your code is publicly visible. This lets people see it, (but not make any changes to it). With the paid version, you can control who can see your code. But there are reasons why you might want other people to see your code. For example, to show it off or to allow other people to make suggestions for improvements.

In addition to the paid version of Github, there is also an Enterprise version of Github that allows you to run a Github server on your own servers.

Github's website comes with a lot of tools to make using Git easier. You get to use the UI in your browser rather than the command line.



## Topic 3. Introduction to Branches and Commits

So your Git project repository is a folder that contains all of the subfolders and files for the project inside of it. A branch is a version of that folder. Each branch has a name and belongs to a repository. Each repository can have as many branches as you want. And if your repository has permission to interact with another repository for the same project, you can see their branches. Let’s say you want to have two different versions of your folder at the same time, you could do it just by having two branches. Or you could have two different branches that represent the exact same version of the project folder.

You can think of a branch as being a series of commits. Commits are the units with which you build your Git repository. A single commit can contain any number of changes to any number of files. A commit can say that a file was added or removed to the folder. A commit can say that a certain line in a plain text file was removed or that a certain line was added.

Each git repo starts out with one branch, called "master". But you can create a new one at any time. When you create a new branch, it is only stored in your local repo. But you can also push branches to another repo if you want. When you switch from working on one branch to another branch, Git will modify your files and folders to flect the state of your code at the end of that branch.

The latest commit on the current branch is called HEAD. The commits before it are HEAD~1, HEAD~2, HEAD~3, etc.

A commit is a collection of changes to the repository. And a branch is a collection of commits that is the result of all the commits being applied one after another. They are called branches because they form a tree structure. Typically a secondary branch of commits branches off from another more primary branch. Then, if you later want that secondary branch to be included back into the main branch, you can merge it into the main branch.

What does a commit contain? A commit contains the following fields: a commit hash (which is used as an ID string), a commit message string, the changes (to all relevant files and folders), an author name string, a datetime. You identify a commit by its commit hash. But you don't have to use the whole thing: if you get the first several characters Git will try to figure out which commit you are referring to. This hash comes from a hash function that takes in all of the data related to the commit (including the commit message). Which you can't really "edit" a commit, but instead have to replace it with a new commit with a new hash.

Git also a feature called Tags. These let you give a String name to a particular commit which can be used to refer to that commit elsewhere. But many people use Git without using tags, so I consider it an advanced feature.



## Topic 4. Crafting commits

A commit is a collection of changes to the repository. Changes to the repository can include adding a new file, removing a file, or changing the lines within a file.  A change to the repository can either be staged or unstaged. A staged change is one that you are getting ready to use in a commit. You create a commit by making changes to the repository, staging the changes you want to commit, and then creating a commit out of the staged changed.

The command “git status” will show you the status of all of the changes made to the repository since the last commit. It will show you if files were added, removed, or changed. The command “git diff” will show you how the files have changed. The command “git diff --staged” will show the changes to the repository that are staged. By default, “git diff” will show you the differences for the entire repository. You can also show the changes to a particular file by using “git diff FILENAME”. The repository you are working on is sometimes called the “working directory” and the differences that you’ve made are changes to the “working tree”. Another name for the stage is the “index”.

The next step is to “stage” the changes by adding them to the “stage”. If you added a new file or made a change to a file, you can stage that difference by using the command “git add FILENAME”. If you removed a file, you can stage that difference to the repo by using the command “git rm FILENAME”. Of course, staging each file individually can get tedious so you don’t have to do it that way. You can stage all of the changes to a folder (including changes to folders inside that folder) by using “git add DIRECTORY”. And of course the period means the current directory you are in, so it is common to do do “git add .”. Sometimes you might want to give this command an argument. By default, "git add DIRECTORY/FILENAME” will stage new files and changes to files but it won’t stage that a file has been removed. So the argument -A tells it to stage all changes, including removing files. So if you are in the root directory, the command “git add -A” will add of all the changes you made to your working tree to the stage.

Why do we having a staging process? The stage help you to create commits exactly as you want them to by giving you a place to see what’s going to be in the commit before it is created.

Occasionally, you might find that there are some changes to a file that you want to stage and other changes to a file that you don’t want to stage because you don’t want to keep those changes. Using “git add -p” will let you go through the differences in that file and choose which smaller changes (called “hunks”) you want to add and which you don’t.

Sometimes you will want to remove a change from the stage. As “git status” will tell you, you can use “git reset HEAD <filename>” to remove that file’s changes from the staging environment but keep the changes in the working tree. I’m not sure why the command is “git reset HEAD” though, because it doesn’t discard your changes that you made to HEAD, just unstages them.

You can also unstage a change if you decide you don’t want it.

Concept: Gitignore
    Sometimes you want to have files in your repository folder without having those files be "tracked" as part of the repository. So you need a way to tell git which files in your repository folder should not be tracked. You do this by creating .gitignore files inside of your repository.
    Files that are ignored won't show up as being untracked in git status. And they won't be added to the staging area when using git add.



## Topic 5. A typical workflow example

Now we'll run you through an example of how a team might typically use Git.

You'll start by creating a folder that contains all of your code and files. When you're ready to start using Git with that project, you can initialize a Git repo in that folder. Immediately, you'll have a master branch with no commits and all of the existing files and folders will be unstaged changes. You can stage the entire directory. The change will be represented as adding all of your files and folders since you started out with nothing and adding everything will get you to where you are.

Since you want to store your work in the cloud, you find an instance of a Git server running on the Internet. Most people use Github or Bitbucket or something like that, either the free version or a paid version. But you can also run your own Git server if you really want to. If you have your credentials set up, you can push a copy of your Git repo to the cloud. This will act as your origin repo. You can set your local master to point to the origin's master branch as its upstream branch. This lets you keep track of how many commits you are ahead or behind that branch.

Your co-worker, Betty, can clone the repo from the cloud to her local computer. If she wants, she can push new commits or new branches to origin. To prove she is who she says she is, she might have to create a ssh key from a password.

After working on the project for some time, you decide you want to code a new feature. You will create a new branch to put all of the new code changes related to that feature in. This is called a feature branch.

Before you do that, you will need to make sure your master branch is up to to date. So you checkout master and pull any commits from origin/master to local/master. From master, you create a new branch and call it "new-video-player". (Or whatever describes the feature you're working on.) You create several commits on this branch until it's working to your satisfaction.

During the time you worked on your feature branch, the master branch has moved ahead a couple commits. So it's good practice to merge the latest master branch head into your feature branch. That way all of the commits from master branch will be in your feature branch, including the ones that you didn't have when the feature branch was first created. This might cause some merge conflicts, in which case a new commit will be created to address those conflicts. This way, you'll have already dealt with those conflicts when it is time to merge the feature branch back into the master branch.

When you're ready to share what you've built with your co-worker, you push your new branch to origin as a remote copy of that new branch. Now your co-worker, Betty, can copy the feature branch from origin/new-video-player to her local repo and check it out. She tests out the new feature that you built and looks over your code.

Everything looks good, so you are ready to release your new feature. You merge your feature branch into your local master branch. Now your local master branch is ahead of the origin master branch. You push your master branch to origin so that it is all caught up with you. Now, the next time you deploy master branch to product, it will contain your new feature. Also, you might have a production branch on origin that represents the version of master that is deployed into production.



## Topic 6. Resolving conflicts

Git keeps track of the files and the changes made to them over time. If it is a text file, it can point out which line(s) were changed and how. If it is an image file or some other non-text resource, Git will just notify you that the binary of the file has changed.

In a single branch of sequential commits, a conflict cannot arise. One commit might modify a line. Then the next commit could possibly modify the same line. But it would always know the order. Both the "before" and "after" versions of that line would be appropriate.

But when commits from one branch are merged into another branch, it's possible that the changes in the commits conflict. Imagine a line of code is original Version A. In one branch B, that line of code is changed from Version A to Version B. But in the other branch C, that line is changed from Version A to Version C. If you simply tried to apply change C after change B, it would result in a conflict because change C assumes Version A as a starting point rather than Version B.

So what Git will do is mark all the conflicts across all files. Then ask you to manually merge them. Then when you're done merging them, it will create a new commit to merge them as you wanted. Depending on the logic of the code and the changes you are trying to make in each branch, you can decide what is best to do about the conflict. For example, you might decide that if each branch has different code at that line, that the merged version should contain both lines of code, one after another. Or you might decide that you want one and can delete the other. Or you might decide that you want a completely new version of that line that correctly combines the ideas behind both changes.



## Topic 7. Rebase and amend

Rebase is a powerful command that advanced Git users can use. It allows you to re-write the git commit history and juggle around commits. You can even sort of edit a commit by replacing creating a replacement commit for it. You're actually not really editing the commit, but rather replacing it with a commit that is the old commit plus whatever new changes.

Rebase allows you to take one or more commits and re-apply them (with new changes) to the current branch. For example, you can use rebase to re-order the commits in a branch. Or you can split a single commit into two commits. Or to combine two commits into a single commit. Or you can remove a commit from a branch. Or you can edit the commit messages.

You can also use rebase to move commits from one branch to another. In this case, it is possible to have merge conflicts just like you would when merging two branches.

I use Interactive Mode (git rebase -i) when rebasing. This brings up a little text file that you edit in Vim. This file acts as instructions for the rebase. When you save and exit, the rebase procedes using those instructions.

Rebasing is considered a somewhat dangerous action because it can be used to remove commits. And any time you edit a commit you are really just deleting it and replacing it with a new commit. As long as you are only deleting commits on a local branch that you haven't pushed anywhere, this is not an issue. For example, I will sometimes rebase commits in order to combine multiple commits into a single more comprehensive commit to make the commit history cleaner.

Things can get messy if you rebase commits on a branch that has already been pushed to the origin repo or a branch being used by someone else. Because now your version of the branch is missing commits that the original had, and has different commits instead. This is essentially a meta merge conflict, because Git doesn't know which commits should be included in the branch. Those conflicting commits have to be manually resolved in order for the two branches to get in-sync again. It's not the end of the world if it happens, but that's why it is considered bad practice to rebase a branch's commits that have already been pushed.

You can read more about rebase in Git's documentation "git rebase --help".

"git commit --amend" is a handy command to know. It is essentially a very small, quick and easy rebase. It only modifies the most recent commit on the current branch (HEAD). It allows you to modify the commit message for that commit. Also, any changes that are currently staged when this command is run, will be included as part of that commit. Of course, behind the scenes what this is doing is actually deleting the commit and creating a new one to replace it, with a new hash ID and everything. This lets you quickily and easily add something that you forgot to write or stage into a commit you just created.



## Topic 8. Other software built on top of Git.

The most common software built on top of Git is programs that allow you to use Git with a GUI interface instead of the command line.

Some text editors and IDEs come with built in Git functionality. For example, Apple's Xcode.

"Gitless" is a command line interface built on top of git that is designed to be easiler to learn how to use than Git.

Other programs are built on top of Git and creatively take advantage of git's abilities to keep different versions of files in sync. For example, Ruby on Rail's package manager "RubyGems" uses Git repos to store and share code.



## Topic 9. Aliases and tab-completion

Once you get good at using Git, you'll want to learn how to use git faster. There are two great ways to do this: aliases and autocomplete.

You can setup aliases to make git commands shorter so that you don't have to type as much to run a command. There are (at least) two different places you can configure this.

The first is in the global git config file for your username. By default, this is a file stored in ~/.gitconfig . You designate the alias section of the config file with [alias]. Here are some that I have in mine:

        co = checkout
        ci = commit
        amend = commit --amend
        s = status
        st = status
        sh = show
        b = branch
        br = branch
        p = pull
        d = diff
        l = log
        a = add

You can also create aliases for your terminal, such as your ~/.bashprofile. Example: alias gs='git status '

Git also has a tab auto-completion tool. This way you only have to start typing the name of a branch (or other identifier), hit tab, and it will try to finish the complete name. It doesn't come built in with Git. You have to I'd call it semi-official since it's available in the same repo as git's official source code. But it's not part of their main project. You can download the version for bash from here, and then source it in your bash_profile:

https://github.com/git/git/tree/master/contrib/completion



## Topic A. Commands you should know.

git “command” --help
     Git will show you the Help page for the command if you add --help
git diff
	Shows you the changes to files in the repository that haven't been added to the staging area.
git diff --staged, git diff --cached
	--staged and --cached do the same thing. Both show you which changes to your repository have been added to the staging area. Meaning, these changes have been selected to be part of the next commit

git checkout -
	The dash argument will checkout the previous branch you were on before your current branch. (Similar to how `cd -` changes your directory to the previous one you were in.)

git init “foldername"
	create a new directory with "foldername" as the name. Then create a new git repo in that directory.
git init ./
	initialize a new git repo in the current directory
git status
	Shows the current status. Includes which branch you are on. What changes have been made to the files, and whether those unstaged changes or changes that have already been staged. Also shows if your current branch is behind its upstream branch. 
git branch
git branch -r
git branch -v
	Shows more verbose info about the branches, such as what is the latest commit in each
git branch -vv
	Shows EVEN MORE verbose info about the branches, including the upstream branch for each branch that has one
git show
	Same thing as "git show HEAD"
git show HEAD
    Shows the contents of the HEAD commit (the latest commit in the current branch)
git show “commit-hash"
	Shows the contents of a particular commit.
git log --graph
	Prints out a graph so you can see how branches were merged
git log -n 3
	Use -n x to only show information about the X latest commits
git log --oneline
	Use the --oneline argument to only print out one line per git commit
git log --reverse
	This flag shows commits beginning from oldest to newest instead of newsest to older.
git fetch
	You local repository stores information about what it knows about the remote repository. Calling git fetch tells git to communicate with the remote repository and update what your local repository knows about it.

git fetch -p
	By default, git fetch will update what your local repository knows about the remote repository. It will download new commits and branches. But if a branch is deleted on the remote repository, your local storage will not delete the corresponding local-remote branch. However, if you use -p for prune it will delete any local-remote branches that no longer have a corresponding branch in the remote repository.

git merge “other_branch"
	This will merge the “other_branch” into your current branch. Unless the merge is a fast-forward merge, this will create a “merge commit”.

git pull
	This does two things. First, it does a git fetch. This means that your local repository will have all the updates from the remote repository stored in the form of remote branches. Also, if you are on a branch that has an upstream remote branch, it will merge that upstream remote branch (which is now a local-remote branch because of the Fetch) into your current branch

git add -p FILENAME
	Have you ever wanted to stage some of the changes in a file but not all of the changes in that file? You can do this with the --patch argument, or -p for short. Git will go through all the changes in the file. To make this go quickly, it does it in "hunks" of lines instead of individual lines. A hunk is a group of lines that are next to each other. For each hunk, you can tell Git if you want to stage it, or move on to the next hunk. You can even tell it that you want to break down the hunk into individual lines if you want to get really specific about what you add to the staging area.

	When this is done, try running the `git status` command. You'll see the filename appear in the both the list of files with staged changes and the list of files with unstaged changes.

git commit --amend
	This makes changes to the latest commit on your current branch (HEAD). It allows you to do two things. One, it allows you to modify the commit message of your most recent commit (HEAD). It will also combines your staged changes with HEAD. I use this if I create a commit but then realize there is another change I want to make to the files and add to that commit. So this is a very convenient way to modify the contents of your most recent commit.

	Note that this actually deletes your HEAD commit and creates a new commit (with a new commit hash) to replace it. It's a type of "rebase".

	This is a very clean way of editing a commit you just made but haven't pushed or merged anywhere else. In this case, you're removing a commit from your current branch and relacing it with the new commit that contains the amendments.

	However, it can get a little ugly if you use it on a commit that you have pushed or merged to another branch. Because now there are two commits: the amended version on your current branch and the original version on some other branch. These two commits will conflict with each other if you try to merge them. Usually this isn't too bad since Git will know how to automatically resolve simple merge conflicts. But it can potentially get messy.

git clean
	Used for cleaning up (deleting) untracked files in your repo. Because this command deletes files from your computer, it requires an extra argument (-f) to force it to do anything
git clean --dry-run
	The --dry-run argument prints out which files will be removed without actually removing any files
git clean -f
	The -f argument (or --force) tells git that you are serious about removing those files
git clean -d
	Deletes untracked directories as well as files

git blame "filename"
	Show which commit (and which commit author) is responsible for each line of the file.

git reset
	I use this to get rid of commits

git checkout <commit> <file>
	I use this to revert to a particular version of a file. It will stage the differences for that file from <HEAD> to <commit>. So that if you committed, you would have the old version of the file.

git bisect
	This is a tool (that comes with git) that you can use to find when a bug was introduced to your code. What it does is help you checkout old commit versions of your code. For each commit, you manually test for the bug and then you tell the command prompt whether or not the bug was present. If you have a script or command you could run to test for the bug, you can configure the bisect tool to run that command on every bisection.

	Not everyone will need `git bisect` but it's nice to know that it's there if you ever need it for a giant project.

git rebase -i <commit/branch>
git rebase -i HEAD~3
	Starts a rebase procedure in Interactive Mode. Interactive mode allows you to see what commits will be re-applied and make any changes before they are re-applied. In the example HEAD~3, I am rebasing the last three commits of my current branch. The fourth to last commit (3 commits before HEAD) is acting as the end of the branch and I'm rebasing all of the commits that come after HEAD~3 on top of HEAD~3.



## Topic B. Other resources.

The company Atlassian, which makes tools for software developers, has some great educational web pages about Git. You can read these web pages for free. Atlassian is now the parent company of BitBucket, a product that competes with GitHub.

GitHub.com also has some good, free resources and tutorials to help people learn Git.

The official Git website has a free book that covers all the features of Git. It's called 'Pro Git': https://git-scm.com/book



