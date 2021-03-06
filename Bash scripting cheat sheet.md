# Bash Scripting
![Bash scripting image](https://www.osetc.com/en/wp-content/uploads/2019/04/list-and-set-shell-variable1.gif)
## How to Find Which Shell You Are Using on Linux ?
1. **ps -p $$**
  * The special shell parameter $$. “$$” indicates the process id of the current instance of the shell you are running.
2. **echo $0**
  * $0 can be the name of the shell or the name of shell script.
3. **pstree $$**
  * The pstree command shows the process tree.
4. **cat /proc/$$/cmdline**
  * The proc directory contains the runtime system information about your Linux system.

## The SheBang line at the beginning of shell script.
* **#! /bin/bash** : This line tells the interpreter that your script is written for bash shell.

## Adding your shell script to the PATH
* export PATH=$PATH:[_script path_] : this step makes your script run from any directory without using "**./**"

## Variables
* **myvar=3**  note : there is no space around the equal operator.
* **readonly PI=3.14** : this will create a constant variable which makes error if you try to change its value.
* **echo "myvar values is _$myvar_"** : variable substitution.
* **read myvar** : To assign the variable to STDIN.

## Command substitutions
* **DATE=$(date)** : will pass the date command to the shell then takes the ouput from the STDOUT and assign it to the variable DATE.
* **DATE=\`date\`** : The back ticks is the same as $(command), but it's an old style.
## Passing arguments to a bash shell script
* **no_lines=$(wc -l < $1)** : This line will take the first argument passed to the script and find the number of lines in it.
* **find / -iname $1 2> /dev/null** : this command will search for the name passed as argument and direct the stream 2 to the /dev/null file.
## Special variables in Bash shell
* **$0** : the name of the bash script.
* **$1,$2,$3,...**: The first,second,third,... argument passed to the script.
* **$#** : The number of arguments passed to the script.
* **$@** : The values of all arguments passed to the script.
* **$$** : The process id of the current shell.
* **$?** : The exit status of the last executed command.
* **$!** : The process id of the last executed command.
## Arrays in Bash shell
* myarray=(val1 val2 val3) : declaring array.
* echo ${myarray[2]} indexing of an arrays.
* echo ${myarray[\*]}  : print the whole array.
* echo ${#myarray[@]} : print the number of elements in the array.
* myarray+=(val4) : append an element to the array.
* unset mrarray[2] : drop the third element in the array.
* unset myarray : delete the array.
## Arithmatic operations
* $((arithmatic operation)) : To make any calculations.
* **_Example_**
  * filesize1=$(du -b $1 | cut -f1)  :  du command stands for _disk usage_ which means it calculates the size on disk used by a files.
  * filesize2=$(du -b $2 | cut -f1)
  * totalsize=$(filesize1+filesize2)
* $(5/2) : it prints 2 not 2.5
* echo "5/2" | bc -l : The bc command with -l option -which includes the math library- prints the floating point.
* var=$(echo "scale=2;10/4" | bc -l) : Scale is used to dispaly the output in two decimal points
## String Operations in Bash
* **${#string}** : Get string length
* **string3=$string1$string2** : Concatenating two strings
* **expr index "$string3" "$string2"** : find the index of the first match from string2 in string3
* **${string:start_index:length}** : Extract substrings from a string.
  * ${string:start_index} : Extract the substring starting from the index to the end of the string.
  * ${string::length} : Extract the substring starting from the index 0 and with the specified length.
* **${string/old_char/new_char}** : Replace the first occurence of the old_char by the new_char.
  * ${string//old_char/new_char} : Replace every old_char by the new_char.
  * ${string//old_char} : Remove all the old_char from the string.
* **${string^^}** : Capitalize all the characters of the string.
  * ${string^} : Capitalize the first character of the string.
  * ${string^^[abc...]} : Capitalize specified characters from the string.
* **${string,,}** : lowercase all the characters of the string.
  * ${string,} : lowercase the first character of the string.
  * ${string,,[abc...]} : lowercase specified characters from the string.
## Decision Making in Bash
### if statement in bash
* **if [ condition ]; then  
     body1  
    elif [ condition ]; then  
     body2  
    else  
     body3  
    fi**
### case statement in bash
* **case "variable" in  
	     "pattern1" )  
		  Command … ;;  
	     "pattern2" )  
		  Command … ;;  
	     "pattern2" )  
		  Command … ;;  
    esac**
## Get all the test conditions in Bash
* **man test** : man page contains the test conditions.
  * -z $STRING1 :	$STRING1 is empty or null. (**empty string : *string1=""* , null string : *string1***)
  * -n $STRING1	$STRING1 is not empty.
## Loops in Bash
### For loop
* **for ((initialize ; condition ; increment)); do  
	[COMMANDS]  
     done**  
     
* **for item in [LIST]; do  
	[COMMANDS]  
    done**  
    
  * for i in {1..10} : a counter from 1 to 10
  * for i in /Desktop/* : to loop on all files and directories
### While loops
* **while [ condition ]; do  
	[COMMANDS]  
    done**    
### Until loops
* **until [ condition ]; do  
    	[commands]  
    done**  

## Functions in Bash
* **function *function_name* ()  
    {  
    	[Function Body]  
    }**  
  
* **function_name ()  
     {  
     	[funciton body]
     }**
* In bash, functions don't return values but we can return a number as exit status then we read it by $?. (walk around)
* **varA=1  
    varB=2  
    function_name ()    
     {  
     	local varA=5  #This will not overwrite the global variable  
	varB=5        #This will overwrite the global variable  
     }**    
