# backpack

backpack is a small wrapper around ssh.

It transfers a file simular to .bashrc to remote host, sources it and continues with normal ssh session.

Some highlights:

* works best as `alias ssh=backpack`
* won't create any files on remote hosts (even temporary)
* it is self-replicating and can be called again directly from remote host.
* tries to fallback to normal ssh when remote shell is not bash

Example of ~/.backpack file:
	
	PS1="\u \[\033[1;31m\]\h\[\033[0m\] \W "
	
	alias ssh=backpack
	alias l="ls -alah"
	alias juu="perl -MJSON::PP -E 'local \$/; say JSON::PP->new->pretty(1)->encode(decode_json(<>));'"
	
	human() {
		if [ $# -ne 0 ]; then
			numfmt --to=iec "$@"
		else
			cat | numfmt --to=iec "$@"
		fi
	}

	bind '"\e[A": history-search-backward'
	bind '"\e[B": history-search-forward'

	# I use st terminal, but probably there is no st.info
	TERM=xterm-256color

Also check simular project [sshrc](https://github.com/Russell91/sshrc).