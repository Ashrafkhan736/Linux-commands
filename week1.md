# Table of content

- [ln command](#ln)
- [ln -s command](#ln-s)
- [file command](#file)

## **ln**

```bash
$ln [file 1] [file 2]
```

>This command is use for hard link.
>
>This command will make the Inode of \<file2name> change in to Inode of \<file1name>.
>
>It is same as refrence used by two varible for same list object in python.
>
## **ln-s**

```bash
$ln -s [file 1] [file 2]
```

> This command is use for creating for soft link.
>
> It is similar to the desktop shortcut present in Windos's OS.

## **file**

```bash
$file week1.md
week1.md: ASCII text
```

>This command is use to list the file's information in following format.
>
>Example:

```bash
$file *
file.txt:                             empty
Notes:                                directory
SysComm:                              symbolic link to ../SysComm Dropbox
System Commands Sample Questions.md:  UTF-8 Unicode text, with very long lines
System Commands Sample Questions.pdf: PDF document, version 1.7
```

>Here * is a wild card entry same as regex.
