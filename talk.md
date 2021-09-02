name: cover
<style>
    body {
        background: white }
    section {
        background: white;
        color: black;
        border-radius: 1em;
        padding: 1em;
        position: absolute;
        top: 50%;
        left: 50%;
        margin-right: -50%;
        transform: translate(-50%, -50%) }
</style>
<script type="text/javascript"
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
# The Bash shell

## 

BB2441 The shell


---

layout: false



* [The Bash shell](#cover)
    + [Learning objectives](#goals)
    + [What is a terminal](#terminal)
    + [Shell](#shell)
        - [What is a CLI](#cli)
        - [Graphical vs command-line interface](#cli)
        - [How do I start a  CLI](#startcli)
        - [Getting help](#startcli)
        - [Manual pages](#man)
    + [The file system](#navigation)
        - [Navigation](#navigation)
        - [A tree view of a file system](#navigation)
        - [Looking around](#looking)
        - [Moving around](#moving)
    + [Working with files and direcories](#files)
        - [Files](#files)
        - [Directories](#directories)
    + [Shell scripts](#scripts)
        - [Variables](#scripts)
        - [Logic](#logic)
    + [Summary](#summary)
        - [Commands used](#summary)
        - [Bash reference ](#summary)


---

name: goals
## Learning objectives

* Navigation in the file system
* Working with files
* Combining commands
* Repeating commands (looping)
* Choosing commands (branching)
* Finding stuff

---

<section>
<h2>What is a terminal?</h2>
</section>

---

name: terminal
## What is a terminal?


<img height="200" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/DEC_VT100_terminal.jpg/1013px-DEC_VT100_terminal.jpg">

--

<img height="200" src="https://c2.staticflickr.com/4/3029/2627291590_66060a771b_o.jpg">

???

If you google for terminal you may get images like this

A terminal is an end point of a computer facing the user

At the other end one could have the real computer filling a room like this

Now all of this is combined into this (laptop) and much more powerful

---
<section>
<h2>What is a shell?</h2>
</section>
---
name: shell

## Shell

* *In computing, a shell is a user interface for access to an operating system's
services.* 

* *It is named a shell because it is a layer around the operating system
kernel (Wikipedia)*

<img class="img-responsive" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTQrJeHObbV2Y-Drb7P3vXFHnYoO-bU3Ii7haw5vqT-2wTUE3yfMg">

* *It is a program running on the computer accepting user input*

* *A handful of different shell programs (dialects) exist*

    + Bourne shell (`/bin/sh`)
    + Bourne again shell (`/bin/bash`) - often default/de facto standard
    + C-shell (`/bin/csh`)
    + T-C-shell (`/bin/tcsh`)



---

<section>
<h2>What is a CLI?</h2>
</section>

---
name: cli
### What is a CLI?

* CLI = command-line interface
* GUI = graphical user interface


#### In practice

* terminal
* shell
* CLI

different names for the same thing

---
name: gui-cli

### Graphical vs command-line interface


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
* Piping command means chaining output from to input to another

---

<section>
<h2>How do I start a  CLI?</h2>
</section>

---
name: startcli

### How do I start a  CLI?

* Search for a program with the `terminal` (or similar)
* Start a terminal session in jupyter (see lab instruction)

--

~~~
$ █



~~~

* prompt (`$`): computer asking for input
* cursor ( `▒` ): where characters you type go in

---
<section>
<h2>How do I find help?</h2>
</section>
---

### Getting help

The `help` command

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
...
```

---
name: man

### Manual pages

The `man` command

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

...
```

---
~~~
$ echo Hello world!
Hello world!
$ echo "Hello world!"
Hello world!
$ echo 'Hello world!'
Hello world!
~~~
---
name: navigation

## The file system

### Navigation

* The *file system* organizes data into files and directories (folders)
* Directories are special files that are contains of other files
* Often called a file tree
* The beginning of the tree is called the root "/"

<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRajiMVifhNZj_GfkJ53S7AfxQIm330z6hIiYi19hKt6jMWTNgyzg"> 


* Directories are branches
* Files are leaves

---
name: file-tree

### A tree view of a file system

<img src="https://docs.oracle.com/cd/B19306_01/backup.102/b14236/img/obref001.gif"> 


???

* Files names often have a dot, the latter part is the extension 
* signifies type of file
* convention not requirement

---

<section>
<h2>Where am I?</h2>
</section>

---
name: looking

### Looking around

Concept of location: current/working directory

~~~
$ pwd 
/home/jane
$ ls
file1  file1.bak  file1.tmp  tmp
$ ls /home/pablo
file1 file1.bak file2
~~~
<img src="https://docs.oracle.com/cd/B19306_01/backup.102/b14236/img/obref001.gif" height=300> 

---
name: example

~~~
$ echo ~
/home/jane
$ echo ~pablo
/home/pablo
$ ls ../pablo
file1 file1.bak file2
~~~

<img src="https://docs.oracle.com/cd/B19306_01/backup.102/b14236/img/obref001.gif" height=250> 

Directory shortcuts
- ~ (home) 
- . (current directory) 
- .. (parent directory)

---
name: moving

### Moving around

* `cd` - change directory

~~~
$ cd ~pablo
$ pwd
/home/pablo
$ ls 
file1 file1.bak file2
~~~

<img src="https://docs.oracle.com/cd/B19306_01/backup.102/b14236/img/obref001.gif" height=250> 
---
<section>
<h2>How do I view/change/save text in files?</h2>
</section>
---
name: files

## Working with files and direcories

### Files

#### Saving output in a file

* redirection (>)
* redirection with append (>>)

~~~
$ echo "Hello" >  /tmp/saved
$ ls  >>  /tmp/saved
~~~
#### What is in the file?
~~~
$ cat /tmp/saved
Hello
file1
file1.bak
file2
~~~
---
name: edit

#### Edit a file with a text editor
~~~
$ nano /tmp/saved
~~~
~~~
  GNU nano 2.9.8                      /tmp/saved                                
____________________________________________________________________________

file1 file1.bak file2












^G Get Help  ^O Write Out ^W Where Is  ^K Cut Text  ^J Justify   ^C Cur Pos
^X Exit      ^R Read File ^\ Replace   ^U Uncut Text^T To Spell  ^_ Go To Line




~~~

#### Remove the file
~~~
$ rm /tmp/saved
~~~

---
name: directories

### Directories

#### Creating and removing dictionaries

* `mkdir` create directory
* `rmdir` remove directory

```
$ mkdir thesis
$ cd thesis
$ nano thesis.tex
...
```

~~~
$ cd ..
$ rmdir thesis
rmdir: failed to remove 'thesis': Directory not empty
$ rm -r thesis
~~~

* be careful with this command!
---

<section>
<h2>I want to rerun a set of commands many times. How?</h2>
</section>

---
name: scripts

## Shell scripts

* Save bash commands in a file
* make the file executable
* execute file with  `bash file` or `./file`
* put it in a directory in your `PATH`

---

### Save bash commands in a file

You use a text editor of your choice to write bash statements that are to be
executed together

### make the file executable

On a Linux system you can set different file permissions for different user
categories; the
permissions are readable (r), writeable (w) and executable (x),  and can be
defined for the owner, a user group, or for others. The output of an `ls`
command of an ordinary file looks typically like
~~~
$ ls -l document.md
-rw-r--r-- 1 user user 11224 aug 26 12:10 document.md
~~~
where the initial string shows the permissions for owner, group and others
respectively
~~~
 r w x   r w x   r w x
(owner) (group) (others)
~~~

---

### execute file with  `bash file` or `./file`

A bash script in the current directory may be executed with the file as an
argument to the bash interpreter
~~~
$ bash script
~~~
To execute a script in the current directory directly from the command line (i.e. typing only its name)
it has to be executable, and have an 'x' in the file permissions. You can set
the file permissions with the `chmod` command
~~~
$ ls -l script
-rw-r--r-- 1 user user 11224 aug 26 12:10 script
~~~
~~~
$ chmod +x script
$ ls -l script
-rwxr-xr-x 1 user user 11224 aug 26 12:10 script
$ ./script
~~~

---

### put it in a directory in your `PATH`

The `./script` notation specifies that you intend to run a script from the
current directory. You may type
~~~
$ script
~~~
without the directory part, without really knowing where it is, as long as it
is in a folder that is in the `PATH` shell environment variable

* **In the command line interface you run programs by typing the name of the program.**
* **When typing a program name the computer will go through a sequence of
  directories defined by `PATH` to look for an executable file by that name**

~~~
$ echo $PATH
/home/user/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
~~~

---

### Variables
* Scripts often make use of shell variables
* They are created on the fly by assignment 
~~~
var="some value"
~~~
* They are referenced with a dollar sign
~~~
echo $var 
~~~
    - prints `some value` to the screen

---
name: logic
### Logic

#### Repetition

* execute same code several times with small variations
* loop (for-loop, do-loop)


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


---
name: branching

#### Branching: `if` statements

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

---
name: example

#### Example
~~~
#backup.sh
for i in $(ls *$1*|grep -v bkp)
do
    if [ -f $i.bkp ]
    then
        mv $i.bkp $i.bkp2
    fi
    cp -v $i $i.bkp
done
~~~
What is happening?

--
* command line arguments enter the script as numeric variables (`$1`, `$2`, `$3`...,)
* `$0` is the name of the running script
* `ls *$1*` lists all files whose name contain the first argument
* the output is *piped* to `grep -v bkp` which excludes all files with `bkp`
* indentation is for readability but not required
* each matching file is copied (`cp`) to a new file with added extension `.bkp`
* in case that already exists the `bkp` file is moved (`mv`) to `.bkp2`
---

#### Shortcut control characters

* `&&` continue if ok (exit status zero)
* `||` continue if not ok (exit status non-zero)

#### List a file and its contents if it exists
~~~
$ ls /tmp/saved && cat /tmp/saved
/tmp/saved
file1 file1.bak file2
~~~
#### Create a new directory if it does not exist
~~~
$ ls /tmp/newdir || mkdir /tmp/newdir
~~~

---
name: summary

## Summary

### Commands used

* help
* man
* echo
* pwd
* ls
* for
* if
* cat
* rm
* mkdir
* rmdir

-- -

### Bash reference 

http://swcarpentry.github.io/shell-novice/reference/
