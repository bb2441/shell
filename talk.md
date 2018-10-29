<script type="text/javascript"
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
# shell

## 

BB2441 The shell


---

layout: false

## Goals

* Navigation in the file system
* Working with files
* Combining commands
* Repeating commands (looping)
* Choosing commands (branching)
* Finding stuff

---
<img height="200" src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/7c/Typewriter_%284855182596%29.jpg/1599px-Typewriter_%284855182596%29.jpg">

--


<img height="200" src="https://upload.wikimedia.org/wikipedia/commons/0/00/Rokli_mechanical_calculator_1.jpg">

---

<img height="200" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/DEC_VT100_terminal.jpg/1013px-DEC_VT100_terminal.jpg">

--

<img height="200" src="https://c2.staticflickr.com/4/3029/2627291590_66060a771b_o.jpg">

---

## Shell

* *In computing, a shell is a user interface for access to an operating system's
services.* 

* *It is named a shell because it is a layer around the operating system
kernel (Wikipedia)*

<div class="col-md-12">
<img class="img-responsive" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTQrJeHObbV2Y-Drb7P3vXFHnYoO-bU3Ii7haw5vqT-2wTUE3yfMg">
</div>
---

## Why

GUI vs CLI

* you want the computer to do stuff for you
* you need to communicate with the computer somehow
    * sign language: point-and-click (graphical user interface)
    * words: small set of commands the computer understands (command line * interface, aka terminal aka shell)



- Cryptic

+ Powerful
+ Remote access
+ Combinations of programs


* A collection of well defined programs that does one thing well
* Can be combined in many ways
* Piping command means chaninig output from to input to another


---

## Navigation

* The *file system* organizes data into files and directories (folders)
* Directories are special files that are contains of other files
* Often called a file tree
* The begining of the tree is called the root "/"

<div class="row">
<div class="col-md-6">
<img class="img-responsive" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRajiMVifhNZj_GfkJ53S7AfxQIm330z6hIiYi19hKt6jMWTNgyzg"> 
<ul>
<li> Directories are branches</li>
<li> Files are leaves</li>
</ul>
</div>
<div class="col-md-6">
<img class="img-responsive" src="https://docs.oracle.com/cd/B19306_01/backup.102/b14236/img/obref001.gif"> 
<ul><li> Inverted tree</li></ul>
</div>
</div>

???

* Files names often have a dot, the latter part is the extension 
* signifies type of file
* convention not requirement

---

## Getting help

```
$ help
GNU bash, version 4.4.7(1)-release (x86_64-pc-linux-gnu)
These shell commands are defined internally.  Type `help' to see this list.
Type `help name' to find out more about the function `name'.
Use `info bash' to find out more about the shell in general.
Use `man -k' or `info' to find out more about commands not in this list.

