# Linux_again
**Shell**: command line interpreter<br>
Commands are **case-sensitive** -> date ≠ Date
### Structure:

    commandName + option + input
  
### Shortcut:
clear or Ctrl+L: clear screen
Ctrl+Alt+T: Open new terminal

### Baisc commands:
**echo**: echo abcd -> abcd<br><br>
**cal**: check calendar<br><br>
**history**: -c -> clear history; -w -> write and make it permanent<br><br>
**!!**: execute last command or **![number]**: execute command [number]<br><br>
**which** [-a] command: locate the command<br><br>
man command -> search command in the manual
man "list directory contents"<br><br>
**ls** -lh
+ Some commands are defiend directly in the shell and cannot be found in manual page. For example: **cd** -> **help cd**
+ Standard inputs are connected to the keyboard and standars outputs are connected to the terminal
+ Command line arguments (cal 12 2017): only associated with the cmd ≠ data stream: can be redirected
+ Std input:0, std output:1, std error:2<br>

**Redirection**<br>
cat 1> output.txt : std output is redirected to output.txt<br><br>
'>' truncation: remove old text and replace with new text<br><br>
'>>' appending<br><br>
cat 2>> error.txt
'<': input redirection
**Example**: cat < input.txt > output.txt 2> error.txt

    Everything in Linux is treated as a file even the terminal
    cat <input.txt >/dev/pts/1
**Piping**<br>
Taking std output of 1 command and connecting it to the std input of another command

**Tee**: Allow use to pass the data to another pipe abnd also keep the data in a file<br>
![Tee](https://upload.wikimedia.org/wikipedia/commons/thumb/2/24/Tee.svg/400px-Tee.svg.png)<br>
cat <input.txt  | tee  output2.txt     >>   output.txt<br>
**xargs**: convert std input into command line argument<br>
date | echo -> not work<br>
date | xargs echo -> work<br>


