# ansible-role-vim

This ansible role installs my personalized VIM.

## Requirements

To execute this role, superuser rights are needed as the build of VIM
requires to install some development libraries as well as some Python
libraries globally. Moreover, `git` has to be installed.

Typically, I use VIM inside of `tmux` and to make them work together,
some configurations to `tmux.conf` are needed to make them work
together perfectly. My [ansible-role-cmd-utils](https://github.com/windisch/ansible-role-cmd-utils) takes care of these configuration (and many more).

### MacOS

Make sure that the installed `python` interpreters are installed from
[here](https://www.python.org/downloads/mac-osx/). I had some issues
using the interpreters comming with `homebrew`.

## Example Playbook

Create a file `playbook.yml` with the following content:
```
- hosts: all

  roles:
    - {role: ansible-role-vim, vim_install_dir: /home/user/myvim, vim_set_alias: True}
```
In the same directory as `playbook.yml` lives, create a directory
`roles`and clone the role repository with:

```
git clone https://github.com/windisch/ansible-role-vim roles/ansible-role-vim
```

## VIM Configurations

After VIM is installed, the configuration is taken from 
[here](https://github.com/windisch/vim). This probably does not fits
you well. Feel free to clone any other vim configuration repo (have a
look at `vim_remote_git_config_repo` in the [variables](#variables)
section).


## Variables

- `vim_install_dir`: States where VIM should be installed with `make install` after building it. Defaults to `/usr/local`
- `vim_remote_git_config_repo`: URL of a cloneable git repository
    holding the configurations of vim. Assumes an `vimrc` to be there.
    Defaults to my configuration.
- `vim_set_alias`: If set to true, an alias is created in the users
    `.bashrc` for `vim`and `vimdiff` that point to this version of
    VIM. This option should be set to true the VIM binaries are
    installed to a directory not contained in
    `$PATH`. Defaults to false.
- `vim_lua_lib`: If you have a custom installation of `lua` and
    `luajit`, you should provide the path where `include/luajit-{version}/lua.h` can be found. 
