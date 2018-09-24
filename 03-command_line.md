# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

> > pwd - show current working directory path
> > mkdir [name] - create directory with name [name]
> > rmdir [name] - delete directory named [name]
> > touch [name] - create a file named [name]
> > rm [name] - delete file named [name] 
> > mv [name1] [name2] - rename a file from [name1] to [name2]
> > ls -a - list hidden files (ie files with . in front of them)
> > cp [name1] [name2] - copy file from location [name1] to location [name2]
> > cat - display contents of a file
> > head/tail - display first / last ten lines of a file

---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls`  
`ls -a`  
`ls -l`  
`ls -lh`  
`ls -lah`  
`ls -t`  
`ls -Glp`  

> > ls - lists the contents of a directory
> > ls -a - lists hidden files in a directory (ie files with . in front of filename)
> > ls -l - display the long format listing of a file
> > ls -lh - display long format listing in human readable format
> > ls -lah - list the long format listing of hidden files in human readable format
> > ls -t - list the contents of a directory sorted by time
> > ls -Glp - inhibit grouping of files, use long listing format, append file indicator to entries 
---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

> > ls -r - display files in reverse order
> > ls -R - display subdirectories as well
> > ls -u - display files by file access time
> > ls -d - display only directories
> > ls -m - display entries as comma separated list

---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

> > xargs reads in data from stdin and passes it as an argument to a function.  The function is supplied when xargs is executed as an argument to xargs.  If no function is specified for xargs, it executes the function 'echo' on the stdin.  

> > Example of use: to find all the files in a current directory and its subdirectories, put find and its option -name as an argument to xargs; when stdin is prompted, type in "*.txt", and "*.txt" will be passed as an argument to find -name. 

'''bash
xargs find -name
"*.txt"
'''
