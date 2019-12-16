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

### `$ echo`
prints its arguments to standard out
-  `$ echo hello world`
- prints: `hello world`
- `$ echo ‘hello world’`
- prints: `hello world`
- `$ echo “hello world”`
- prints: `hello world`
flags:
`-e # interprets special characters`
use for printing white space with echo
`\t` for tab
`\n` for newline
example: `$ echo -e “a\nb\nc”` \
output: \
`a` \
`b` \
`c` \
example: `$ echo “a\nb\nc”` \
output: `a\nb\nc`

### `$ date`
displays the current time in a given format \
can be used to set the system date \
example: `$ date` \
output: `Mon Feb 26 18:20:13 UTC 2018` \
example: `$ date -I # capital i` \
output: `2018-02-26` \
example: `$ date -R` \
output: `Mon, 26 Feb 2018 18:21:55 +0000` 

### `$ cal`
prints a calendar \
`$ cal -m july # prints the month of july for the current year (even if july has past)`

### `$ seq`
prints numbers from FIRST to LAST in steps of INCREMENT \
example: `$ seq 1 10` \
output: \
`1` \
`2` \
`3` \
`4` \
`5` \
`6` \
`7` \
`8` \
`9` \
`10` \
example: `$ seq 1 3 20 # starts at 1, goes to 20, increases by 3 each time` \
output: \
`1` \
`4` \
`7` \
`10` \
`13` \
`16` \
`19` 

### `$ sleep`
suspends execution for a specified number of seconds \
example: `$ sleep 2`

### `$ man`
- interactively displays a manual page for commands
- useful to find out about option flags
- terse output
- uses same paging and search keys as less command

### `$ help`
displays a help page for commands that may not have `$ man` entries

### `--help option`
- available for many commands 
- tells you how to use that command 
- example: `$ cat --help` 

### `$ touch`
- creates a file (or multiple files if multiple names provided in one line) if doesn’t (don’t) exist
- updates the modification time of the file
- example: `$ touch foo bar baz`
- !! DOESN’T take input file, just creates an empty file or updates the timestamp of an existing file

### `$ cp`
copy a file or files \
Usage: \
`cp [OPTION] SOURCE DEST_FILE` \
`cp [OPTION] SOURCE(S) DIRECTORY` \
`# $ cp assumes that if you specify multiple files, the last specified argument is a directory` \
`# therefore, it will fail if the last specified argument isn’t a directory` \
examples: \
`$ cp /class/files/alice.txt . # copies /class/files/alice.txt to the current directory` \
`$ cp alice.txt ~/test/my-alice.txt # copy single file to new name and location` \
`$ cp keats fstree.dot ~/test # copy multiple files to a directory` \
#### cases: 
|command|first arguement|action|
|-------|---------------|------|
|`$ cp f1 f2`|`f2` doesn’t exist|`f2` created as copy of `f1`|
|`$ cp f1 f2`|`f2` exists|`f2` is overwritten (not reversible!)|
|`$ cp f1 d2`|`d2` exists (is a directory)|puts a copy of `f1` in `d2`|
|`$ cp f1 d2`|`d2/f1` is an existing file (`f1` in directory `d2`)|`d2/f1` is overwritten (not reversible!)|
|`$ cp f1 d2/`|`d2` doesn’t exist|error: can’t create file (not a dir) b/c the directory doesn’t exist|
|`$ cp f1 dw`|`d2/f1` exists and is a directory (`d2/f1` is a directory)|error: can’t overwrite dir with file|
|`$ cp d1 x`|`d1` is a directory|error: can’t copy directory b/c `-R` flag wasn’t used|

#### recursive copy
use `-R` flag to recursively copy the specified directory and contents of all subdirectories \
examples: \
`$ cp -R dirname target_dir` \
`$ cp -R dirname1 dirname2 target_dir` \

### `$ mv`
move a file or a directory \
changes the location of a file or renames it \

#### cases:
|command|first arguement|action|
|-------|---------------|------|
|`$ mv f1 f2`|`f2` doesn’t exist|renames `f1` to `f2`|
|`$ mv f1 f2`|`f2` exists|renames `f1` to `f2` and old `f2` is removed (not reversible!)|
|`$ mv f1 d2`|`d2` is a directory|moves `f1` into `d2`|
|`$ mv f1 d2/`|`d2` is a directory|moves `f1` into `d2`|
|`$ mv f1 d2`|`d2/f1` exists|moves `f1` into `d2` and removes old `d2/f1` (not reversible) |

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

### I/O redirection
#### standard streams
- `STDIN` = 0
- `STDOUT` = 1
- `STDOUT` goes to terminal by defult
- `STDERR` = 2

#### redirecting output (`STDOUT`) using `>`
- example: `date > thedate`
- `>` overwrites the file thedate with the new output
- `>` will create the file for you if it doesn’t already exist

#### redirecting output (`STDOUT`) using `>>`
- example: `date >> myoutput`
- `>>` appends the output to the end of the file (good for log files)
- `>>` will create the file if it doesn’t already exist

#### redirecting by not specifying input file
- many commands (such as `cat`) take their input from either a file argument or from `STDIN` if a file for the file argument isn’t specified
- example: `cat > new_file # and then start typing b/c no file specified to cat so the keyboard (default STDIN) is used; press RETURN for new line; use ctrl-d for end-of-file b/c STDIN is a file`

#### redirecting input (`STDIN`) to take input from a file
- `sort /class/files/keats`
- same as
- `sort < /class/files/keats`

#### redirecting `STDIN` and `STDOUT`
- `sort < /class/files/keats > sortedkeats`

#### redirecting `STDERR`
- If you redirect `STDOUT` but not `STDERR`, `STDERR` will still print to the terminal screen.
- use `2>` to redirect `STDERR`
- `cat /etc/passwd /etc/shadow > new 2>/dev/null # discard errors by redirecting to /dev/null; cat two files at once (does cat on the first one followed directly by cat on the second one)`

#### redirecting `STDOUT` and `STDERR`
- `2>&1` redirects `STDERR` (2) to `STDOUT` (1)
- `1>&2` redirects `STDOUT` (1) to `STDERR` (2)
- ORDER MATTERS!
- example: `date sfsf 2>&1 1> log # redirects STDERR to STDOUT (so both going to terminal) and then redirects STDOUT to log (so STDOUT goes to log and STDERR goes to terminal)`
- example: `date sfsf 1> log 2>&1 # redirects STDOUT to log and then redirects STDERR to STDOUT (so both go to the log)`

#### redirection using “Here string”
- `<<<` redirects `STDIN` from a here string (string specified in the command)
- example: `wc -w <<< “This is a here string”`
- example: `grep “lend” <<< “lend me your ears”`

#### redirection using “Here document”
`<<` specifies a here document (used to include data in a shell script itself) \
`$ grep dog <<DATA # DATA is some tag used to mark the end of the here document` \
`rose flower` \
`dog animal` \
`blue color` \
`# put tag at end to mark end of here document (must be on its own line)` \
`DATA` \
output from the command above: `dog animal`

### Pipes
output one command becomes the input of the next command \
example: `$ ps aux | grep firefox | wc -l > output_file # wc -l takes input from grep firefox output and counts the lines in the file and stores that result in output_file` \
can input interactive commands with pipes (as the last operation) \
example: `$ cat keats | sort | less`


### absolute vs relative paths
#### absolute path
- always refers to the same location
- starts with `/`
#### relative path
- specifies a path relative to your current directory
- starts with a file or directory name (without leading slash) or with `.` or `..`
- `.` for current directory



