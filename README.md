# MY CUSTOM BASHRC FILE

This is an example of my `.bashrc` file. I made customizations as shown below:-

## HOW TO USE
Copy parts or all of the .bashrc file into your systems .bashrc file.

## 1. BEAUTIFY TERMINAL WITH COLORS AND RANDOM EMOJIS
### setting random emoji function
```sh 
EMOJI=(☀️️  😺 🐬 😸 🌠 🙊 🧜 😾 🐈 🦒 🦈 🐠 😿 🥀 🍒 🥂 🎻 🗡  ✔ ✖ ✳ ❇ 🤠 💍 😹 🍇 😻 🐧 😼 🔥 😽 🌷 🌴️️ 🙈 🤓 🙊)
# random emoji function
RANDOM_EMOJI(){
SELECTED_EMOJI=${EMOJI[$RANDOM % ${#EMOJI[@]}]};
echo $SELECTED_EMOJI;
} 
```
```sh
export PS1="\[\033[34m\]edit_name\[\e[m\] \[\033[33m\]$(RANDOM_EMOJI)\[\e[m\] \[\033[33m\]:\[\e[m\]\[\033[37m\]\w\[\e[m\]$\[\e[m\] ";
```

Add more customization as you feel fit.

## 2. GENERAL OPTIONS

```sh
# Prevent file overwrite on stdout redirection
# Use `>|` to force redirection to an existing file
set -o noclobber
# Automatically trim long paths in the prompt (requires Bash 4.x)
PROMPT_DIRTRIM=5
# Turn on recursive globbing (enables ** to recurse all directories)
shopt -s globstar 2> /dev/null

# Case-insensitive globbing (used in pathname expansion)
shopt -s nocaseglob;
```
## 3. SMARTER TAB-COMPLETION (Readline bindings)

```sh
# Perform file completion in a case insensitive fashion
bind "set completion-ignore-case on"

# Treat hyphens and underscores as equivalent
bind "set completion-map-case on"

# Display matches for ambiguous patterns at first tab press
bind "set show-all-if-ambiguous on"

# Immediately add a trailing slash when autocompleting symlinks to directories
bind "set mark-symlinked-directories on"
```
## 4. SANE HISTORY DEFAULTS
```sh
# Append to the history file, don't overwrite it
shopt -s histappend

# Save multi-line commands as one command
shopt -s cmdhist

# Record each line as it gets issued
PROMPT_COMMAND='history -a'

# Huge history. Doesn't appear to slow things down, so why not?

HISTSIZE=100000
HISTFILESIZE=100000

# Avoid duplicate entries
HISTCONTROL="erasedups:ignoreboth"

# Don't record some commands
export HISTIGNORE="&:[ ]*:exit:ls:bg:fg:history:clear"

# Use standard ISO 8601 timestamp
# %F equivalent to %Y-%m-%d
# %T equivalent to %H:%M:%S (24-hours format)
HISTTIMEFORMAT='%F %T '

# Enable incremental history search with up/down arrows (also Readline goodness)
# Learn more about this here: [http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/]
bind '"\e[A": history-search-backward'
bind '"\e[B": history-search-forward'
bind '"\e[C": forward-char'
bind '"\e[D": backward-char'
```


## 5. BETTER DIRECTORY NAVIGATION 

```sh
# Prepend cd to directory names automatically
shopt -s autocd 2> /dev/null

# Correct spelling errors during tab-completion
shopt -s dirspell 2> /dev/null

# Correct spelling errors in arguments supplied to cd
shopt -s cdspell 2> /dev/null

# This defines where cd looks for targets
# Add the directories you want to have fast access to, separated by colon
# Ex: CDPATH=".:~:~/projects" will look for targets in the current working directory, in home and in the ~/projects folder
CDPATH="."

# This allows you to bookmark your favorite places across the file system
# Define a variable containing a path and you will be able to cd into it regardless of the directory you're in
shopt -s cdable_vars

# append to the history file, don't overwrite it
shopt -s histappend
```


### credits
`[https://github.com/mrzool/bash-sensible]([https://github.com/mrzool/bash-sensible)`
