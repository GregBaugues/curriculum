# Bash Profile

### Projected Time

Example: 30-45 minutes

### Prerequisites

Here are links to lessons that should be completed before this lesson:

- [Command Line Interface](command-line/command-line-inteface.md)
- [Command Line Advanced](command-line/command-line-advanced.md)

### Motivation

Learn about how to customize a computer's environment 

### Objectives

**Participants will be able to:**.
- Export environmental variables to make them always available when they open a terminal shell.
- Add a file to the `$PATH` environmental variable.
- Change the terminal prompt
- Create an alias 


### Environmental Variables
Environmental variables are available whenever you open up a terminal shell. Your system
already includes many useful ones. For example `$HOME`. You can see that it is the path to 
your user's home directory if you "echo" it. Type `echo "$HOME"` and you'll see something like `/Users/david`. 
You can combine the variable with other commands like `cd $HOME` to change to your home directory. 

You can add your own environmental variables. 
Make a directory called scripts in our home directory. `mkdir $HOME/scripts`. 
Open `~/.profile` and add the following: `export SCRIPTS="$HOME/scripts"`. 
The export command is saying that you want to make `SCRIPTS` available anytime time .profile file is loaded. Since
.profile is loaded each time you open up new terminal shell its always available.
Close the shell and open a new terminal shell. 
To use an environmental variable you need to  prepend it with the dollar sign. 
Change your directory to scripts using your environmental variable: `cd $SCRIPTS`

### The $PATH Environmental Variable

The PATH environmental variable is a collection of files that are always available without needing to `source`
them directly. Type the follow command and hit enter: `echo $PATH`.
You will see a list of paths separated by a colon (you may have different results):
`/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin`. 

A useful thing to do is add files to your PATH environmental variable so they are available at anytime.
- First let's make simple script inside of `~/scripts` called `hello_world`
- Copy the following:
```bash
#!/bin/bash
echo "HELLO WORLD"
```
- Next make the file executable: `chmod a+x ~/scripts/hello_world`
- Let's add line to our `.profile` file: `export PATH=$PATH:$HOME/scripts`. What this says is that everytime we open
a terminal shell all of the files that are inside of `$HOME/scripts` which is the same as `~/scripts` can be called
from anywhere. 
- Save & open a new Terminal window or `source ~/.profile`
type the following to demonstrate: `hello_world` and you will see HELLO WORLD. It doesn't matter where you are at in
the file system because you've added the file's directory, `scripts` to your path so its always available to you. Lots
of helpful libraries are written using scripts in this way.

### Aliases

It's often helpful to make commands for yourself that are short cuts. For example what if you want to change to
your directory but you don't want to type `cd ~/scripts`. What if you could just type `cdscr` instead? Let's make a file
called `aliases` in our scripts folder. 
type the following:
`alias cdscr='cd "$HOME/scripts"'`

Next let's add the following to our `.profile`. 
```bash
source "$HOME/scripts/aliases"
```
When we type source and a file after it, it's saying, import all of the aliases in our file so we can call them
by name no matter where we are in our file system. That's why we do the same when we make changes to our `.profile`. 
When we open a new terminal window after changing our `.profile` the system essentiall calls `source .profile` before
we do anything. 

Let's test our alias.
- Save & open a new Terminal window or `source ~/.profile` 
- type `cdsrc` and hit enter. You should now be in `~/scripts`


### Change the terminal prompt
You can change the value of your system's environmental files to change how your termimal prompt appears.
The $PS1 variable sets what you see. 
Add the following to your `.profile` change what your prompt displays: `export PS1="\u@\h "`

Save & open a new Terminal window or `source ~/.profile` to reload this. Notice how the prompt now displays 
something simliar to `david@Davids-MacBook-Pro` now.

More info: [how-to-customize-your-terminal-prompt](http://osxdaily.com/2006/12/11/how-to-customize-your-terminal-prompt/)


### Independent Practice
[BASH Programming - Introduction HOW-TO](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

