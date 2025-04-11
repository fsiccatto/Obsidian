# CD (change directory)
- . (current directory). This is the directory you are currently in.
- .. (parent directory). Takes you to the directory above your current.
- ~ (home directory). This directory defaults to your “home directory”. Such as /home/pete.
-  - (previous directory). This will take you to the previous directory you were just at.
# LS (list directions)
list directory contents. The ls command will list directories and files in the current directory by default, however you can specify which path you want to list the directories of.
- -a flag to see files which are not visible
- -l long format list
- -la both flags
# TOUCH
Touch allows you to the create new empty files.
`touch mysuperduperfile`
# FILE
To find out what kind of file a file is, you can use the file command. It will show you a description of the file’s contents. In linux, filenames aren't requiered to represent the contents of the file
`file asf.jpg`
# CAT
It not only displays file contents but it can combine multiple files and show you the output of them.
`cat dogfile birdfile`
It's recommend for short files
# LESS
The text is displayed in a paged manner, so you can navigate through a text file page by page.
`$ less /home/pete/Documents/text1`
Use the following command to navigate through less:
- q - Used to quit out of less and go back to your shell.
- Page up, Page down, Up and Down - Navigate using the arrow keys and page keys.
- g - Moves to beginning of the text file.
- G - Moves to the end of the text file.
- /search - You can search for specific text inside the text document. Prefacing the words you want to search with /
- h - If you need a little help about how to use less while you’re in less, use help
# HISTORY
With history we can see all the commands that we previously entered.
With clear we clear up our display
# CP (copy)
Let’s start making some copies of these files. Much like copy and pasting files in other operating systems, the shell gives us an even simpler way of doing that.
`$ cp mycoolfile /home/pete/Documents/cooldocs`
mycoolfile is the file you want to copy and /home/pete/Documents/cooldocs is where you are copying the file to.
You can copy multiple files and directories as well as use wildcards. A wildcard is a character that can be substituted for a pattern based selection, giving you more flexibility with searches. You can use wildcards in every command for more flexibility.
- * the wildcard of wildcards, it's used to represent all single characters or any string.
- ? used to represent one character
- [] used to represent any character within the brackets
`$ cp *.jpg /home/pete/Pictures`
This will copy all files with the .jpg extension in your current directory to the Pictures directory.
-r flag, this will recursively copy the files and directories within a directory.
`$ cp -r Pumpkin/ /home/pete/Documents`
You can use the -i flag (interactive) to prompt you before overwriting a file.
`$ cp -i mycoolfile /home/pete/Pictures`
# MV (move)
Used for moving files and also renaming them. Quite similar to the cp command in terms of flags and functionality.
You can rename files like this:
`$ mv oldfile newfile`

Or you can actually move a file to a different directory:
`$ mv file2 /home/pete/Documents`

And move more than one file:
`$ mv file_1 file_2 /somedirectory`

You can rename directories as well:
`$ mv directory1 directory2`

Like `cp`, if you `mv` a file or directory it will overwrite anything in the same directory. So you can use the `-i` flag to prompt you before overwriting anything.
`mv -i directory1 directory2`

Let’s say you did want to `mv` a file to overwrite the previous one. You can also make a backup of that file and it will just rename the old version with a `~`.
`$ mv -b directory1 directory2`
# MKDIR (make directory)
The mkdir command (Make Directory) will create a directory if it doesn’t already exist. You can even make multiple directories at the same time.
`$ mkdir books paintings`
You can also create subdirectories at the same time with the -p (parent flag).
`$ mkdir -p books/hemmingway/favorites`
# RM (remove)
To remove files you can use the rm command. The rm (remove) command is used to delete files and directories.
`$ rm file1`
Take caution when using rm, there is no magical trash can that you can fish out removed files. Once they are gone, they are gone for good, so **be careful**.
You can absolutely remove a bunch of files.

`$ rm -f file1`
-f or force option tells rm to remove all files, whether they are write protected or not, without prompting the user (as long as you have the appropriate permissions).

`$ rm -i file`
Adding the -i flag like many of the other commands, will give you a **prompt** on whether you want to actually remove the files or directories.

`$ rm -r directory`
You can’t just rm a directory by default, you’ll need to add the -r flag (recursive) to remove all the files and any subdirectories it may have.

You can remove a directory with the rmdir command.
`$ rmdir directory`
# FIND
A command for find a file
`$ find /home -name puppies.jpg`
With find you’ll have to specify the directory you’ll be searching it, what you’re searching for, in this case we are trying to find a file by the name of puppies.jpg.

You can specify what type of file you are trying to find.
`$ find /home -type d -name MyFolder`
You can see that I set the type of file I’m trying to find as (d) for directory and I’m still searching by the name of MyFolder.

One cool thing to note is that find doesn’t stop at the directory you are searching, it will look inside any subdirectories that directory may have as well.
# HELP
help, is a built-in bash command that provides help for other bash commands (echo, logout, pwd, etc).
`$ help echo
This will give you a description and the options you can use when you want to run echo. For other executable programs, it’s convention to have an option called --help or something similar.

`$ echo --help`
Not all developers who ship out executables will conform to this standard, but it’s probably your best shot to find some help on a program.
#