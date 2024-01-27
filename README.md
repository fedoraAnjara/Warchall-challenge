# Warchall-challenge
#
> To start with, I create an SSH account and then connect to the account I've just created by using a terminal.
## 1. The Beginning
### For this level we are asked to search for 6 hidden passwords (level 0-5) in various files
## *LEVEL 0*
#### At the very beginning, I display the contents of the WELCOME.md file with the command :
```
cat WELCOME.md
```
>  **_cat command_** lets you view the contents of a file

#### In this file they welcome me and tell me that I will find the solutions in the level directory. So I go there by typing :
```
cd /home/level/
```
#### Now I'm running a command to list existing files:
```
ls -al
```
> Linux **_ls -A command_**, show all files and subdirectories in the current directory, including hidden files and **_ls -l command_**, display detailed information of non-hidden files and directories
#### Then I go to the 00_welcome folder, where there's a README.md file in which the first password is stored
```
cd 00_welcome/
```
```
cat README.md
```
## *LEVEL 1*
#### The file containing the level 1 solution is hidden in one of the many subfolders in the 01_choice_tree directory. I used these commands to access it:
```
cd /home/level/01_choice_tree/
```
```
ls -al
```
```
cd ......
```
#### After rummaging through the folders using cd, cat and ls I found the file containing the password in the folder named patience which is a sub-subfolder of blue and display the file contents with :
```
cat SOLUTION.txt
```
