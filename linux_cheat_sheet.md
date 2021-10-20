## Getting Help
* **man command** : displays the manual page for the command.
  * /key word : to search the man page.
  * man -f command = whatis command :  It displays man pages that match, or partially match, a specific name and provide the section number.
  * man _**sec_number**_ command : display the man page that located at the section with that number.
  * man -k _**key_word**_ : searches both the names and descriptions of the man pages for a keyword. 
* **whereis command**  : search for the location of a command or the man pages for a command.
* **locate file/dir**  : searches a database of all files and directories that were on the system when the database was created.
  * locate -c file/dir : how many files match.
  * locate -b file/dir : only includes listings that have the search term in the basename of the filename.
  * locate -b "\file_dir: this character limits the output to filenames that exactly match the term. 
* **info command** : displays documentation for the command in a way different to the man command.
* **command --help** : provides basic information about the command.
## Navigating the Filesystem
* **pwd** : prints the current directory path
* **cd path** : change the current directory.
  * cd ~ : go to the current user directory (/home/usrname)
  * cd ..: got back one step in the path
  * cd . : the current directory.
* **ls [OPTION]... [FILE]...**: list the contents of the directory
  * \ls : to avoid using the aliasing for _**ls --color=auto**_
  * ls -a : listing all files including the hidden files.
  * ls -l : use the long list format.
  * ls -h : use the human readable size format
  * ls -l -d : show the information of the current directory without its contents.
  * ls -R : recursive listing.
  * ls -S : sort by file sizes in descending order
  * ls -t : sort by file editing time starting with the most recent file.
## Managing Files and Directories
* **cp [source] [destination]** : copy the source file to the destination directory "only files"
  * cp -v : vorbose option to print output showing the steps of operation
  * cp -i : interactive options asks the user before overwriting
  * cp -n : means no overwrite for all files
  * cp -r : recursive copy means copy the whole directory structure. "copy files and directories"
  * cp sourcefile destination/filename : to give the file a new name
* **mv [source] [destination]** : remove the file from the original location and place it in the destination.
  * Like the cp command, the mv command provides the following options: -v, -i, -n
  * There is no -r option for mv command.
* **touch [filename]** : create a file
* **rm [filename]** : delete a file permanently
  * rm -i : ask before deleting
  * rm -r : delete the directory with all directories and files included
* **mkdir [dir_name]** : create a directory.
* **rmdir [dir_name]** : remove the directory only if it's empty
