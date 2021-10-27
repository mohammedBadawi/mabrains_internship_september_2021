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
* **DATE=`date`** : The back ticks is the same as $(command), but it's an old style.
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
