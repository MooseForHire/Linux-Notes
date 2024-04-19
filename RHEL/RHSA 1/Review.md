
`/etc`  persistent, system-specific configuration data
`/run`  non-persistent process runtime data

`cd`    with no args, returns you to your home directory
`cd -`  returns you to the working directory before the current working directory 

`mkdir -p`   Creates any missing parent directories. Ex: `mkdir -p Scripts\Bash` 

`cp -r /var/log/ ~/Logs`  Copy a directory and all of its contents

`rm -r` Removes directories and their contents. add `i` to  choose y/n. `f` = force
`rmdir Dir1`  Can remove empty directories

=========================================================

`-rw-r--r--. 1 user user 0 Oct 3 10:55 newfile.txt`    The `1` is # of hard links.

`ls -li`   Check inode number of file
`ln newfile.txt /tmp/newfile2.txt`    Create a hardlink called `newfile2.txt` 

- Hard links share the same permissions, ownership, timestamps, content.
- When one is changed, the other changes as well.
- When one is deleted, the other still exits.
- Hard links must be on the same file system. See below:

![[Capture.png]]



`ln -s ~/Documents/file.txt /tmp/file2.txt`  Creates a soft link called `file2.txt`

`ln -s /tmp ~/tempdir`  Creates a soft link called `tempdir` 

- Soft links can link two files on different file systems.
- Soft links can point to a directory or special file, not just regular files.
- When the original file/directory is deleted, the symbolic link no longer knows what data the file or directory contains.

=========================================================

Metacharacters

```
*	Any string of zero or more characters
?	Any single character
[abc…​]	Any one character in the enclosed class (between the square brackets)
[!abc…​]	Any one character not in the enclosed class
[^abc…​]	Any one character not in the enclosed class
[[:alpha:]]	Any alphabetic character
[[:lower:]]	Any lowercase character
[[:upper:]]	Any uppercase character
[[:alnum:]]	Any alphabetic character or digit
[[:punct:]]	Any printable character that is not a space or alphanumeric
[[:digit:]]	Any single digit from 0 to 9
[[:space:]]	Any single white space character, which might include tabs, newlines, carriage returns, form feeds, or spaces
```

Examples:

`ls [ac]*`     Lists any filenames starting with an `a` or a `c` , with anything following.

`ls ????`       Lists filenames that have 4 letters

=========================================================

Braces

`{}`  -- Comma separated values inside braces 

`echo {Sunday,Money,Tuesday,Wednesday}.log`    Prints Sunday.log Monday.log etc...

`echo file{1..5}.txt`   Prints file1.txt file2.txt file3.txt etc...

`echo file{1,2}{a,b}.txt`  Prints 4 files:   file1a.txt   file1b.txt  file2a.txt  file2b.txt

`echo f{a{1,2},b,c}.txt`   Prints: fa1.txt  fa2.txt   fb.txt   fc.txt 

=========================================================

Tilde

`~` Matches the current users home directory: `/home/csteen` or `/root`

`~/Documents`   =  `/home/csteen/Documents`

`echo ~root`     Prints `/root`

`echo ~csteen`  Prints `/home/csteen`

=========================================================

Variable

`VARIABLENAME=value`

`echo $VARIABLENAME`    prints `value`

`USERNAME=developer`
`echo ${USERNAME}`      prints `developer` 

Curly braces are used here to prevent mistakes.

=========================================================

Command Substitution

Command sub is used to combine commands together.

Remember: 

Format for `date` command:

- `date +%<format-option`

Examples:

`<Command1> $(command2)`

`echo $(date)`             prints  `Tue Oct 3 11:37:56 AM MST 2023`
`echo $(date +%A)`      prints  `Tuesday`

=========================================================

Escape Characters

`\`     Escapes the character immediately after it from expansion.            
`""`   Escapes anything inside of it except `$` `\` `!` and backtick 
`''`   Escapes EVERYTHING inside.

=========================================================

Man pages

Section 1: User commands
Section 2: System calls
Section 5: File formats
Section 8: Admin commands

`man passwd`    Displays `passwd(1)`
`man 5 passwd`  Displays `passwd(5)`

`man -k passwd` Searches the entire manual for the keyword "passwd"


=========================================================

Redirection

`&> file`    Sends both output and errors to `file` , creates it if it doesnt exist, if it does, overwrite it.

`2>`  Send stderr to a file

`> file1 2>&1` Create or overwrite `file1`, Send stderr and stdout to `file1`.
`&>`                   SAME THING

`>> file2 2>&1` Append to `file2`, Send stderr and stdout to `file2`
`&>>`                   Same

`| tee file`   Sends output to both screen and `file` at the same time.

=========================================================

VIM

Visual Mode: Select multiple characters for text manipulation.

From command mode (default when opening vim)

`v` enters Visual mode, also called Character Mode:

- `Shift+V` for multiline selection (Line mode)
- `Ctrl+V`   for block selection (Block Mode)

Character Mode: Highlights sentences
Block Mode: Data files

To exit Visual mode, hit `v` 

Copy and Paste:

1. From command mode, move the cursor to the first character to select.
2. Enter `v` for visual mode
3. Use arrow keys to expand selection.
4. Press `y` to copy
5. Position cursor at new location
6. Press `p` to paste.


Configuration files:

`/etc/vimrc`  Alter vim settings for the entire system.
`~/.vimrc`      Alter vim settings for a specific user.

=========================================================

Shell Variables

- Unique to a particular shell session
- Some are set when Bash starts.

You assign a shell variable when you make it: `USERNAME=csteen`

`set | less`      List all shell variables currently set.

=========================================================

Environment Variables

If a shell variable is not an environment variable, then only the shell can use it. However, if a shell variable is an environment variable, **then the shell and any programs that run from that shell can use the variable.**

To make a variable an environment variable, just add `export` in front of the variable:

`export EDITOR=vim`

Append directory to `$PATH` :

`export PATH=${PATH}:/home/user/sbin`

List environment variables for a shell:

`env`

=========================================================

BASH Startup Scripts:

`/etc/profile` 
`/etc/bashrc`

`~/.bash_profile`          Creating a variable here will only let the **login shell** use it. The example they give is modifying it when you `ssh` to a host. This is because you normally only use that shell to issue commands when `ssh` 'ing


`~/.bashrc`                     Creating a variable here will allow the users' login shell, **and any  other shells launched by the user to use it.** Add aliases here as well.

=========================================================

Alias

`alias hello='echo "Hello, my name is Caleb"'`

=========================================================

Unsetting Aliases, Shell Variables, and Environment Variables

- Unset a shell variable:

`unset $file1`

- Unset an environment variable (aka make it a shell variable):

`export -n USERNAME`

- Unset an alias:

`unalias hello`

=========================================================

Users, Groups, etc.

Login Shell = User's command line prompt

=========================================================

Sudo

`su - user2`         Switch to the user2 account

```
su -    

Switch to root and start a login shell. This sets up the shell environment as if it is a new login as that user.

sudo -i

Switches to the root account and runs that users default shell.
```

=========================================================






