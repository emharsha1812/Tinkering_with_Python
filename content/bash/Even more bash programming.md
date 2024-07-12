---
title: "Even more bash programming"
tags:
  - Command Line
  - Bash
  - Terminal
date: "2024-07-11"
---


### File Manipulation in Bash

touch
`touch` command is considered one of the easiest ways to create new files because it does not overwrite the existing files unlike `cp`, `rm` etc. It is also used to change the timestamps of files. A timestamp can be of three types: Access Date & Time, Modification Date & Time and the Time & Date when meta information associated with file was changed. By default, the behavior of this command is set to create empty files only. You can use different options to change file’s timestamp information.

#### Syntax:

```
touch [option] [file_name(s)]
```

Several options can be used together to simultaneously change the timestamp information associated to the file.

|**Option**|**Meaning**|
|---|---|
|-am|A is for Access Time and M is for Modification Time. You can change both together by using this option|
|-r|Means _reference_. It makes a reference to another file’s timestamps and use them for your file|
|-B|Means _Back_. This options changes time by going a few seconds back, specified by the user|
|-F|Means _Forward_. This options changes time by going a few seconds forward, specified by the user|
|-d or -t|These two options are used if the user wants to add his/her own access time in a specific forma|

```shell
touch my_file

touch -m my_file

touch -a my_file
```

## rm
`rm` is used to delete files and directories. By default, it is only set to remove files and not directories for safety. It basically unlinks the file name with the data stored in so that it cannot be accessed anymore. Before deleting any file, you must have permissions to delete it. You can delete multiple files at once. This command is almost similar to `rmdir`. The only difference is that `rmdir` is used to delete empty directories only. You can also delete symbolic links to a file, in this way, only link is removed but the file remains unaffected.