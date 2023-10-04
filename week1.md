# CSE15L Week 1 Lab Report - Remote Access and FileSystem 

# cd command
The cd command stands for "current directory" and it is used to move between directories.
## cd no arguments
![Image](cdnoarguments.PNG)

Using cd with no arguments resets the current directory to the home directory, also known as /home. I was in the ~/lecture1/messages directory, using cd reset me to home.
This is **not** an error and is an intentional/useful way for easy access to the home directory.

## cd to a directory
![Image](cdtodirectory.PNG)

Using cd with directory as an argument is used to change and move inbetween directories. This allows easy access to the files in the directory.
This is **not** an error and allows movement between directories.

## cd to a file
![Image](cdtofile.PNG)

Using cd with a file as an argument is an **error**. This is because a file is not a directory and so the command "change directory" will not work. 
A directory basically has multiple files in it and a single file can not be a directory. 

# ls command
This lists the files in the directory.

## ls no arguments
Using ls with no arguments gives the list of files that is in the current directory you are in.

## ls to directory
Using ls with a directory gives the list of files of the specified directory. If the specified directory doesn't exist it will cause an error. 

## ls to a file
Using ls on a file just displays the mentioned filename. If the file doesn't exist in the current directory it will cause an error.

#
