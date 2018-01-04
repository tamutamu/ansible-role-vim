# ansible-role-vim

This role installs my personalized VIM.

## Requirements

To execute this role, superuser rights are needed as the build of VIM
requires to install some development libraries as well as some Python
libraries globally. Moreover, `git` has to be installed.

### MacOS
Make sure that the installed `python` interpreters are installed from
[here](https://www.python.org/downloads/mac-osx/). I had some issues
using the interpreters installed with `homebrew`.

## Example Playbook

Create a file `playbook.yml` with the following content:
```
- hosts: all
  tasks:
   - include_role:
       name: ansible-role-vim
     vars:
         - vim_install_dir: /home/user/myvim"
         - vim_set_alias: True
```
In the same directory as `playbook.yml` lives, create a directory
`roles`and clone the role repository with:

```
git clone https://github.com/windisch/ansible-role-vim roles/ansible-role-vim
```

## Variables

- `vim_install_dir`: States where VIM should be installed with `make install` after building it. Defaults to `/usr/local`
- `vim_set_alias`: If set to true, an alias is created in the users
    `.bashrc` for `vim`and `vimdiff` that point to this version of
    VIM. This option should be set to true the VIM binaries are
    installed to a directory not contained in
    `$PATH`. Defaults to false.
- `vim_lua_lib`: If you have a custom installation of `lua` and
    `luajit`, you should provide the path where `include/luajit-{version}/lua.h` can be found. 
