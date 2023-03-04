# Linux_again
- **Shell**: command line interpreter<br>
- Commands are **case-sensitive** -> date ≠ Date
### **Structure**:

    commandName + option + input
  
### **Shortcut**:
clear **OR** Ctrl+L: clear screen<br>
Ctrl+Alt+T: Open new terminal

### **Baisc commands**:
**echo**: echo abcd -> abcd<br><br>
**cal**: check calendar<br><br>
**history**: -c -> clear history; -w -> write and make it permanent<br><br>
**!!**: execute last command or **![number]**: execute command [number]<br><br>
**which** [-a] command: locate the command<br><br>
**man** command -> search command in the manual<br>
**Another example**: man "list directory contents"<br><br>
**ls** -lh
+ Some commands are defiend directly in the shell and cannot be found in manual page. For example: **cd** -> **help cd**
+ Standard inputs are connected to the keyboard and standars outputs are connected to the terminal
+ Command line arguments (cal 12 2017): only associated with the cmd ≠ data stream: can be redirected
+ Std input:0, std output:1, std error:2<br>

### **Redirection**:

    cat 1> output.txt -> std output is redirected to output.txt
    '>' truncation -> remove old text and replace with new text
    '>>' -> appending
    cat 2>> error.txt
    '<' -> input redirection
    
**Example**:

    cat < input.txt > output.txt 2> error.txt

Everything in Linux is treated as a file even the terminal

    cat <input.txt >/dev/pts/1
    
**Piping**: Taking std output of 1 command and connecting it to the std input of another command
![Piping](https://github.com/hyhung12/Linux_again/blob/main/piping.PNG)<br>
**Tee**: Allow use to pass the data to another pipe abnd also keep the data in a file<br>
![Tee](https://upload.wikimedia.org/wikipedia/commons/thumb/2/24/Tee.svg/400px-Tee.svg.png)

    cat <input.txt  | tee  output2.txt    >>   output.txt
**xargs**: convert std input into command line argument

    date | echo -> not work
    date | xargs echo -> work
    
**Navigate file system**

    pwd
    ls -F: hightlight folders
    cd . or cd ..

### **Wildcards * ? [] {}**:

    ls * -> list everything in the folders
    ls *.txt -> everything with txt extension
    ?txt -> everything ends with txt but have only 1 space before it
    
Everything in the square bracket

    output[1234].txt || output[1-9].txt || output[1-9][1-9][a-z].txt

### **Creating Files  Folders**

    touch file1 -> Creating at current directory
    touch Documents/file1 -> Creating at different directory
    
**mkdir** for folders

    mkdir -p fd1/fd2/fd3/... : to create folders even if previous fds do not exist
    
**Brace expansion**:

    mkdir {jan,feb,mar,apr}_{2017..2019}
    touch {jan,feb,mar,apr}_{2017..2019}/file{1..100}
    ls {jan,feb,mar,apr}_{2017..2019}
    
### **Deleting Files Folders**

    rm deleteme -> Deleting at current directory
    rm Documents/deleteme -> Deleting at different directory
    rm -r delfolder -> Delete parent and child folder
    rm -ri delfolder -> ask when deleting folders
    rm delfolder* -> delete only empty folders

