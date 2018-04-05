# GitSync
Sync git repos across machines

# One Line Install
$ `wget https://raw.githubusercontent.com/amankhoza/gitsync/master/gitsync && chmod +x gitsync && sudo mv gitsync /usr/bin/`

# Pre-requisites
Your remote machine must be set up to accept SSH connections (you can Google how to do this).

# Initial Setup
Before you can run `gitsync` you need to make a config file in your home directory. 

The path of this config file should be `~/.gitsync/<repo_name>/config` (replace <repo_name> with the name of the repo you want to sync)

The config file should contain the following two lines:

```
remote_host="<ip_address_of_remote_machine>"
remote_dir="<full_path_of_repo_on_remote_machine>"
```

Also to make things easier and prevent you from continually typing in your password for SSH, apend your public SSH key to the remote machines authorized_keys file, this is located at `~/.ssh/authorized_keys`

# Usage
cd into the git repo you want to sync with your remote machine and run:

`gitsync`

This will send any commits you have on your local machine to the remote machine.

(Useful for when you work with two machines or develop on one and build on the other etc.)
