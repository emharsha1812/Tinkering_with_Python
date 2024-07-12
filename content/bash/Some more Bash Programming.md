---
title: "Some more Bash Programming.md"
tags:
  - Command Line
  - Bash
  - Terminal
date: "2024-07-11"
---


**To simply print**
```
echo I like to code
```

**Sleep: Sleep command pauses for some time as specified by the **NUMBER****
```shell
sleep NUMBER[SUFFIX]
```

**To check present working directory**
```shell
pwd
```

**Navigating directories**

Syntax
```shell
cd [option] [directory_name]
```

|**Option**|**Meaning**|
|---|---|
|/|To change the current directory to Root directory|
|-L|This mode lets cd move directly to the directory the link is pointing to|
|-P|This mode is opposite of -L. It uses physical directories and does not follow symbolic links|
|-e|This option is only used to show an error in case the `cd` command fails to determine the director|

##### Examples

To move from current directory to parent directory (Remember Linux has tree based directory structure so cd .. ( going back) means moving upward)
```shell
cd ..
```

To move from current directory to a different directory using relative path
==cd [name]==
```shell
cd ..
cd etc
ls
```

To move from current directory to a different directory using relative path
```shell
cd ..
cd etc/R/
ls
```

**To create a directory**
```shell
mkdir [options][dir_name]

mkdir demo
```
To remove a directory
```shell
rmdir demo
```

Print all the files in the directory, including the hidden files as well
```shell
ls -a
```

Sort files/directories by time
```shell
ls -t
```