A star (*) next to a name means that the command is disabled.

 job_spec [&]                            history [-c] [-d offset] [n] or hist>
 (( expression ))                        if COMMANDS; then COMMANDS; [ elif C>
 . filename [arguments]                  jobs [-lnprs] [jobspec ...] or jobs >
 :                                       kill [-s sigspec | -n signum | -sigs>
 [ arg... ]                              let arg [arg ...]
 [[ expression ]]                        local [option] name[=value] ...
 alias [-p] [name[=value] ... ]          logout [n]
 bg [job_spec ...]                       mapfile [-d delim] [-n count] [-O or>
 bind [-lpsvPSVX] [-m keymap] [-f file>  popd [-n] [+N | -N]
 break [n]                               printf [-v var] format [arguments]
 builtin [shell-builtin [arg ...]]       pushd [-n] [+N | -N | dir]
 caller [expr]                           pwd [-LP]
 case WORD in [PATTERN [| PATTERN]...)>  read [-ers] [-a array] [-d delim] [->
 cd [-L|[-P [-e]] [-@]] [dir]            readarray [-n count] [-O origin] [-s>
 command [-pVv] command [arg ...]        readonly [-aAf] [name[=value] ...] o>
 compgen [-abcdefgjksuv] [-o option] [>  return [n]
 complete [-abcdefgjksuv] [-pr] [-DE] >  select NAME [in WORDS ... ;] do COMM>
 compopt [-o|+o option] [-DE] [name ..>  set [-abefhkmnptuvxBCHP] [-o option->
 continue [n]                            shift [n]
 coproc [NAME] command [redirections]    shopt [-pqsu] [-o] [optname ...]
 declare [-aAfFgilnrtux] [-p] [name[=v>  source filename [arguments]
 dirs [-clpv] [+N] [-N]                  suspend [-f]
 disown [-h] [-ar] [jobspec ... | pid >  test [expr]
 echo [-neE] [arg ...]                   time [-p] pipeline
 enable [-a] [-dnps] [-f filename] [na>  times
 eval [arg ...]                          trap [-lp] [[arg] signal_spec ...]
 exec [-cl] [-a name] [command [argume>  true
 exit [n]                                type [-afptP] name [name ...]
 export [-fn] [name[=value] ...] or ex>  typeset [-aAfFgilnrtux] [-p] name[=v>
 false                                   ulimit [-SHabcdefiklmnpqrstuvxPT] [l>
 fc [-e ename] [-lnr] [first] [last] o>  umask [-p] [-S] [mode]
 fg [job_spec]                           unalias [-a] name [name ...]
 for NAME [in WORDS ... ] ; do COMMAND>  unset [-f] [-v] [-n] [name ...]
 for (( exp1; exp2; exp3 )); do COMMAN>  until COMMANDS; do COMMANDS; done
 function name { COMMANDS ; } or name >  variables - Names and meanings of so>
 getopts optstring name [arg]            wait [-n] [id ...]
 hash [-lr] [-p pathname] [-dt] [name >  while COMMANDS; do COMMANDS; done
 help [-dms] [pattern ...]               { COMMANDS ; }
```

---
### Manual pages

```
$ man echo
ECHO(1)                          User Commands                         ECHO(1)

NAME
       echo - display a line of text

SYNOPSIS
       echo [SHORT-OPTION]... [STRING]...
       echo LONG-OPTION

DESCRIPTION
       Echo the STRING(s) to standard output.

       -n     do not output the trailing newline

       -e     enable interpretation of backslash escapes

       -E     disable interpretation of backslash escapes (default)

       --help display this help and exit

       --version
              output version information and exit

       If -e is in effect, the following sequences are recognized:

       \\     backslash

       \a     alert (BEL)

       \b     backspace

       \c     produce no further output

       \e     escape

       \f     form feed

       \n     new line

       \r     carriage return

       \t     horizontal tab

       \v     vertical tab

       \0NNN  byte with octal value NNN (1 to 3 digits)

       \xHH   byte with hexadecimal value HH (1 to 2 digits)

       NOTE: your shell may have its own version of echo, which usually super‐
       sedes the version described here.  Please refer to your  shell's  docu‐
       mentation for details about the options it supports.

AUTHOR
       Written by Brian Fox and Chet Ramey.

REPORTING BUGS
       GNU coreutils online help: <http://www.gnu.org/software/coreutils/>
       Report echo translation bugs to <http://translationproject.org/team/>

COPYRIGHT
       Copyright  ©  2016  Free Software Foundation, Inc.  License GPLv3+: GNU
       GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
       This is free software: you are free  to  change  and  redistribute  it.
       There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       Full documentation at: <http://www.gnu.org/software/coreutils/echo>
       or available locally via: info '(coreutils) echo invocation'

GNU coreutils 8.26                March 2017                           ECHO(1)
```
---

## Looking around

* **prompt** (*noun*) an act of encouraging a hesitating speaker. (Wikipedia)


* **REPL** read-execute-print-loop



{% if False %}
<div class="col-md-12">
<div class="embed-responsive embed-responsive-16by9">
<iframe src="https://localhost:4200"></iframe>
</div>
</div>
{% endif %}
<div class="col-md-6">
<ul>
<li><tt>pwd</tt></li>
<li><tt>cd</tt></li>
</ul>
</div>
<div class="col-md-6">
<li><tt>ls</tt></li>
<li><tt>cat</tt></li>
</div>

---



???

What do you see
- a dollar sign and a blinking square
- the dollar sign is a prompt asking for input
- the blinking square is a cursor
- try changing the prompt PS1=

The REPL bash
- enter a word
- computer finds a program that matches that word
- runs that program
- prints result
- ask for more

What happens if you type something wrong

Where do we start?
- whatabout `help`
- whatabout hello. command for printing is...`echo`
- terminal shortcuts? ^A ^E ^P ^L

questions we may want to ask
- `whoami`
- where are we?  `pwd` print working directory
    - the first directory after logging is called home directory
    - HOME is an environment variable
    - ~ is an alias for home
    - ~user is an alias for user's home
    - *current working directory* the default director our computer things we
      want to work with when running programs

- what's in here? `ls`
    - long format
        - file type - permissions - owner - size - date (of last modification)
    - hidden files
    - recursive
    - arguments/ defaults
    - what is '.' and '..'?
    - *try invalid argument*

* commands taking arguments/parameters
* commands with options single or double dash
* demonstrate tab completion


---
## Moving around

* *cd* - change directory
* shortcuts: 
	- ~ (home) 
	- . (current directory) 
	- .. (parent directory)
	
    
* relative/absolute path of a file 

Example

```
/home/guest/dir1  # <- current directory
└── file1
/home/guest/dir2
└── file2
```
* You are in dir1 referencing file2
* absolute path: `/home/guest/dir2/file2`
* relative path: `../dir2/file2`



{% if False %}
<div class="col-md-9">
<div class="embed-responsive embed-responsive-4by3">
<iframe src="https://localhost:4200"></iframe>
</div>
</div>
{% endif %}

???

* cd (without argument)
* cd dir (argument)
A useful command is `cd -` if you swap between two different directories

* relative pathds `cd ../Music`
* absolute paths `cd /home/guest/Music
* what is a path
    * path of a filename
        * generally a sequence of names in the file tree to reach a specific file
        * names are separated by a forward slash
        * absolute path starts from the root
        * relative paths starts from current . (or ..)
    
---

## Working with files and direcories


* `mkdir` create directory
* `rmdir` remove directory
* `nano file` edit/create a file
* `cat` print contents of files
* `rm` remove file


{% if False %}
<div class="col-md-9">
<div class="embed-responsive embed-responsive-4by3">
<iframe src="https://localhost:4200"></iframe>
</div>
</div>
{% else %}
```
$ mkdir thesis
```
{% endif %}

???
15 min

* create del files  and direcories
* `mkdir thesis`


---

### Special characters

* `>`: redirect (screen) output
	```$ ls > filelist```
* `<`: redirect (terminal) input
    ```$ cat <```
* `|`: piping (passing output to input) `$ cat file | sort`
* `*` wildcard (matches anything) `$ ls *.txt`
* `?` wildcard (matches any single character) `$ ls ?.txt`
* `[]` selection


```
$ ls h*.txt
hello.txt  hi.txt  ho.txt  h.txt  hx.txt
$ ls h?.txt
hi.txt ho.txt hx.txt
$ ls h[io].txt
hi.txt ho.txt

```
---
## Repetition

* execute same code several times with small variations
* loop (for-loop, do-loop)


{% if False %}
<div class="col-md-9">
<div class="embed-responsive embed-responsive-4by3">
<iframe src="https://localhost:4200"></iframe>
</div>
</div>
{% else %}
from 
```
goostats NENE01729A.txt stats-NENE01729A.txt
goostats NENE01729B.txt stats-NENE01729B.txt
goostats NENE01736A.txt stats-NENE01736A.txt
goostats NENE01751A.txt stats-NENE01751A.txt
goostats NENE01751B.txt stats-NENE01751B.txt
goostats NENE01812A.txt stats-NENE01812A.txt
goostats NENE01843A.txt stats-NENE01843A.txt
...
```
to
```
for txt in NE*[AB].txt
do
goostats $txt stats-$txt
done
```
{% endif %}


???
* explain loop variable/loop value

* exercise: backup a lot of files
* `cp *.dat *.dat.bkp`
* with >2 args, last must be a directory
* avoid spaces in filenames
* `for f in a file; do echo $f; done`

* The example:
    - run goostat on each of the files

* build up the loop in steps

* history commands
* history
* !! !$

* sample loop to file which overwrites/appends
* dry run with echo
* nested loop

---

## Branching: `if` statements

Control characters

* `==`: equality
* `!=`: inequality
* `-r` existing (about files)
* `-x` executable (about files)
* `-d` existing directory 

```
$ if [ $a == "b" ]
$ then
$ echo yes
$ else
$ echo no
$ fi
yes
```

Shortcut control characters

* `&&` continue if ok (exit status zero)
* `||` continue if not ok (exit status non-zero)

---

##  Scripts

* Save bash commands in a file
* make the file executable
* execute file with  `bash file` or `./file`
* put it in a directory in your `PATH`

---


### Bash reference summary

http://swcarpentry.github.io/shell-novice/reference/
