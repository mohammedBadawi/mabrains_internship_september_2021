## Getting Help
* **man [command]** : displays the manual page for the command.
  * /key word : to search the man page.
  * man -f [command] = whatis [command] :  It displays man pages that match, or partially match, a specific name and provide the section number.
  * man [_**sec_number**_] [command] : display the man page that located at the section with that number.
  * man -k [_**key_word**]_ : searches both the names and descriptions of the man pages for a keyword. 
* **whereis [command]**   : search for the location of a command or the man pages for a command.
* **locate [file/dir]**   : searches a database of all files and directories that were on the system when the database was created.
  * locate -c [file/dir]  : how many files match.
  * locate -b [file/dir]  : only includes listings that have the search term in the basename of the filename.
  * locate -b ["\file_dir]: this character limits the output to filenames that exactly match the term. 
* **info [command]**   : displays documentation for the command in a way different to the man command.
* **command --help** : provides basic information about the command.
## Navigating the Filesystem
* **pwd** : prints the current directory path
* **cd [path]** : change the current directory.
  * cd ~  : go to the current user directory (/home/usrname)
  * cd .. : got back one step in the path
  * cd .  : the current directory.
* **ls [OPTION]... [FILE]...**: list the contents of the directory
  * \ls      : to avoid using the aliasing for _**ls --color=auto**_
  * ls -a    : listing all files including the hidden files.
  * ls -l    : use the long list format.
  * ls -h    : use the human readable size format
  * ls -l -d : show the information of the current directory without its contents.
  * ls -R    : recursive listing.
  * ls -S    : sort by file sizes in descending order
  * ls -t    : sort by file editing time starting with the most recent file.
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
## Archiving and Compression
* **gzip file / gunzip file**   : compress/decompress the file using  **_Lempel-Ziv-Markov (LZMA)_** algorithm
* **bzip2 file / bunzip2 file** : compress/decompress the file using  **_Burrows-Wheeler_** algorithm (better compression, more cpu time)
* **xz file / unxz file**       : compress/decompress the file using  **_Lempel-Ziv-Markov (LZMA)_** algorithm
* **tar -c [-f ARCHIVE] [OPTIONS] [FILE...]**  : archive files into one file
  * tar -cz [-f ARCHIVE] [OPTIONS] [FILE...]   : compress the resulting file with gizp
  * tar -cj [-f ARCHIVE] [OPTIONS] [FILE...]   : compress the resulting file with bzip2
* **tar -t [-f ARCHIVE] [OPTIONS] [FILE...]**  : list the archived files
* **tar -x [-f ARCHIVE] [OPTIONS] [FILE...]**  : extract the archived files
  * tar -xz [-f ARCHIVE] [OPTIONS] [FILE...]** : extract the archived files after decompressing using gzip
  * tar -xj [-f ARCHIVE] [OPTIONS] [FILE...]** : extract the archived files after decompressing using bzip2
## Working With Text
* **cat [filename]** : view the file in the std output
* **less [filename]** : view the file using the less pager
  * Spacebar : 	Window forward
  * B	       : Window backward
  * Enter    :	Line forward
  * Q        :	Exit
  * H        :	Help 
* **head/tail [filename]** : view the first/last 10 lines from the file in the std output
  * head -5    : view the first lines
  * head -n 5  : view the first 5 lines
  * head -n -5 : view the whole file except the last 5 lines
  * tail -5    : view the last 5 lines
  * tail -n -5 : view the last 5 lines
  * tail -n 5  : view the last 5 lines
  * tail -n +5 : view the file from the line number 5 to the end
* **tail -f [filename]** : view the live file changes , ex: used in viewing the log files
* **standard streams**
  * STDIN  : standard input
  * STDOUT : standard output , stream/channel #1
  * STDERR : standard error  , stream/channel #2
  * echo "hello" > file.txt : redirect the STDOUT stream to the file (overwrite)
  * echo "hello" >> file.txt : redirect the STDOUT stream to the file and overwrite (append)
  * ls /ABC 2> file.txt     : redirect the STDERR stream to the file
  * ls /fake /etc/ppp &> all.txt : &> is used to direct both stream 1&2 to the file
  * ls /etc /fake > output.txt 2> error.txt : direct the stream 1 to output.txt and stream 2 to error.txt
  * tr 'a-z' 'A-Z' : tar command is used to translat a set of characters to another set of characters. In this case it's used to capitaize the word input from the STDIN.
* **sort [file]** : sort the lines of the file in alphabetical order.
  * sort -t: -k3 -n file.txt : -t: defines the field delimiter which is now : , -k3 means sort by the 3rd field , -n means numerical sort
  * sort -t, -k2 -k1n -k3 -r file.txt : defines the delimiter as ',' and sort by the 2nd field then the first field numerically then the third field and use reverse order for sorting.
* **wc file.txt** : count the number of lines,words and bytes.
  * wc -l : count the lines only
  * wc -w : count the words only
  * wc -c : count the bytes (characters) only
* **cut -d[delimiter] -f[columns numbers] [file name]** : extract the columns from the file using the defined delimiter
  * cut -d: -f1,5-7 mypasswd : extract columns number 1,5,6,7 from the mypasswd file using ':' as delimiter
* **cut -c[characters numbers] [file name]** : extract the columns of the defined characters from the file
  * ls -l | cut -c1-11,50- : pipline the output of the ls command to the cut command to extract the columns of the first 11 characters and from 50 to the end.
* **grep [text] [file]** : find the linein the specified file that contain the specified text.
  * grep -c [text] [file] : prints the number of lines that contain the specified text.
  * grep -v [text] [file] : finds the lines that don't contain the specefied text.
  * grep -n [text] [file] : adds the lines numbering.
  * grep -i [text] [file] : ignores the case (capitalization) distinctions.
  * grep -w [text] [file] : only returns lines which contain matches that form whole words.
