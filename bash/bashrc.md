# set up the prompt 
PROMPT_COMMAND=setprompt
function setprompt
{
	local LAST_COMMAND=$? # Must come first!

	# Define colors
	local LIGHTGRAY="\033[0;37m"
	local WHITE="\033[1;37m"
	local BLACK="\033[0;30m"
	local DARKGRAY="\033[1;30m"
	local RED="\033[0;31m"
	local LIGHTRED="\033[1;31m"
	local GREEN="\033[0;32m"
	local LIGHTGREEN="\033[1;32m"
	local BROWN="\033[0;33m"
	local YELLOW="\033[1;33m"
	local BLUE="\033[0;34m"
	local LIGHTBLUE="\033[1;34m"
	local MAGENTA="\033[0;35m"
	local LIGHTMAGENTA="\033[1;35m"
	local CYAN="\033[0;36m"
	local LIGHTCYAN="\033[1;36m"
	local NOCOLOR="\033[0m"

	# Show error exit code if there is one
    # general usage, I removed error indications

	# User and server
	local SSH_IP=`echo $SSH_CLIENT | awk '{ print $1 }'`
	local SSH2_IP=`echo $SSH2_CLIENT | awk '{ print $1 }'`
	if [ $SSH2_IP ] || [ $SSH_IP ] ; then
		PS1="\[${RED}\]\u@\h"
	else
		PS1="\[${LIGHTGREEN}\]\u"
	fi

	# Current directory
    PS1+="\[${LIGHTGREEN}\]:\[${LIGHTGREEN}\]\w\[${LIGHTGREEN}\]){=_=}(:\[${LIGHTGREEN}\]\$"
	PS1+="\[${LIGHTGREEN}\] "
}

# My alias
alias cp='cp -i'
alias mv='mv -i'
alias cls='clear'
alias apt-get='sudo apt-get'
alias vi='vim'
alias svi='sudo vim'

# directory alias
alias cd..='cd ..'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias odd='cd $OLDPWD'


#listing alias
alias la='ls -a'
alias ll='ls -ali'
alias lx='ls -lXBh' # sort by extension
alias lk='ls -lSrh' # sort by size
alias lc='ls -lcrh' # sort by change time
alias lu='ls -lurh' # sort by access time
alias lr='ls -lRh' # recursive ls
alias lt='ls -ltrh' # sort by date
alias lm='ls -alh |more' # pipe through 'more'
alias lw='ls -xAh' # wide listing format
alias labc='ls -lap' #alphabetical sort
alias lf="ls -l | egrep -v '^d'" # files only
alias ldir="ls -l | egrep '^d'" # directories only


# Search command line history
alias h="history | grep "

# Search running processes
alias p="ps aux | grep "
alias topcpu="/bin/ps -eo pcpu,pid,user,args | sort -k 1 -r | head -10"

# Search files in the current folder
alias f="find . | grep "


# Alias's for archives
alias mktar='tar -cvf'
alias mkbz2='tar -cvjf'
alias mkgz='tar -cvzf'
alias untar='tar -xvf'
alias unbz2='tar -xvjf'
alias ungz='tar -xvzf'


# Alias for python on Mac
alias python='python3'


# Symbolic Links 
# ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/sublime


