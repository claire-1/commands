# Linux Commands
Linux is an operating system. Operating system = software to manage hardware and software resources

## Commands
### `$ ssh`
`$ ssh <your username>@<server’s IP address>`

### `$ exit` and `$ logout`
- `$ exit`
- `$ logout`
- or ctrl-d for EOF character (everything is a file in Linux)

### `$ pwd`
- present working directory
- lists what directory you are currently in (the absolute path)

### `$ cd` 
change directory
with no arguments, takes you back to your home directory
- `$ cd`
other ways to get to home directory
- `$ cd` 
- `$ cd ~ # bash preforms tilde substitution and replaces ~ with the absolute path to the home directory; same with $HOME environment variable`
- `$ cd $HOME`
- `$ cd <absolute path to home directory>`
- `$ cd ~<your username> # or put any username to go to their home directory`
with `.`, takes you to current directory
- `$ cd .`
with `..`, takes you to parent directory
- `$ cd ..`
with `-`, takes you to the previous directory you were in
- `$ cd -`
changes in a child process will not affect the parent (changing directory in the child process doesn’t change directory in the parent process)
For example:
`$ pwd
$ bash
$ cd /
$ exit
$ pwd # gives the same path as the first pwd command because the cd in the child (from $ bash) doesn’t affect the parent`

### `$ ls`
lists info about the file or directory \
usually lists the files or subdirectories in a directory unless use options to specify otherwise \
- `$ ls -l # is the long listing of the directory’s content and optional meta info`
- `$ ls -a # to see dot files (hidden files)`
- `$ ls -d # list directories as files (so show size and meta info instead of contents)`
- `$ ls -h # show file sizes in human readable formats (only useful when used with -l)`
- `$ ls -lh <filename> # shows 917K instead of 938848`
- `$ ls -altr dir # show all files (-a) with long listing (-l) sorted in reverse (-r) and the time (-t)`
- `$ ls -i # shows the i node number of the file next to the file name`
`$ ls` options
- `-l` (long listing, show file attributes)
- `-S` (sort by size, MUST be capital `S`)
- `-t` (sort by modification time)
- `-r` (reverse sort)
- `-h` (human readable sizes)
- `-a` (show all files including dot files, must use this to show ALL files and directories)
- `-d` (show directory as a file rather than showing the contents)
-`-1` (list one file per line (only  useful when listing to screen))
- `-i` (show inode number)

### `$ cat`
displays contents of a file or files
can concatenate many files together
`$ cat file1 file2 file3 # prints out contents of all files`
`$ cat` options:
- `-n` (displays line numbering)
- `-t` (displays tabs as special characters (^I))
- `-e` (displays end of line as special character ($))
example:
`$ cat -nte test-tabs`

### `$ tail`
`$ tail -n 5 /etc/hosts # gives last 5 lines of the file /etc/hosts`

### `$ grep`
Finds and prints matching lines in a text file
`grep` = global regular expression print
options:
- `-n` (number lines)
- `-i` (ignore case)
- `-v` (find lines that don’t match)
- `-c` (print count of number of matching lines)
- `-l` (return filename instead of matching text)
ex//
`$ grep -l “hi” test.txt`
output:
`test.txt`
good for grepping over many files at once and then printing out the filenames with the matching text
- `--include <pattern>` (only include filenames matching the patterns)
ex//
`$ grep -l -r ingham --include “*.txt” literature # use double quotes around “*.txt” so that the wildcard expansion isn’t done by the shell and instead of expression is passed to the command`
- `-r` (recursive)

### `$ less`
“pager” to interactively view a file
press space or f to move forward a page
press b to move back a page
press / to search
press n to repeat last search (go to the next match)
press shift-n to repeat last search (go backwards)
press q to quit


## Syntax
### Shell command syntax
`command [-option(s)] [positional argument(s)]` \
options preceded by `-` or `--`
- `$ cat -n file`
- `$ cat --number file # This shows the content of the file with line numbers next to each line` \
single char options can be grouped with one hyphen
- `$ ls -lda directoryName`
- `$ ls -l -d -a directoryName`
standalone `--` signifies end of options and beginning of positional args when there is ambiguity (positional arguments = file names)
- `$ ls -l -- directoryName`

multiple commands can be put on one line if separated by `;`
- `$ cd tmp; ls; cd ..`

`#` makes the rest of the line a comment, which is useful in shell scripting
- `$ cd tmp # assuming tmp exists`



