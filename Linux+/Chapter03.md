# Gnu and Unix Commands
## The Bash Shell
`echo $USER` will return the name of the account you used to log in.

`echo $PWD` will print the Present Work Directory.
  - `pwd` is quicker, and returns the same information.

`env` will display all shell variables, including local variables and functions.

New variables are created like so: `myvariable=hello`.
  - Running `echo $myvariable` will return "hello".

A dollar sign lets bash know you're referencing a variable.

These variables only exist for the current shell.

To allow it to be available for future shells, you'll need to export it with `export myvariable`

To destroy a saved variable, use `unset myvariable`

To display information about the linux kernel and installation, use `uname -a`

Bash saves a history of commands in the `.bash_history` file (stored in each user's home).

You can access the contents of this file with `history`.

If you need documentation, but don't know the exact spelling of a command, you can use `apropos` instead of `man`.

## Processing Text Streams
`cat -n` or `cat -nl` prints with numbered lines

`cut -d: -f1 /etc/passwd` will print the contenst of /etc/passwd, but only the first field in every line. `-d` delimiter, `-f` field.


`expand -t 10 filename` will convert every tab to ten spaces.

`unexpand -t 3 filename` will convert every three spaces to tabs.

You can use `fmt` to format the way text is printed to the screen.

`fmt -w 60 filename` will start a new line after 60 characters.

`fmt -t filename` will indent all but the first line of a paragraph.

`pr -d -1 10 filename` will print the first 10 lines of a file, double spaced.

  - `-d` will add a new space between lines.

  - `-l` sets the maximum number of lines to print.

`head` and `tail` return a certain number of lines from the top or bottom of a file.
  - `head -10 filename` will print the first 10 lines.
  - `tail -n 3 /etc/passwd` will print only the last three lines of passwd.
  - `tail -f /var/log/syslog` will continuously print lines as they are added.

`join column1 column2 > newfile` will merge data with overlapping columns and insert into a new file.

You can also merge with `paste`.
  - `paste column1 column2`.
  - `paste -s column1 column2` will print them sequentially.

The way lines can be rearranged using `sort`.
  - Without any flags, it will sort alphabetically.
  - `-r` will reverse the order.
  - `-n` will sort by number.
  - `-nr` will display the output in reverse numerical order.

To print only unique lines, you can use `uniq`.
  - `-u` will only print lines that are never printed.

`split` will divide a single file into multiple files of a specified length
  - `split -2 filename` will split the file into multiple files of two lines each. "line" means "paragraph".

`od filename` will print text in various formats.
  - `od -a filename` will substitute "ht" for tabs and "sp" for spaces
  - `od -c filename` will display tabs as \t and new lines as \n.

Text can be transformed using `tr`.
  - `cat /etc/passwd | tr "a-z" "A-Z"` will convert all lowercase letters to uppercase.

`wc filename` will print the total number of lines, words, and bytes.

To replace the first instance of "hello" in text.txt, use `cat txt | sed s/hello/"goodbye/"`
 - use `-g` for all instances

## File Management
`rm file?` will remove all files named "file1, file2" etc

`touch newfile` will update the access-time metadata for newfile

`file myfile` will display the metadata

###File Archives
`file.tar` is a Tape ARchive with at least two source files bundled together.

`file.tar.gz` is similar, but also compressed.

`tar czvf archivename.tar /home/myname/mydirectory*` will Create, Verbosely, a (Z)Compressed archive with all of the Files in mydirectory.

`tar xzvf archivename.tar.gz` will (X)Extract archivename.tar.gz

## Streams, Pipes, and Redirects
- stdin - Standard Input (0).
- stdout - Standard Output (1).
- stderr - Standard Error (2).

  These are accessed via their numerical identifiers.
The default behavior of the `>` redirect pipe is stdout.
  - A single `>` will overwrite a file, while a `>>` will append to the end of an existing file.
  - You can redirect error messages like `cat filename 2> errors.txt`. This will only write the errors, not the output of filename.

The `tee` command can send streams to multiple targets.
  - ex `ls -l | tee list.txt` will print the output of `ls -l` and also save it to list.txt.

Chaining commands:
  - `&&` executes a second command on the successful completion of the first.
  - `;` executes a second command regardless of the first outcome.
  - `||` will run either the first or second command, but not both.

## Managing Processes
### Monitoring Processes
`top` lists information about system processes.

`free -h` will display the amount of ram in use and how much is available.

`ps` lists all processes used by the current shell.
  - `ps aux | grep yoursearch` will search processes for yoursearch.
  - `pgrep -u root sshd` will search for any instance of sshd being run by the root user.

### Managing Background Processes
Adding an ampersand (`&`) to the end of a command will launch the process in the background.

Check background processes with `job`.

To bring a job back to the foreground, use `fig 1` where 1 is the job number.

To suspend a job, use `ctrl+z`

To return a job back to the background, use `bg 1`

Adding `nohup` to the inital command will continue the command even if the shell is closed.

Talk about Screen for a bit. idk, I dont like it.

### Killing Processes
`kill 1234` will kill PID 1234.

`killall process-name` will find the named process and kill it.

The default kill/killall value is 15 (sigterm).

`killall -l` will list all the signal codes.
  - `1, sighup` - parent shell is closing
  - `2, sigint` - interrupt (ctrl-c)
  - `9, shutdown` - hard kill
  - `15, sigterm` - regular kill

## Execution Priorities
`nice` can allocate values between 19 and -20, where 19 gives a process the least resources and -20 the most.
  - `nice -10 apt-get install apache2` will set the nondefault nice value to 10.
    - `nice --10 apt-get install apache2` sets the nice value to -10.

`renice -10 -p 3745` will set the niceness value of PID 3745 to 10. (or maybe -10??)

`renice 10 -u tony` will renice all of Tony's processes

`renice 10 -g audio` will renice all of a group's processes.

## Using Regular Expressions (REGEX)
Just look it up.

## Using vi
You know all of this.

--
## Test Yourself
1. What can the uname command display?
  * c. The name of your OS

2. The .bash_history file contains:
  * a. Your most recent commands

3. Which of these will NOT change the number of characters displayed?
  * d. fmt -w 60 filename

4. Which of these will create at least one new file?
  * a. split -3 filename

5. Which of these commands will copy subdirectories?
  * b. cp -r /etc /dev/sdb1

6. Which of these will copy your root filesystem to a backup drive?
  * d. dd if=/ of=/media/usb/backup/

7. In which of these cases will a file called errors.txt be created?
  * c. Running cat filename 2> errors.txt whine there is no such file

8. ls -l | tee list.txt will redirect traffic to which two places?
  * a. The screen and the file list.txt

9. Which of these will display all current system processes?
  * c. ps -e

  AND
  * d. ps aux

10. To return a process to the foreground, you use fg and the PID displayed by which command?
  * b. job

11. Which of the following will close a screen in GNU Screen?
  * d. ctrl-a \

12. Running kill with a value of 2 will send...
  * a. sigint

13. Which of these will create a nasty process?
  * c. nice --15 apt-get install apache2

14. Which of the following will interpret (hello) as plain text?
  * c. grep -F

15. Which of the following will remove an entire line in Vim Normal mode?
  * d. dd
