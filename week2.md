# Table of content <!-- omit in toc -->

- [ls command](#ls-command)
- [Commands used for reading text file](#commands-used-for-reading-text-file)
- [Commands used to get information about other commands](#commands-used-to-get-information-about-other-commands)
- [Alias command](#alias-command)
- [commands used to get info about file size](#commands-used-to-get-info-about-file-size)
- [Shell variable and echo command](#shell-variable-and-echo-command)
- [Process managment](#process-managment)
- [tips](#tips)
  
## ls command

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

## Commands used for reading text file
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
## Commands used to get information about other commands
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

## Alias command

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

## commands used to get info about file size
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

## Shell variable and echo command
>
>- **echo** It works same as print function in python
>
>- **printenv** or **env** gives enviroment variable/shell variable.
>
>- **set** gives function and enviroment variable/shell variable.
>
>- **ps -ef** gives list of process that are running with their process id.
>
>```bash
>(base) ashraf@320:~$ echo hello world
>hello world
>(base) ashraf@320:~$ echo hello             world
>hello world
>(base) ashraf@320:~$ echo 'Hello              world'
>Hello              world
>(base) ashraf@320:~$ echo "Hello world'
>> some 
>> close single quote'
>> close double quote"
>Hello world'
>some 
>close single quote'
>close double quote
>(base) ashraf@320:~$ echo $PATH
>/home/ashraf/anaconda3/bin:/home/ashraf/anaconda3/condabin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
>(base) ashraf@320:~$ echo '$PATH'
>$PATH
>(base) ashraf@320:~$ echo "$PATH"
>/home/ashraf/anaconda3/bin:/home/ashraf/anaconda3/condabin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
>(base) ashraf@320:~$ echo "\$PATH"
>$PATH
>```
>
>### some sepcial shell variables
>
>- **$0**  return name of shell
>- **$$**  return process ID of the shell
>- **$?**  return code of previously run program
>- **$-**  return flags set in bash shell

## Process managment

- Use of **&** to run a job in the background.

- **fg**  brings the command running in background to foreground.Example

```bash
(base) ashraf@320:~$ sleep 30 &
[1] 10914
# & is used to run sleep command in background. ps command shows that sleep is running.
(base) ashraf@320:~$ ps
    PID TTY          TIME CMD
  10306 pts/0    00:00:00 bash
  10914 pts/0    00:00:00 sleep
  10916 pts/0    00:00:00 ps
# fg is used to bring sleep in to foreground.
(base) ashraf@320:~$ fg
sleep 30
```

- **coproc** helps run a command in backgrond. Example:

```bash
(base) ashraf@320:~$ coproc sleep 10
[1] 10182
#Now sleep command will run for 10 sec in background.
(base) ashraf@320:~$ ps --forest
    PID TTY          TIME CMD
   5086 pts/0    00:00:00 bash
  10182 pts/0    00:00:00  \_ sleep
  10184 pts/0    00:00:00  \_ ps
```

- **jobs**  tells you the commands that are running in background in current shell. Example:

```bash
(base) ashraf@320:~$ sleep 30 &
[1] 11292
(base) ashraf@320:~$ jobs
[1]+  Running                 sleep 30 &
(base) ashraf@320:~$ sleep 40 &
[2] 11293
(base) ashraf@320:~$ jobs
[1]-  Running                 sleep 30 &
[2]+  Running                 sleep 40 &
(base) ashraf@320:~$ ps --forest
    PID TTY          TIME CMD
  10306 pts/0    00:00:00 bash
  11293 pts/0    00:00:00  \_ sleep
  11295 pts/0    00:00:00  \_ ps
[1]-  Done                    sleep 30
# sleep 30 just got finished. That's why ps command did not list that.
```

- **top**  it gives the list of programm running with their cpu and memoery usage same as window's task manager. `ctrl+c` or `q` can be used to comeout of this procedure. It list the process in decreasing order of cpu utilization. Example:

```bash
top - 16:57:17 up  7:53,  1 user,  load average: 1.04, 1.51, 1.76
Tasks: 276 total,   1 running, 275 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.8 us,  2.3 sy,  0.0 ni, 93.0 id,  0.8 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   3711.3 total,    252.2 free,   2337.6 used,   1121.5 buff/cache
MiB Swap:   2048.0 total,   1889.7 free,    158.2 used.   1045.9 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                         
   8166 ashraf    20   0   49.0g 245452 120676 S   5.0   6.5   2:04.86 Discord                                                         
   1041 root      20   0 6661304  97200  45184 S   4.0   2.6   5:06.01 Xorg                                                            
   8115 ashraf    20   0  613956 105320  73592 S   4.0   2.8   1:19.14 Discord                                                         
   1377 ashraf    20   0 4479228 378260  90392 S   2.3  10.0   9:08.06 gnome-shell                                                     
   2763 ashraf    20   0   24.4g 246200 117784 S   2.3   6.5  33:12.95 chrome                                                          
   8001 ashraf    20   0   36.7g 143212 102032 S   1.7   3.8   0:37.60 Discord                                                         
  10298 ashraf    20   0  822596  49196  38184 S   1.7   1.3   0:01.81 gnome-terminal-                                                 
   4588 ashraf    20   0   16.5g 249200 127912 S   1.3   6.6   6:48.31 chrome                                                          
   2397 ashraf    20   0   16.5g 228460 136168 S   1.0   6.0   3:53.39 chrome                                                          
   4893 ashraf    20   0   36.3g 148992  55352 S   1.0   3.9   1:01.31 code                                                            
   4874 ashraf    20   0   50.5g 278496 120840 S   0.7   7.3   6:37.15 code                                                            
    192 root     -51   0       0      0      0 S   0.3   0.0   0:16.04 irq/87-SYNA2B33                                                 
    203 root     -51   0       0      0      0 S   0.3   0.0   0:07.84 irq/128-i2c_hid                                                 
   1149 root     -51   0       0      0      0 S   0.3   0.0   1:35.95 irq/138-nvidia                                                  
   1151 root      20   0       0      0      0 S   0.3   0.0   0:11.38 nv_queue                                                        
   1353 ashraf    20   0    7380   3792   3544 S   0.3   0.1   0:00.31 dbus-daemon                                                     
   1416 ashraf    20   0  162916   5852   5640 S   0.3   0.2   0:02.41 at-spi2-registr                                                 
   2717 ashraf    20   0   24.4g 137112  94916 S   0.3   3.6   0:44.67 chrome                                                          
   4444 ashraf    20   0   40.8g 168704 102176 S   0.3   4.4   1:40.72 code                                                            
   4476 ashraf    20   0  551044 218708  81620 S   0.3   5.8   3:14.05 code                                                            
   4606 ashraf    20   0   36.3g  74324  51476 S   0.3   2.0   0:08.07 code                                                            
   9670 root      20   0       0      0      0 I   0.3   0.0   0:00.21 kworker/2:0-mm_percpu_wq                                        
  10555 ashraf    20   0   20624   3796   3144 R   0.3   0.1   0:00.06 top                                                             
      1 root      20   0  167556  10484   7324 S   0.0   0.3   0:02.47 systemd                                                         
(base) ashraf@320:~$ echo $?
0
# I used ctrl+c to stop the top command and after checking the finish status it shows success means $?=0
```

- **kill** with -9 option and process ID kills a process. It works when you the owner of the process that is running. Example:

```bash
(base) ashraf@320:~$ coproc sleep 30
[1] 10322
(base) ashraf@320:~$ ps
    PID TTY          TIME CMD
  10306 pts/0    00:00:00 bash
  10322 pts/0    00:00:00 sleep
  10323 pts/0    00:00:00 ps
(base) ashraf@320:~$ kill -9 10322
(base) ashraf@320:~$ 
[1]+  Killed                  coproc COPROC sleep 30
```

- **ctrl + z**  is used to suspend a running program and put in background. And now we can run some other program/command in current shell. `fg` can bring the suspended program in foreground.

- flag set in bash shell.

```bash
(base) ashraf@320:~$ echo $-
himBHs
# we are going to start a child bash shell with less feature(flag) avaliable.
# \ is used so that this command does not run in current shell.
(base) ashraf@320:~$ bash -c echo" \$-;echo \$$; ps --forest"
hBc
11930
    PID TTY          TIME CMD
  10306 pts/0    00:00:00 bash
  11930 pts/0    00:00:00  \_ bash
  11931 pts/0    00:00:00      \_ ps
  ```

- **histroy**  command list the previously run commands since couple of days and using `!` symbol with command number we can the previously ran command right now. Example: (I will not give the whole output here.)

```bash
(base) ashraf@320:~$ history

  826  echo $?
  827  sleep 30 &
  828  ps
  829  fg
  830  sleep 30 &
  831  jobs
  832  sleep 40 &
  833  jobs
  834  ps --forest
  835  echo $-
  836  bash -c echo" \$-; $$; ps --forest"
  837  echo $-
  838  bash -c echo" \$-;echo \$$; ps --forest"
  839  kill -9 11930
  840  history 
(base) ashraf@320:~$ !837
echo $-
himBHs
```

- `Brace expansion`: It is enable because B is shown when **$-** shell varible is run. It gives following feature

```bash
(base) ashraf@320:~$ echo {A..D}
A B C D
(base) ashraf@320:~$ echo {A..E}{1..4}
A1 A2 A3 A4 B1 B2 B3 B4 C1 C2 C3 C4 D1 D2 D3 D4 E1 E2 E3 E4
(base) ashraf@320:~$ echo {a,d,f}{1..4}
a1 a2 a3 a4 d1 d2 d3 d4 f1 f2 f3 f4
(base) ashraf@320:~$ echo *
anaconda3 Anime Bsc_prog Desktop dir1 Documents Downloads Music Pictures Public snap Templates Videos
# echo * list all the file/directory in current folder. Because * expands for 0 or any number of character.
(base) ashraf@320:~$ echo D*
Desktop Documents Downloads
```

## tips

- **ls** * lists all the file present in `pwd` and directories with the file them in following manner.

```bash
(base) ashraf@320:~/Downloads$ ls * -l
-rw-rw-r-- 1 ashraf ashraf      73999 Dec 25 17:53  1
-rw-rw-r-- 1 ashraf ashraf      96428 Jan  1 19:30  5_6064237803246454280.pdf
-rw-rw-r-- 1 ashraf ashraf      63283 Dec 25 18:07  ackerman
-rw-rw-r-- 1 ashraf ashraf     118829 Dec 31 20:16 'Airtel broadband installation receipt.pdf'
-rw-rw-r-- 1 ashraf ashraf    5408204 Dec 25 15:52  Algorithm_Design_by_Jon_Kleinberg_Eva_Tardos.pdf
-rw-rw-r-- 1 ashraf ashraf 2975113637 Dec 30 18:28 '[AnimeKaizoku] Demon Slayer - Infinity Train Arc 1080p Eng Sub [SHINIGAMI_KIRA].zip'
-rw-rw-r-- 1 ashraf ashraf      67568 Dec 25 18:00  coderhigh_meme
-rw-rw-r-- 1 ashraf ashraf  398522695 Jan  9 21:51 '[Erai-raws] One Piece - 957 [1080pp][AnimeOut][1080pp][Multiple Subtitle][RapidBot].mkv'
-rw-rw-r-- 1 ashraf ashraf    1630912 Dec 27 10:49  Figure_1
-rw-rw-r-- 1 ashraf ashraf      69532 Dec 25 17:57  meme2
-rw-rw-r-- 1 ashraf ashraf    2135265 Dec 28 11:17 'Mission Improbable.pdf'
-rw-rw-r-- 1 ashraf ashraf      74954 Dec 31 21:25  Nps_registration_form.pdf
-rw-rw-r-- 1 ashraf ashraf  160737032 Jan  9 21:10  OnPi_956_HD_SubsPlease_ACB.mkv
-rw-rw-r-- 1 ashraf ashraf     534642 Dec 29 13:38  prime
-rw-rw-r-- 1 ashraf ashraf     310506 Dec 29 16:12  Resume.pdf
-rw-rw-r-- 1 ashraf ashraf    2993135 Dec 29 12:38  snail_prob.pdf

'[AnimeKaizoku] Demon Slayer - Infinity Train Arc 1080p Eng Sub [SHINIGAMI_KIRA]':
total 2905416
-rw-rw-r-- 1 ashraf ashraf 286031684 Oct 13 00:25 'Demon Slayer - Infinity Train Arc - 01.mkv'
-rw-rw-r-- 1 ashraf ashraf 401392738 Oct 18 05:14 'Demon Slayer - Infinity Train Arc - 02.mkv'
-rw-rw-r-- 1 ashraf ashraf 472313958 Oct 25 00:47 'Demon Slayer - Infinity Train Arc - 03.mkv'
-rw-rw-r-- 1 ashraf ashraf 496222711 Nov  9 06:49 'Demon Slayer - Infinity Train Arc - 04.mkv'
-rw-rw-r-- 1 ashraf ashraf 531595373 Nov 16 06:56 'Demon Slayer - Infinity Train Arc - 05.mkv'
-rw-rw-r-- 1 ashraf ashraf 451638540 Nov 22 04:10 'Demon Slayer - Infinity Train Arc - 06.mkv'
-rw-rw-r-- 1 ashraf ashraf 335915847 Nov 29 00:19 'Demon Slayer - Infinity Train Arc - 07.mkv'
# [AnimeKaizoku] Demon Slayer - Infinity Train Arc 1080p Eng Sub [SHINIGAMI_KIRA] -> this a folder inside Downloads
# file listed below this folder are the file inside that folder.
```
