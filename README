dotsync
=======

dotsync keeps your local dotfiles in sync with a git repository and keeps 
multiple remote machines in sync, either with them pulling from the git 
repo or pushed via rsync

Master servers can be assigned, for cases where groups of machines are 
behind firewalls or only accessible from a certain location.

Requirements
============

dotsync assumes that you have ssh setup correctly, with ssh-agent and configs
for correct usernames etc, if you can 'ssh hostname' it probably wont work 
and if your asked for passwords it will take hours with any number of machines.

Installation
============

If you already have your dotfiles in a git repo...

    cd ~/.dotfiles
    git submodule add git@github.com:dotphiles/dotsync.git
    git submodule --init update

If you dont...

Fork the main project on [github](https://github.com/dotphiles/dotfiles)

    git clone --recursive git@github.com:*username*/dotfiles.git ~/.dotfiles

Copy your dotfiles into ~/.dotfiles without the dot...

List your dotfiles in dotsyncrc without the dot...

Checkin your changes...

    git commit -a -m "Initial Commit"
    git push

Then, symlink your dotfiles into place...

    ~/.dotfiles/dotsync/bin/dotsync -L

See the *Configuration* section for configuration info.

Then add hosts into dotsyncrc and `dotsync -I -H hostname` (at your own risk!)

Usage
=====

    -I          - Initialise a machine using dotsync
    -L          - Symlink available dotfiles into $HOME
    -u          - Update to the latest copy of dotfiles
    -U          - Update to the latest copy of dotfiles inc submodules
    -P          - Push any local changes back to the repo (git only)
    -H host     - Perform action against host listed in config, can be 'ALL'
    -a          - Updates dotfiles on all known machines
    -A          - Updates dotfiles and submodules on all known machines
    -r          - Use rsync instead of git
    -f conf     - Config file, defaults to '~/.dotsyncrc' or '$DOTSYNCRC'
    -d dotfiles - Location of dotfiles, defaults to '~/.dotfiles'
    -l          - List configured hosts and dotfiles to symlink
    -v          - Verbose
    -h          - Show help message

Configuration
=============

`~/.dotsyncrc`

This config determines which hosts to sync, how, where from and which 
dotfiles to symlink into your homedir. 

This file can be included in the repo, and dotsync will use it if its not 
already symlinked.

See dotsyncrc-example

`~/.dotfiles/.gitignore`

Controls which files are ignored from being added to the git repo, add any
temporary and 'secret' files here.

See gitignore-example

`~/dotfiles/.rsyncignore`

Controls which files are ignored when rsyncing a remote host, add any temporary
and 'secret' files here.

See rsyncignore-example

Issues
======

Probably lots!

If you not sure, keep an ssh session open to any remote machines, in case
it wipes your ssh keys but should be safe.

Existing files will be backed up in ~/.dotfiles/backups or ~/.dotfiles.backup

License
=======

Copyright (c) 2012 Ben O'Hara <bohara@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
