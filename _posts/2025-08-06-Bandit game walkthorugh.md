---
layout: post
read_time: true
show_date: true
title:  Bandit Game walkthrough Level (0-10)
date:   2025-08-06 15:58:00 +0800
description:  Deleting git branches
img: posts/20250806/OverTheWire.png
tags: [linux, gaming, terminal, bandit]
author: Amrit  Dhakal
github: daredoon/Jekyll/
---


 ### Level 0
 Goal: Access and log in to the game using ssh.

 Here I used **[GoogleShell](https://shell.cloud.google.com/)** linux terminal

 Syntax:
 ```bash
 ssh <username>@<remote> -p <port>
```
Bandit0:
 ```bash
 ssh bandit0@bandit.labs.overthewire.org -p 2220
 ```
Whens asked for passwords give corrent password like `bandit0` for Level0


### Level 0 - level 1
 Goal: find password for level 2

 Tip: Use find password for this level in `Readme` and use `2220` port to access this level.
 use `ls` and if you see Readme `vim Readme` to see password.

 For me password was:
 `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`
Then Ctrl+C :qa to save and exit or use Shift+Z then Shift+Q to exit.
 
 then type exit unitll you see your user name instead of bandit@bandit in the terminal

 ### Level 1 - Level 2

There is a - formated file.

This "-" as an argument refers to STDIN/STDOUT i.e dev/stdin or dev/stdout .So if you want to open this type of file you have to specify the full location of the file such as ./- .For eg. , if you want to see what is in that file use `cat ./-` or `cat < -` or `rev - | rev` or `more -`

Password : `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

 ### Level 2 - Level 3

If there are space in the file name it has to be coated with quotation mark. And if it starts with dash use above to open it. Ans: `cat < "--spaces in this filename--"`

Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx


 ### Level 3 - Level 4

use  `cd inhere` then `find` to see all hidden files and folders

then

cat file name to seee the contents `cat ./...Hiding-From-You`

Password: `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`


 ### Level 4 - Level 5

 use  `cd inhere` then `find` to see all hidden files and folders

then

cat file name to seee the contents `cat ./-file07`

Password:  `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`


 ### Level 5 - Level 6

use this code to find the file size of 1033 bytes:
```bash
#!/bin/bash

# Loop through the range 00 to 19
for i in $(seq -w 0 19); do
    # Construct the directory name
    dir="maybehere$i"
    
    # Check if the directory exists
    if [ -d "$dir" ]; then
        # Use ls -l to check file sizes and filter for 1033 bytes
        echo "Checking in directory: $dir"
        ls -la "$dir" | awk '$5 == 1033 {print "Found file: " $9 " in " dir}'
    else
        echo "Directory $dir does not exist."
    fi
done

```

Or 

```bash
cd inhere
find . -type f -size 1033c ! -executable -exec file {} + | grep "text"
```

Password: `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`



 ### Level 6 - Level 7

You can use the `find` command to search for files owned by `bandit7`, belonging to the group `bandit6`, and having a size of 33 bytes. Here’s the command you can run:

   ```bash
   find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
   ```

### Explanation of the Command:
   - `find /`: Start searching from the root directory. You can replace `/` with `.` to search from the current directory.
   - `-user bandit7`: Look for files owned by the user `bandit7`.
   - `-group bandit6`: Look for files owned by the group `bandit6`.
   - `-size 33c`: Find files that are exactly 33 bytes in size.
   - `2>/dev/null`: Suppress error messages (like permission denied) by redirecting them to `/dev/null`.

**Check the output**:
   The command will list files that match the criteria. If you find a file that meets all the conditions, you can use the `cat` command to display its contents:

```bash
   cat <filename>
  
   cat /var/lib/dpkg/info/bandit7.password
```


### Conclusion

This process will help you locate the file containing the password for the next level. Once you identify the correct file, use `cat` to read its contents and find the password.

Password: `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`