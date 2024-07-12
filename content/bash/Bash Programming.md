---
title: "Useful Bash commands that I need to use"
tags:
  - Command Line
  - Bash
  - Terminal
date: "2024-07-11"
---


**To connect to the remote machine**
```bash
ssh harshwardhan@10.24.36.21
```

**To check the GPU status**
```shell
nvidia-smi
```

**To check the versions of Python or poetry**
```shell
poetry --version

python --version
```

**To find out what your default interpreter is**
```shell
ps $$
```

**To find out the _full execution_ path of your shell interpreter**
```shell
which shell


#also we can use echo
echo $SHELL
```

**Changing your default shell**
```shell
chsh -s /bin/bash
```


## Default Commands

**Know the current login session**
```shell
whoami
```



### Basic Command Line Editing
- **Esc + T**: Swap the last two words before the cursor
- **Ctrl + H**: Delete the letter starting at the cursor
- **Ctrl + W**: Delete the word starting at the cursor
- **TAB**: Auto-complete files, directory, command names and much more
- **Ctrl + R**: To see the command history.
- **Ctrl + U**: Clear the line
- **Ctrl + C**: Cancel currently running commands.
- **Ctrl + L**: Clear the screen
- **Ctrl + T**: Swap the last two characters before the cursor

| **Characters** | **Description**                                                                                                                                                                                                                                    |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /              | Directory separator, used to separate a string of directory names. **Example:** `/home/projects/file`                                                                                                                                              |
| \              | Escape character. If you want to reference a special character, you must “escape” it with a backslash first. **Example:** `\n` means newline; `\v` means vertical tab; `\r` means return                                                           |
| #              | Lines starting with `#` will not be executed. These lines are comments                                                                                                                                                                             |
| .              | Current directory. When its the first character in a filename, it can also “hide” files                                                                                                                                                            |
| ..             | Returns the parent directory                                                                                                                                                                                                                       |
| ~              | Returns user’s home directory                                                                                                                                                                                                                      |
| ~+             | Returns the current working directory. It corresponds to the `＄PWD` internal variable                                                                                                                                                              |
| ~-             | Returns the previous working directory. It corresponds to the `＄OLDPWD` internal variable                                                                                                                                                          |
| *              | Represents 0 or more characters in a filename, or by itself, it matches all files in a directory. **Example:** `file*2019` can return: `file2019`, `file_comp2019`, `fileMay2019`                                                                  |
| []             | Can be used to represent a range of values, e.g. [0-9], [A-Z], etc. **Example:** `file[3-5].txt` represents `file3.txt`, `file4.txt`, `file5.txt`                                                                                                  |
| \|             | Known as “pipe". It redirects the output of the previous command into the input of the next command. **Example:** `ls \| less`                                                                                                                     |
| <              | It redirects a file as an input to a program. **Example:** `more < file.txt`                                                                                                                                                                       |
| >              | In **script name >filename** it will redirect the output of “script name” to “file filename”. Overwrite filename if it already exists. **Example:** `ls > file.txt`                                                                                |
| >>             | Redirect and append the output of the command to the end of the file. **Example:** `echo "To the end of file" >> file.txt`                                                                                                                         |
| &              | Execute a job in the background and immediately get your shell back. **Example:** `sleep 10 &`                                                                                                                                                     |
| &&             | “AND logical operator”. It returns (success) only if both the linked test conditions are true. It would run the second command only if the first one ran without errors. **Example:** `let "num = (( 0 && 1 ))"`; `cd/comp/projs && less messages` |
| ;              | “Command separator”. Allows you to execute multiple commands in a single line. **Example:** `cd/comp/projs ; less messages`                                                                                                                        |
| ?              | This character serves as a single character in a filename. **Example:** `file?.txt` can represent `file1.txt`, `file2.txt`, `file3.txt`                                                                                                            |

# Commands & Arguments

The general syntax followed by any Bash command is:

```shell
command_name [-option(s)] [argument[s]]
```
### Command Name: 

A command name is a unique word which is used to indicate to the system what action needs to be performed. Each command has its own set of arguments and options to narrow down the functionality even more. For example, `ls`is a very commonly used command.

### ==Argument:== 

Any Bash command takes a list of arguments to indicate to the system which objects to look for while performing the action. An argument could be a string, set of string or a token passed to the command. For example, the command `ls` can take a directory’s path as an argument.

```Shell
ls /home/user/Downloads/Music
```

### ==Options:== 

An option is also referred as the “mode” of the command. It controls the behavior of the command. It is a single character carry that carries a unique meaning. Most of the commands run without the option. Some commands can also take multiple sets of options simultaneously. For example, the command `ls` can take `-a` as an option which generally means “all” and is used to show hidden files.
```shell
ls -a
```

1. Some commands might not take any arguments or options such as `pwd`
2. Any option is written with a hyphen (-)
3. A double hyphen (–) is used to show the end of options if more than one options are used
4. The order of argument matters sometimes
5. In some commands, we can also pass flags as arguments. It simply carries a true or false value which could be used as an indication to perform something or no

