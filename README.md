# GitSync
Sync git repos across machines

(Useful for when you work away from your main machine but still want to build on it or send commits to/from it)

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
First cd into the git repo you want to sync with your remote machine then run one of the following:

### See git status of local and remote machine
`gitsync status`

### Pull committed changes from remote to local machine
`gitsync pull`

### Push committed changes from local to remote machine
`gitsync push`

### Push all changes (including uncommitted changes) from local to remote machine and then run a build command
`gitsync push <build command in quotes using full paths for executables>`

This creates a temporary branch on the remote machine where changes are pushed to, the build command is run and the output is
displayed on local machine, then the temporary branch on the remote machine is deleted.

# How does it work?
Patches are created using `git format-patch` then sent over to / or pulled from remote machine via `scp`, patch is then applied
using `git am`
