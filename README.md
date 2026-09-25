<div align="center"><img src="https://github.com/ksyv/holbertonschool-web_front_end/blob/main/baniere_holberton.png"></div>

# C - Simple Shell

## Table of Contents :

  - [0. README, man, AUTHORS](#subparagraph0)
  - [1. Betty would be proud](#subparagraph1)
  - [2. Simple shell 0.1](#subparagraph2)
  - [3. Simple shell 0.2](#subparagraph3)
  - [4. Simple shell 0.3](#subparagraph4)
  - [5. Simple shell 0.4](#subparagraph5)
  - [6. Simple shell 1.0](#subparagraph6)
  - [7. What happens when you type `ls -l *.c` in the shell](#subparagraph7)
  - [8. Test suite](#subparagraph8)
  - [9. Simple shell 0.1.1](#subparagraph9)
  - [10. Simple shell 0.2.1](#subparagraph10)
  - [11. Simple shell 0.4.1](#subparagraph11)
  - [12. Simple shell 0.4.2](#subparagraph12)
  - [13. setenv, unsetenv](#subparagraph13)
  - [14. cd](#subparagraph14)
  - [15. ;](#subparagraph15)
  - [16. && and ||](#subparagraph16)
  - [17. alias](#subparagraph17)
  - [18. Variables](#subparagraph18)
  - [19. Comments](#subparagraph19)
  - [20. help](#subparagraph20)
  - [21. history](#subparagraph21)
  - [22. File as input](#subparagraph22)
## Background Context

Write a simple UNIX command interpreter.

![Shell](https://s3.eu-west-3.amazonaws.com/hbtn.intranet.project.files/holbertonschool-low_level_programming/235/shell.jpeg)

*^ "The Gates of Shell", by [Spencer Cheng](/rltoken/IBAW_i8ptSNg3Sf5hMLSJQ), featuring [Julien Barbier](/rltoken/YinaOdtW8C_NL3NlSD1Jdg)*

## Resources

**Read or watch**:

- [Unix shell](/rltoken/McTQ6qvcqZZQlZtZdjdVnQ) 
- [Thompson shell](/rltoken/FLRzIA3zLln5XV7erPHgsQ) 
- [Ken Thompson](/rltoken/Pzs_A3Wo6LTHE8WX_uKiWg) 
- **Everything you need to know to start coding your own shell** concept page

**man or help**: 

- `sh` (*Run `sh` as well*)

## Learning Objectives

At the end of this project, you are expected to be able to [explain to anyone](/rltoken/fmCgGY50xkpiN1RkCWnLYA), __without the help of Google__:

### General

- Who designed and implemented the original Unix operating system
- Who wrote the first version of the UNIX shell
- Who invented the B programming language (the direct predecessor to the C programming language)
- Who is Ken Thompson
- How does a shell work
- What is a pid and a ppid
- How to manipulate the environment of the current process
- What is the difference between a function and a system call
- How to create processes
- What are the three prototypes of `main`
- How does the shell use the `PATH` to find the programs
- How to execute another program with the `execve` system call
- How to suspend the execution of a process until one of its children terminates
- What is `EOF` / "end-of-file"?

## Requirements

### General

- Allowed editors: `vi`, `vim`, `emacs`
- All your files will be compiled on Ubuntu 20.04 LTS using `gcc`, using the options `-Wall -Werror -Wextra -pedantic -std=gnu89`
- All your files should end with a new line
- A `README.md` file, at the root of the folder of the project is mandatory
- Your code should use the `Betty` style. It will be checked using [betty-style.pl](https://github.com/hs-hq/Betty/blob/master/betty-style.pl) and [betty-doc.pl](https://github.com/hs-hq/Betty/blob/master/betty-doc.pl)
- Your shell should not have any memory leaks
- No more than 5 functions per file
- All your header files should be include guarded
- Use system calls only when you need to ([why?](/rltoken/rp53OodD6JzhS5Cv4DHkxQ))

### GitHub
**There should be one project repository per group. If you clone/fork/whatever a project repository with the same name before the second deadline, you risk a 0% score.**

## More Info

### Output

- Unless specified otherwise, your program **must have the exact same output** as `sh` (`/bin/sh`) as well as the exact same error output.
- The only difference is when you print an error, the name of the program must be equivalent to your `argv[0]` (See below)

Example of error with `sh`:

```
julien@ubuntu:/# echo "qwerty" | /bin/sh
/bin/sh: 1: qwerty: not found
julien@ubuntu:/# echo "qwerty" | /bin/../bin/sh
/bin/../bin/sh: 1: qwerty: not found
```

Same error with your program `hsh`:

```
julien@ubuntu:/# echo "qwerty" | ./hsh
./hsh: 1: qwerty: not found
julien@ubuntu:/# echo "qwerty" | ./././hsh
./././hsh: 1: qwerty: not found
```

### List of allowed functions and system calls+

- all functions from string.h
- `access` (man 2 access)
- `chdir` (man 2 chdir)
- `close` (man 2 close)
- `closedir` (man 3 closedir)
- `execve` (man 2 execve)
- `exit` (man 3 exit)
- `_exit` (man 2 \_exit)
- `fflush` (man 3 fflush)
- `fork` (man 2 fork)
- `free` (man 3 free)
- `getcwd` (man 3 getcwd)
- `getline` (man 3 getline)
- `getpid` (man 2 getpid)
- `isatty` (man 3 isatty)
- `kill` (man 2 kill)
- `malloc` (man 3 malloc)
- `open` (man 2 open)
- `opendir` (man 3 opendir)
- `perror` (man 3 perror)
- `printf` (man 3 printf)
- `fprintf` (man 3 fprintf)
- `vfprintf` (man 3 vfprintf)
- `sprintf` (man 3 sprintf)
- `putchar` (man 3 putchar)
- `read` (man 2 read)
- `readdir` (man 3 readdir)
- `signal` (man 2 signal)
- `stat` (\_\_xstat) (man 2 stat)
- `lstat` (\_\_lxstat) (man 2 lstat)
- `fstat` (\_\_fxstat) (man 2 fstat)
- `strtok` (man 3 strtok)
- `wait` (man 2 wait)
- `waitpid` (man 2 waitpid)
- `wait3` (man 2 wait3)
- `wait4` (man 2 wait4)
- `write` (man 2 write)

### Compilation

Your shell will be compiled this way:

```
gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c -o hsh
```

### Testing

Your shell should work like this in interactive mode:

```
julien@ubuntu:/# ./hsh
($) /bin/ls
hsh main.c shell.c
($)
($) exit
julien@ubuntu:/#
```

But also in non-interactive mode:

```
julien@ubuntu:/# echo "/bin/ls" | ./hsh
hsh main.c shell.c test_ls_2
julien@ubuntu:/# cat test_ls_2
/bin/ls
/bin/ls
julien@ubuntu:/# cat test_ls_2 | ./hsh
hsh main.c shell.c test_ls_2
hsh main.c shell.c test_ls_2
julien@ubuntu:/#
```


### Checks

The Checker will be released at the end of the project (1-2 days before the deadline). 
We **strongly** encourage the entire class to work together to create a suite of checks covering both regular tests and edge cases for each task. See task `8. Test suite`.

After the deadline, you will need to fork the repository if it's not on your Github account to be able to be corrected by the checker.


## Task
### 0. README, man, AUTHORS <a name='subparagraph0'></a>

* Write a `README`
* Write a `man` for your shell.
* You should have an `AUTHORS` file at the root of your repository, listing all individuals having contributed content to the repository. Format, see Docker

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`
* File: `README.md, man_1_simple_shell, AUTHORS`

---

### 1. Betty would be proud <a name='subparagraph1'></a>

Write a beautiful code that passes the Betty checks

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 2. Simple shell 0.1 <a name='subparagraph2'></a>

Write a UNIX command line interpreter.

* Usage: `simple_shell`

Your Shell should:

* Display a prompt and wait for the user to type a command. A command line always ends with a new line.
* The prompt is displayed again each time a command has been executed.
* The command lines are simple, no semicolons, no pipes, no redirections or any other advanced features.
* The command lines are made only of one word. No arguments will be passed to programs.
* If an executable cannot be found, print an error message and display the prompt again.
* Handle errors.
* You have to handle the "end of file" condition (`Ctrl+D`)

You don't have to:

* use the `PATH`
* implement built-ins
* handle special characters : `"`, `'`, ```, `\`, `*`, `&`, `#`
* be able to move the cursor
* handle commands with arguments

*`execve` will be the core part of your Shell, don't forget to pass the environ to it…*

```bash
julien@ubuntu:~/shell$ ./shell 
#cisfun$ ls
./shell: No such file or directory
#cisfun$ /bin/ls
barbie_j       env-main.c  exec.c  fork.c  pid.c  ppid.c    prompt   prompt.c  shell.c    stat.c         wait
env-environ.c  exec       fork    mypid   ppid   printenv  promptc  shell     stat test_scripting.sh  wait.c
#cisfun$ ^[[D^[[D^[[D
./shell: No such file or directory
#cisfun$ ^[[C^[[C^[[C^[[C
./shell: No such file or directory
#cisfun$ exit
./shell: No such file or directory
#cisfun$ ^C
julien@ubuntu:~/shell$ echo "/bin/ls" | ./shell
barbie_j       env-main.c  exec.c  fork.c  pid.c  ppid.c    prompt   prompt.c  shell.c    stat.c         wait
env-environ.c  exec       fork    mypid   ppid   printenv  promptc  shell     stat test_scripting.sh  wait.c
julien@ubuntu:~/shell$
```

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 3. Simple shell 0.2 <a name='subparagraph3'></a>

Simple shell 0.1 +

* Handle command lines with arguments

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 4. Simple shell 0.3 <a name='subparagraph4'></a>

Simple shell 0.2 +

* Handle the `PATH`
* `fork` must not be called if the command doesn't exist

```bash
julien@ubuntu:~/shell$ ./shell_0.3
:) /bin/ls
barbie_j       env-main.c  exec.c  fork.c  pid.c  ppid.c    prompt   prompt.c  shell_0.3  stat      test_scripting.sh  wait.c
env-environ.c  exec       fork    mypid   ppid   printenv  promptc  shell     shell.c    stat.c  wait
:) ls
barbie_j       env-main.c  exec.c  fork.c  pid.c  ppid.c    prompt   prompt.c  shell_0.3  stat      test_scripting.sh  wait.c
env-environ.c  exec       fork    mypid   ppid   printenv  promptc  shell     shell.c    stat.c  wait
:) ls -l /tmp 
total 20
-rw------- 1 julien julien    0 Dec  5 12:09 config-err-aAMZrR
drwx------ 3 root   root   4096 Dec  5 12:09 systemd-private-062a0eca7f2a44349733e78cb4abdff4-colord.service-V7DUzr
drwx------ 3 root   root   4096 Dec  5 12:09 systemd-private-062a0eca7f2a44349733e78cb4abdff4-rtkit-daemon.service-ANGvoV
drwx------ 3 root   root   4096 Dec  5 12:07 systemd-private-062a0eca7f2a44349733e78cb4abdff4-systemd-timesyncd.service-CdXUtH
-rw-rw-r-- 1 julien julien    0 Dec  5 12:09 unity_support_test.0
:) ^C
julien@ubuntu:~/shell$
```

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 5. Simple shell 0.4 <a name='subparagraph5'></a>

Simple shell 0.3 +

* Implement the `exit` built-in, that exits the shell
* Usage: `exit`
* You don't have to handle any argument to the built-in `exit`

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 6. Simple shell 1.0 <a name='subparagraph6'></a>

Simple shell 0.4 +

* Implement the `env` **built-in**, that prints the current environment

```bash
julien@ubuntu:~/shell$ ./simple_shell
$ env
USER=julien
LANGUAGE=en_US
SESSION=ubuntu
COMPIZ_CONFIG_PROFILE=ubuntu
SHLVL=1
HOME=/home/julien
C_IS=Fun_:)
DESKTOP_SESSION=ubuntu
LOGNAME=julien
TERM=xterm-256color
PATH=/home/julien/bin:/home/julien/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
DISPLAY=:0
$ exit
julien@ubuntu:~/shell$
```

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 7. What happens when you type `ls -l *.c` in the shell <a name='subparagraph7'></a>

Write a blog post describing step by step what happens when you type `ls -l *.c` and hit Enter in a shell. Try to explain every step you know of, going in as much details as you can, give examples and draw diagrams when needed. You should merge your previous knowledge of the shell with the specifics of how it works under the hoods (including syscalls).

* Have at least one picture, at the top of the blog post
* Publish your blog post on Medium or LinkedIn
* Share your blog post at least on LinkedIn
* Only one blog post by team
* The blog post must be done and published before the first deadline (it will be part of the manual review)
* Please, remember that these blogs must be written in English to further your technical ability in a variety of settings

When done, please add all urls below (blog post, LinkedIn post, etc.)

---

### 8. Test suite <a name='subparagraph8'></a>

Contribute to a test suite for your shell.

This is a task shared by everyone in the class.

* Every team (who contributed) will get the same score for this task (The repository owner will not get more points)
* You have to be pro-active and agree on one and unique repository to use for the test suite
* Please provide the link to the repository you contributed to
* Your contribution must be relevant (Correcting typos is nice and always appreciated on the open source sphere, but we won't consider this a contribution at this point, **unless** it fixes a bug)

Guidelines for your test suite repository:

* The test suite should cover every tasks from `0.` to `20.`
* The test suite should cover every regular cases (many different examples) and possible edge cases
* The entire class should work on the same test suite. Use only one repository (don't forget the `README.md` file)
* Start adding tests ASAP and not just before the deadline in order to help everyone from day 0
* You can take (or fork) inspiration from this example, but it is not mandatory to follow this format/way
* Adopt a style and be consistent. You can, for example, follow this style guide. If you choose a style that already exists, add it to the `README.md` in a style section. If you write your own, create a Wiki page attached to the project and refer to it in the `README.md` style section.
* If you choose to use this code, make sure to update the style accordingly
* You should have an `AUTHORS` file, listing all individuals having contributed content to the repository. Format, see Docker

**Go teams!**

---

### 9. Simple shell 0.1.1 <a name='subparagraph9'></a>

Simple shell 0.1 +

* Write your own `getline` function
* Use a buffer to read many chars at once and call the least possible the `read` system call
* You will need to use `static` variables
* You are not allowed to use `getline`

You don't have to:

* be able to move the cursor

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 10. Simple shell 0.2.1 <a name='subparagraph10'></a>

Simple shell 0.2 +

* You are not allowed to use `strtok`

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 11. Simple shell 0.4.1 <a name='subparagraph11'></a>

Simple shell 0.4 +

* handle arguments for the built-in `exit`
* Usage: `exit status`, where `status` is an integer used to exit the shell

```ruby
julien@ubuntu:~/shell$ ./shell_0.4.1
$ exit 98
julien@ubuntu:~/shell$ echo $?
98
julien@ubuntu:~/shell$
```

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 12. Simple shell 0.4.2 <a name='subparagraph12'></a>

Simple shell 0.4 +

* Handle `Ctrl+C`: your shell should not quit when the user inputs `^C`

man 2 `signal`.

```ruby
julien@ubuntu:~/shell$ ./shell_0.4.2
$ ^C
$ ^C
$ ^C
$ ls /var
backups  cache    crash  lib  local  lock  log  mail  metrics  opt  run  snap  spool  tmp
$ ^C
$ ^C
$ ^C
$ exit
julien@ubuntu:~/shell$
```

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 13. setenv, unsetenv <a name='subparagraph13'></a>

Simple shell 1.0 +

Implement the `setenv` and `unsetenv` builtin commands

* `setenv`
Initialize a new environment variable, or modify an existing one
Command syntax: `setenv VARIABLE VALUE`
Should print something on stderr on failure
* `unsetenv`
Remove an environment variable
Command syntax: `unsetenv VARIABLE`
Should print something on stderr on failure

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 14. cd <a name='subparagraph14'></a>

Simple shell 1.0 +

Implement the builtin command `cd`:

* Changes the current directory of the process.
* Command syntax: `cd [DIRECTORY]`
* If no argument is given to `cd` the command must be interpreted like `cd $HOME`
* You have to handle the command `cd -`
* You have to update the environment variable `PWD` when you change directory

`man chdir`, `man getcwd`

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 15. ; <a name='subparagraph15'></a>

Simple shell 1.0 +

* Handle the commands separator `;`

```bash
alex@~$ ls /var ; ls /var
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
alex@~$ ls /hbtn ; ls /var
ls: cannot access /hbtn: No such file or directory
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
alex@~$ ls /var ; ls /hbtn
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
ls: cannot access /hbtn: No such file or directory
alex@~$ ls /var ; ls /hbtn ; ls /var ; ls /var
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
ls: cannot access /hbtn: No such file or directory
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
alex@~$
```

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 16. && and || <a name='subparagraph16'></a>

Simple shell 1.0 +

* Handle the `&&` and `||` shell logical operators

```shell
alex@~$ ls /var && ls /var
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
alex@~$ ls /hbtn && ls /var
ls: cannot access /hbtn: No such file or directory
alex@~$ ls /var && ls /var && ls /var && ls /hbtn
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
ls: cannot access /hbtn: No such file or directory
alex@~$ ls /var && ls /var && ls /var && ls /hbtn && ls /hbtn
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
ls: cannot access /hbtn: No such file or directory
alex@~$
alex@~$ ls /var || ls /var
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
alex@~$ ls /hbtn || ls /var
ls: cannot access /hbtn: No such file or directory
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
alex@~$ ls /hbtn || ls /hbtn || ls /hbtn || ls /var
ls: cannot access /hbtn: No such file or directory
ls: cannot access /hbtn: No such file or directory
ls: cannot access /hbtn: No such file or directory
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
alex@~$ ls /hbtn || ls /hbtn || ls /hbtn || ls /var || ls /var
ls: cannot access /hbtn: No such file or directory
ls: cannot access /hbtn: No such file or directory
ls: cannot access /hbtn: No such file or directory
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  spool  tmp
alex@~$
```

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 17. alias <a name='subparagraph17'></a>

Simple shell 1.0 +

* Implement the `alias` builtin command
* Usage: `alias [name[='value'] ...]`
`alias`: Prints a list of all aliases, one per line, in the form `name='value'`
`alias name [name2 ...]`: Prints the aliases `name`, `name2`, etc 1 per line, in the form `name='value'`
`alias name='value' [...]`: Defines an alias for each `name` whose `value` is given. If `name` is already an alias, replaces its value with `value`

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 18. Variables <a name='subparagraph18'></a>

Simple shell 1.0 +

* Handle variables replacement
* Handle the `$?` variable
* Handle the `$$` variable

```bash
julien@ubuntu:~/shell$ ./hsh
$ ls /var
backups  cache    crash  lib  local  lock  log  mail  metrics  opt  run  snap  spool  tmp
$ echo $?
0
$ echo $$
5104
$ echo $PATH
/home/julien/bin:/home/julien/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
$ exit 
julien@ubuntu:~/shell$
```

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 19. Comments <a name='subparagraph19'></a>

Simple shell 1.0 +

* Handle comments (`#`)

```ruby
julien@ubuntu:~/shell$ sh
$ echo $$ # ls -la
5114
$ exit
julien@ubuntu:~/shell$
```

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 20. help <a name='subparagraph20'></a>

Simple shell 1.0 +

* Implement the `help` built-in
* Usage: `help [BUILTIN]`

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 21. history <a name='subparagraph21'></a>

Simple shell 1.0 +

* Implement the history built-in, without any argument
* The `history` built-in displays the history list, one command by line, preceded with line numbers (starting at `0`)
* On `exit`, write the entire history, without line numbers, to a file named `.simple_shell_history` in the directory `$HOME`
* When the shell starts, read the file `.simple_shell_history` in the directory `$HOME` if it exists, and set the first line number to the total number of lines in the file modulo `4096`

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---

### 22. File as input <a name='subparagraph22'></a>

Simple shell 1.0 +

* Usage: `simple_shell [filename]`
* Your shell can take a file as a command line argument
* The file contains all the commands that your shell should run before exiting
* The file should contain one command per line
* In this mode, the shell should not print a prompt and should not read from `stdin`

**Repo:**

* GitHub repository: `holbertonschool-simple_shell`

---


## Authors
Ksyv - [GitHub Profile](https://github.com/ksyv)
