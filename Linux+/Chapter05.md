# Shells, Scripting, and Databases
## Customize and Use the Shell Environment
There are two ways to launch a shell: login and non-login.
  - Non-login shells launch from within a GUI desktop session
  - A login shell is a remote or non-GUI session which requires authentication.

Login shells read /etc/profile upon launch. Then it will check `~/.bash_profile`, `~/.bash_login` or `~/.profile`. The shell will load whatever values it finds first.

Non-login shells will first read from `/etc/bash.bashrc` and then from `~/.bashrc`.

- `~/.bash_logout` controls the way a shell session will close, including how anything left in memory is erased.
- Any contents in `/etc/skel` will be copied to the home directories of newly created users. See `examples.desktop`.

## Customize and Write Simple Scripts
### User Inputs
User inputs are incorporated using the `$` invocation.

- `read <variable>` Assigns user input to a variable.
- `declare -i <variable>` Assigns an integer input to a variable.

### Testing Values
Test your scripts!
- `-e` checks if a file exists.
- `-f` checks if it's a regular file.
- `-d` checks if it's a directory.
- `-r` conficms the file is readable for the current user.

Variables can be compared with `$variable1 = $variable2` or `$variable1 != $variable2`.

`case` and `esac` work like if/else statements with multiple choices.

### Loops
- `while` loops are very common!
  - `while [ $variable -gt 2 ]; do`: While $variable is greater than 2, continue until `done`.
  - `-gt` and `-lt` = greater than, less than.
  - A `while` loop continues as long as a condition IS true.
- `until` continues a loop as long as it is NOT true.
