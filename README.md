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
> Linux **_ls -a command_**, show all files and subdirectories in the current directory, including hidden files and **_ls -l command_**, display detailed information of non-hidden files and directories
#### Then I go to the 00_welcome folder, where there's a README.md file in which the first password is stored
```
cd 00_welcome/
```
```
cat README.md
```
## *LEVEL 1*
#### The file containing the level 1 solution is hidden in one of the many subfolders in the **_01_choice_tree_** directory. I used these commands to access it:
```
cd /home/level/01_choice_tree/
```
```
ls -al
```
```
cd ......
```
#### After rummaging through the folders using cd, cat and ls I found the file containing the password in the folder named **_patience_** which is a sub-subfolder of **_blue_** and display the file contents with :
```
cat SOLUTION.txt
```
## *LEVEL 2*
#### To find the password for this level, you need to explore the hidden folders and files.
> here's how I got here.
```
cd /home/.porb/
```
> The **dot** means it's a hidden folder/file
#### And this is how i recovered the password, which is in a **_.porb_** file :
```
cat .solution
```
## *LEVEL 3*
#### For this level I just need to go to folder **_03_** to find the solution, which is located in the file called  **_.bash_history_**
> As for the last level, I use the same commands to move around a folder, to find out what the folder contains and to read the contents of a file.
```
cd /home/level/03/
```
```
cat .bash_history
```
## *LEVEL 4*
#### Here, when you enter the **_04_kwisatz_** folder, you only see one file that says "Look in your ~".
> The **~** in linux designates the personal directory
#### I then find another file with a password named README2.md, using an absolute path like this :
```
cd /home/user/username/level/04_kwisatz/
```
#### I use the **_cat_** command to read its contents 
## *LEVEL 5*
> The last password to be found to validate **"Beginning"** is the one from this level 5. 
#### So I enter into the **_05_privacy_** directory and the only file it contains is where the password is located
```
cd 05_privacy/
```
```
cat README.md
```
### To sum up, for this challenge we mainly used basic commands to be able to move in folders at different stages, to look at what they contain, even if it's hidden, and to read the contents of a file.
