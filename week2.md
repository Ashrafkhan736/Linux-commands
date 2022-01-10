# Table of content

- [ls command](#ls)
- [Commands used for reading text file](#less)
- [Commands used to get information about other commands](#helpers)
- [Alias command](#alias)
- [commands used to get info about file size](#size)
- [Shell variable and echo command](#variables)

## ls

>**ls -l** command list information about file present in current working directory.
>
>Here d means directory and - means normal binary file that can be read.
>
>>```bash
>>$ls -l
>>
>>total 2732
>>drwxrwxr-x 2 ashraf ashraf    4096 Dec 18 19:45  BDM
>>-rwxr----- 1 ashraf ashraf 2646559 Oct  7 11:25 'BDM W1 - W4 Notes.pdf'
>>-rwxr----- 1 ashraf ashraf    1004 Dec 28 15:37  count_k.py
>>drwxrwxr-x 4 ashraf ashraf    4096 Dec 18 19:45  DBMS
>>drwxrwxr-x 4 ashraf ashraf    4096 Jan  4 12:31  DSA_with_python
>>drwxrwxr-x 2 ashraf ashraf    4096 Dec 18 19:48  dynamic_progamming
>>-rwxr----- 1 ashraf ashraf     520 Jun 21  2021  long_prefix.py
>>drwxrwxr-x 3 ashraf ashraf    4096 Jan  1 12:09  MAD1
>>```
>
>**ls -ld** list information about the directory given as arragument.
>
>>```bash
>>$ls -ld DSA_with_python
>>drwxrwxr-x 4 ashraf ashraf 4096 Jan  4 12:31 DSA_with_python
>>```

## less
>
>- **less**
>
>>It gives the output of the file in page by page format.
>
>- **more**
>
>>It is same as less command.
>
>- **cat**
>
>>It concatanate the  content of the text to the terminal window (just dump the content on the screen).
>
>- **head**
>>
>>By default it dumps the first 10 lines of the content on screen.
>>
>>By using -n option we can select the number of line. Example:
>>
>>```bash
>>$head -n 5 file.txt
>>```
>>
>>This gives first 5 lines of content.
>
>- **tail**
>>
>>It dumps the last 10 lines of the content of text file on screen. It is similar to head command.
>
>- **wc**
>
>>It gives the info of a file like how many line, word and size it has.
>>
>>```bash
>>$wc 'BDM W1 - W4 Notes.pdf' 
>>11727   59804 2646559 BDM W1 - W4 Notes.pdf
>>$wc -l 'BDM W1 - W4 Notes.pdf'
>>11127
>>```
>>
>>This says file has 11727 lines, 59804 words and 2646559 byte is the size of a file.
>>
## helpers
>
>- **apropos**
>>
>>It shows the list of commands matching with the given arrugment.
>>
>- **man**
>>
>>It gives the manual pages for the command given as arrgument.
>>
>- **which**
>>
>>It gives the location where command/file/packages are located.
>>
>- **whatis**
>>
>>It gives the short info about any command/file/packages.
>>
>- **info**
>>
>>It is used without any option/arrgument.
>>
>>It shows the manual pages of all the command in GUI form.
>>
>```bash
>$apropos who 
>bsd-from (1)         - print names of those who have sent mail
>from (1)             - print names of those who have sent mail
>w (1)                - Show who is logged on and what they are doing.
>w.procps (1)         - Show who is logged on and what they are doing.
>who (1)              - show who is logged on
>whoami (1)           - print effective userid
>$whatis who 
>who (1)              - show who is logged on
>$whatis python
>python3 (1)          - an interpreted, interactive, object-oriented programming language
>$which python
>/home/ashraf/anaconda3/bin/python
>$man -k who
>bsd-from (1)         - print names of those who have sent mail
>from (1)             - print names of those who have sent mail
>w (1)                - Show who is logged on and what they are doing.
>w.procps (1)         - Show who is logged on and what they are doing.
>who (1)              - show who is logged on
>whoami (1)           - print effective userid
>$which apropos 
>/usr/bin/apropos
>$which whatis
>/usr/bin/whatis
>$ls -l /usr/bin/apropos 
>lrwxrwxrwx 1 root root 6 Dec 21 12:43 /usr/bin/apropos -> whatis
>$type type
>type is a shell builtin
>```

## alias

>alias helps in creating short commannds by combaining default commands with some useful options.
>
>Just by typing alias you can see the pre existing aliases.
>
>unalias command remove the alias.
>
>I suggest using -i option with cp,mv and rm to get confurmation prompt from shell for every operation.
>
>Examples:
>
>```bash
>$alias
>alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
>alias egrep='egrep --color=auto'
>alias fgrep='fgrep --color=auto'
>alias grep='grep --color=auto'
>alias l='ls -CF'
>alias la='ls -A'
>alias ll='ls -alF'
>alias ls='ls --color=auto'
>
>$alias rm='rm -i'
>
>$unalias rm
>
>$alias ll
>alias ll='ls -alF'
>```

## size
>
>- ls -s command list file with it's size and -h can be use to get human readable output.
>
>- stat and du command also gives the file size info.
>
>```bash
>$ls -sh "BDM W1 - W4 Notes.pdf" 
>2.6M 'BDM W1 - W4 Notes.pdf'
>
>$stat "BDM W1 - W4 Notes.pdf"
>  File: BDM W1 - W4 Notes.pdf
>  Size: 2646559    Blocks: 5176       IO Block: 4096   regular file
>Device: 802h/2050d Inode: 18089569    Links: 1
>Access: (0740/-rwxr-----)  Uid: ( 1000/  ashraf)   Gid: ( 1000/  ashraf)
>Access: 2022-01-04 18:17:34.064217119 +0530
>Modify: 2021-10-07 11:25:39.000000000 +0530
>Change: 2021-12-24 11:17:14.965959450 +0530
> Birth: -
>
>$du "BDM W1 - W4 Notes.pdf"
>2588 BDM W1 - W4 Notes.pdf
>
>$du -h "BDM W1 - W4 Notes.pdf"
>2.6M BDM W1 - W4 Notes.pdf
>```

## variables

- **echo** It works same as print function in python

- **printenv** or **env** gives enviroment variable/shell variable.

- **set** gives function and enviroment variable/shell variable.

- **ps -ef** gives list of process that are running with their process id.

```bash
(base) ashraf@320:~$ echo hello world
hello world
(base) ashraf@320:~$ echo hello             world
hello world
(base) ashraf@320:~$ echo 'Hello              world'
Hello              world
(base) ashraf@320:~$ echo "Hello world'
> some 
> close single quote'
> close double quote"
Hello world'
some 
close single quote'
close double quote
(base) ashraf@320:~$ echo $PATH
/home/ashraf/anaconda3/bin:/home/ashraf/anaconda3/condabin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
(base) ashraf@320:~$ echo '$PATH'
$PATH
(base) ashraf@320:~$ echo "$PATH"
/home/ashraf/anaconda3/bin:/home/ashraf/anaconda3/condabin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
(base) ashraf@320:~$ echo "\$PATH"
$PATH
```
