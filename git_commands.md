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
than we can create our working directory folder by using 
		git init folder_name
# it will create a folder with .git folder inside which is where our repository is located

# than we can make files in the working directory by using 
		default_editor_name file_name.extension
->this will create and open the file in the default editor.

# We can add this file in repo by using
		git add filename.extention
		git add .a(this adds all the files in working dir)

# now the file is created but not commited yet which is staging area, we can commit the file by using 
		git commit -m 'commit_name'
# We can check status of working directory by using
		git status	
# We can delete our local repository recursively by using 
		rm -rf .git



			