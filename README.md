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

### **Creating Files/Folders**

    touch file1 -> Creating at current directory
    touch Documents/file1 -> Creating at different directory
    
**mkdir** for folders

    mkdir -p fd1/fd2/fd3/... : to create folders even if previous fds do not exist
    
**Brace expansion**:

    mkdir {jan,feb,mar,apr}_{2017..2019}
    touch {jan,feb,mar,apr}_{2017..2019}/file{1..100}
    ls {jan,feb,mar,apr}_{2017..2019}
    
### **Deleting Files/Folders**

    rm deleteme -> Deleting at current directory
    rm Documents/deleteme -> Deleting at different directory
    rm -r delfolder -> Delete parent and child folder
    rm -ri delfolder -> ask when deleting folders
    rm delfolder/* -> delete only empty folders

### **Copying Files/Folders**

    cp old_file new_file -> Copy & paste file
    cp -r old_fd new_fd -> Copy & paste folder
    cp file1 file2 Documents/ -> Copy & paste files to different directory
    cp Documents/* . -> Copy everything in 1 folder to current directory
    
### **Removing + Renaming Files/Folders** (does not require -r)

    mv old_name.txt new_name.txt || mv old_fd new_fd
    mv folder1/* newFolder ||  mv folder1/* .   -> Move everything in folder 1 to new folder
    mv folder1 ~/Desktop/folder   -> Move and rename folder
    
### **Find command**: List all files and folders but can be very slow(does not search from database ≠ locate)
 
 **Search by depth**
 
    find . -maxdepth 1 -> Display everything in current diretory
    find . -maxdepth 2 -> One level down
    
**Search by name and type**

    find . -type f -> Only show files | -type d -> Only folders
    find . -name "5.txt" -> search all locations that have the wanted file (wildcards work but not brace expansion)
    find . -iname -> ignore case-sensitive
    
**Search by size**
 
    find . -size +100k
    find . -size +100k -o -size -5M (
    find . -size +100k | wc -l -> count number of lines
    
### **cat command**

    cat file[1-5].txt > output.txt  -> Stick files together

### **Viewing commands**

    tac file1.txt -> read content reversely
    rev, head, tail, less
    
### **Archive**
Tarball – a bag containing all files and it can be compressed using compression algorithm

    tar -cvf (create, verbose: give feedback, f: accept files) ourarchive.tar file1.txt file2.txt
    tar -tf archive.tar (test label: check inside tarball, -f is needed for file) 
    tar -xvf (-x to extract tarball, extract does not delete the tarball, tarball is like a reused bag)

### **Compress**

    gzip: faster but lest compression power
    bzip2: compress smaller file but requires more power (only good for large files like img, video)
    bzip2 / Gzip ourarchive.tar to compress tarbal
    bunzip2 / Gunzip ourarchive.tar.gz to get back tarball file

### **Zip/Archive + Compress in 1 command**

    zip ourzipfile.zip file[1..4].txt -> zip does archive and compression in 1 step
    tar -cvzf ourarchive.tar.gz file[1..4].txt  -> Archive + compression in 1 step
    tar -xvzf ourarchive.tar.gz  -> Extract gzip file to tarball

### **Apt: Advanced package tool**

    apt-cache search “search term” ->  search for related packages
    apt-cache show package_name | less -> search info about package

### **Update + upgrade packages**

    sudo apt-get update -> download the most updated version of the package list
    sudo apt-get upgrade -> upgrade all the packages to the newest version
    
### **Install new package**

    sudo apt-get install package_name
    
### **Remove package**

    sudo apt-get remove package_name -> don’t do this, it will leave config file in the system
    sudo apt-get purge package_name -> remove package + config file
    sudo apt-get autoremove -> remove unwanted dependencies
    cd /var/cache/apt/archives
    sudo apt-get clean -> remove all archives of packages
    sudo apt-get autoclean -> delete packages archives no longer accessible

