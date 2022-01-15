# Week 3

## How to run multiple command in same line.

- Using semicolon (**`;`**) in between the command we can run multiple commands.

```bash
(base) ashraf@320:~$ cd ; ls ; wc -l /etc/profile
anaconda3  Anime  Bsc_prog  Desktop  Documents  Downloads  Music  Pictures  Public  snap  temp  Templates  Videos
27 /etc/profile
```

- Another way to run multiple commands in same line is to excute commands in sub shells means child shells.
Using parentheses **`()`** we can lauch sub-shells with in the cureent shells.

```bash
# $BASH_SUBSHELL store the level of shell
(base) ashraf@320:~$ echo $BASH_SUBSHELL 
0
(base) ashraf@320:~$ (echo $BASH_SUBSHELL)
1
# we ran the ls,date and echo command in chile sub-shell
(base) ashraf@320:~$ (ls;date;echo $BASH_SUBSHELL)
anaconda3  Anime  Bsc_prog  Desktop  Documents  Downloads  Music  Pictures  Public  snap  temp  Templates  Videos
Saturday 15 January 2022 06:18:52 PM IST
1
# Here ls command is run on first child shell and echo is run on second child shell
(base) ashraf@320:~$ (ls ; (echo $BASH_SUBSHELL ))
anaconda3  Anime  Bsc_prog  Desktop  Documents  Downloads  Music  Pictures  Public  snap  temp  Templates  Videos
2
# More example here we ran the echo in third child shell
(base) ashraf@320:~$ (((echo $BASH_SUBSHELL ););)
3
```

***

## Logical operations based on output of the commands

- **`&&`** operator behave same as AND logic. Here next command will execte only if previous command ran sucessfully.

- **`||`** operator behave same as OR logic. Here next command will execte only if previous command did not run sucessfully.

```bash
(base) ashraf@320:~$ ls && date
anaconda3  Anime  Bsc_prog  Desktop  Documents  Downloads  Music  Pictures  Public  snap  temp  Templates  Videos
Saturday 15 January 2022 06:39:06 PM IST
(base) ashraf@320:~$ ls /blah && date
ls: cannot access '/blah': No such file or directory
(base) ashraf@320:~$ ls || date 
anaconda3  Anime  Bsc_prog  Desktop  Documents  Downloads  Music  Pictures  Public  snap  temp  Templates  Videos
(base) ashraf@320:~$ ls /blah || date
ls: cannot access '/blah': No such file or directory
Saturday 15 January 2022 06:39:51 PM IST
```

***

## File redirection

- Here we can see the default behaviour of command. How it takes output and gives input.
![default case](./images/default.png)

- We can change `1` pointer using **`>`** or **`>>`** operator. `>` store the output in the file and delete the previous content present in it. But `>>` append the output in the file at the end starting from new line without deleting the previous content. If file does not exist then it will be created freshly for the operator.

```bash
(base) ashraf@320:~$ touch file
(base) ashraf@320:~$ echo "first line" > file
(base) ashraf@320:~$ cat file 
first line
(base) ashraf@320:~$ echo "second line" > file
(base) ashraf@320:~$ cat file 
second line
(base) ashraf@320:~$ rm file 
(base) ashraf@320:~$ echo "first line" > file
(base) ashraf@320:~$ echo "second line" >> file
(base) ashraf@320:~$ cat file 
first line
second line
```

- **`2>`** operator redirect the `2` pointer means stderr to the file. Using this we can store the error in the file. We can also combine `>` and `2>` on same line.

```bash
(base) ashraf@320:~$ ls /blah Desktop/ > file1 2> file
(base) ashraf@320:~$ cat file1
Desktop/:
(base) ashraf@320:~$ cat file
ls: cannot access '/blah': No such file or directory
```

***

## Writing txt in the file using cat command

```bash
# we can also type txt in the file using cat  command on the terminal
(base) ashraf@320:~$ cat > file
first
second 
use ctrl +d to get out of the command
(base) ashraf@320:~$ cat file
first
second 
use ctrl +d to get out of the command
# using >> we can append the txt in to file
(base) ashraf@320:~$ cat >> file
third 
fourth
(base) ashraf@320:~$ cat file
first
second 
use ctrl +d to get out of the command
third
fourth
(base) ashraf@320:~$ cat 
Hi
Hi
hjhkjj
hjhkjj
```
***
