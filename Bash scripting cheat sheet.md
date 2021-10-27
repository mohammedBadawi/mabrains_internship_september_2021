# Bash Scripting
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
