# git commands for windows:

=============================================

# For minimal configuration like User Name or User Email

git config --global user.name "Your Name"
git config --global user.email "Email"

=============================================

*To be able to access code editor anywhere from the system add code's exe file path to path variable in environment variables

============================================

# For changing default editor for git:

1. create or update bash alias to provide custom short command for the editor

	create or open your ._profile file by typing
		editor_exe_file_name ~/.bash_profile
	within this file a line 
		alias any_command_you_wanna_use="editor_exe_file_name -multiInst -nosession'
	now save this file

2. Now we have our code editor accessible from within git bash, we can make that editor default editor for git which can be done by using git global command

	type in gitbash
		git config --global core.editor "editor_exe_file_name -multiInst -nosession"
	To check is it has worked type
		git config --global -e

============================================

# To P4merge git integration (p4merge as diff tool)

	Type in git 
		git config --global diff.tool p4merge
	than type
		git config --global difftool.p4merge.path "C:/Program Files/Perforce/p4merge.exe"
	than type
		git config --global difftool.prompt false
		
# To P4merge git integration (p4merge as merge tool)

	Type in git 
		git config --global merge.tool p4merge
	than type
		git config --global mergetool.p4merge.path "C:/Program Files/Perforce/p4merge.exe"
	than type
		git config --global mergetool.prompt false

===========================================

# we can make a custom project by opening terminal or git bash anywhere and using cd "path_we_want_to_direct_terminal _to" or just open git bash in that folder and use command 
		mkdir project_folder_name
# than we can create our working directory folder by using 
		git init folder_name
# it will create a folder with .git folder inside which is where our repository is located, we can also do this by making a folder manually and using
		git init . or git init 
	by directing our git bash into that folder, this will create a .git folder in that folder.

# than we can make files in the working directory by using 
		default_editor_name file_name.extension
->this will create and open the file in the default editor.

# We can add this file in staging area by using
		git add filename.extention
		git add .a(this adds all the files in working dir)

# now the file is created but not commited yet which is staging area, we can commit the file into the repo by using 
		git commit -m 'commit_message'
	this can also be done by using only
		git commit
	which will prompt you to the default git_bash editor and you can type your commit message in the editor which be a single or multiline.

# We can check status of working directory by using
		git status	
# We can delete our local repository recursively by using 
		rm -rf .git
# We can check our commits by using 
		git log
		git show
# To check what files git is tracking use 
		git ls-files
	it will show files only which are tracked or we can say which are commited yet
# we can add new files using git bash by typing 
		touch new.file
	after making this file, if we use "git status" command we will see this file as "untracked files" which is not added to staging area yet and it will not show in the "git ls-files" command.
# We can remove the file by using bash remove command
		rm new.file
# If we want to unstage some changes we made before commiting them we can use
		git reset HEAD file.name
	it will only unstage the changes that have been added, but if we want to delete those changes completely, even from the file and go back to last stage that has been commited, we can use
		git checkout -- file.name
# Add & commit in a single command:
	We generally add some files and after then commit them. However, this can be done using a single command only when there is not any new file.
		git commit -a -m 'commit message'
# To see the history of the git commits, branches etc
		git help log
	this will show allot of information but to see most important in just a few lines history use 
		git log --online --graph --decorate --all
# To make our own short version of long commands we can use alias command
		git config --global alias.any_short_command_we_want "command_except_git"
		git config --global alias.hist "log --online --graph --decorate --all"
# To list out git config entries
		git config --global --list
# To rename some file added use move command
		git mv old_file.name new_file.name
	although it will stage the changes not commit them.
# If we want to make some changes externally like creating a file or renaming, these files will not be staged on thier own. So, we need to add/stage them 
		git add -u(update)
	this will only update the file which has already been staged. to update all the files which has been been staged or not staged in git repo we can use
		git add -A(update and add all the files in working directory)

# To check branches we use 
		git branch
	it will list all the branches, if we want create a new branch and switch to it we can use 
		git checkout -b branch_name
	-b denotes creating the branch and -d is for delete, to only switch to a branch use
		git checkout branch_name
	we can merge branches with some branch by switching to it and than use 
		git merge name_of_branch_you_want_to_merge_with_current_branch
# We can use "git diff" to see changes b/w commits and branches etc
		git diff 1st_commit/branch 2nd_commit/branch
		git difftool 1st_commit/branch 2nd_commit/branch
# if we "cat" the file, it just outputs the entire contents of that file

# So, if we want to mark some point in the repository with some type of milestone. We can use 
		git tag tag_name
		git tag -a tag_name -m "tag_message"
	we can list by 
		git tag --list
	we can also use our "git show" command, and then specify our tag name. This is really useful when you're trying to note major milestones and you might want to associate some information with it.
# what if we decide that we're really not supposed to be doing that right now? What if we decide that we really should have started this on a branch, or maybe we need to change content and work on something else for a while?
	Well, we can do that by using Git's stashing ability
		git stash
	If we do a "git stash list", it shows us our stashes.

# Space for reset and reflog

# we're going to specify the name of the folder we wish to use. Type "git clone", space, and then paste in the URL that should still be on our clipboard, space, and then the name of the folder you wish to create
		git clone copied_ssh_url name_of_the_folder
# in order to update the remote references to the origin in hdd like when we change the name of the repository we can use 
		git remote set-url ssh/html_cloning_link
	useful
		git remote show origin
# Imp: if we want to create a new branch on github we need to push to that branch by using -u (tracking parameter)
		git push -u origin name_of_the_branch

# In order to integrate our changes into master, we need to change back to the master branch. we need to use the "checkout" command: 
		git checkout master 
	Once you've switched to the master branch, since we haven't fetched anything recently our local repo doesn't realize that it's actually out of date so I'm just going to do a 
		git pull
	Great, now we've integrated all the changes that have changed on master from our GitHub repository. So, now we're ready to integrate our changes that we have on our local "example_branch" branch. Type
		git merge the_branch_to_merge_in
	which is "example_branch". Using
		git status
	we see that our local master is "ahead of 'origin/master' by 1 commits" So now, let's synchronize our local changes back up to GitHub using 
		git push
	However, we're not done yet; let's go back to our terminal, and we have two things going on. If I do a
		git branch -a
	I can see that I have a "example_branch" branch still laying around. That's the local branch that we started out with, before we pushed it up to GitHub and then later merged it back into master. We also still have that branch on GitHub, or at least the __reference to it__; that's under "remotes/origin/", branch name. So, let's fix both of those things; first thing I'm going to do is delete our branch.
		__git branch -d branch_name__
	but we still have the "example_branch" branch referenced on origin; however, we know that that branch doesn't exist on GitHub, it's just a stale reference. So, we need to update those stale references. And one way to do that is with the "fetch" command. Type
		__git fetch -p__
	the "-p" is the prune option, which means it's going to look for any dead branches and remove those references. Now doing a
		__git branch -a__
	we see that we have master like before, locally,