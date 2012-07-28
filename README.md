dotsync
=======

dotsync keeps your local dotfiles in sync with a git repository and keeps 
multiple remote machines in sync, either with them pulling from the git 
repo or pushed via rsync

Master servers can be assigned, for cases where groups of machines are 
behind firewalls or only accessible from a certain location.

Requirements
------------

dotsync assumes that you have ssh setup correctly, with ssh-agent and configs
for correct usernames etc, if you can 'ssh hostname' it probably wont work 
and if your asked for passwords it will take hours with any number of machines.

Installation
------------

If you already have your dotfiles in a git repo...

    cd ~/.dotfiles
    git submodule add git@github.com:dotphiles/dotsync.git
    git submodule --init update

If you dont...

Fork the main project on [github](https://github.com/dotphiles/dotphiles)

    git clone --recursive git@github.com:*username*/dotphiles.git ~/.dotfiles

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
-----

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
-------------

`~/.dotsyncrc`

This config determines which hosts to sync, how, where from and which 
dotfiles to symlink into your homedir. 

This file can be included in the repo, and dotsync will use it if its not 
already symlinked.

See *templates/dotsyncrc*

`~/.dotfiles/.gitignore`

Controls which files are ignored from being added to the git repo, add any
temporary and 'secret' files here.

See *templates/gitignore*

`~/dotfiles/.rsyncignore`

Controls which files are ignored when rsyncing a remote host, add any temporary
and 'secret' files here.

See *templates/rsyncignore*

Issues
------

If you not sure, keep an ssh session open to any remote machines, in case
it wipes your ssh keys but should be safe.

Existing files will be backed up in ~/.backup/dotfiles or ~/.backup/dotfiles.old

Contribute
----------

This project would not exist without all of its users and [contributors][1].

If you have ideas on how to make the configuration easier to maintain or
improve its performance, do not hesitate to fork and send pull requests.

### Issue Reporting

   - Check that the [issue][2] has not already been reported.
   - Check that the [issue][2] has not already been fixed in the latest code.
   - Open an [issue][2] with a clear title and description in grammatically correct,
     complete sentences.

### Pull Request

   - Read [how to properly contribute to open source projects on GitHub][3].
   - Use a topic branch to easily amend a pull request later, if necessary.
   - Write [good commit messages][4].
   - Squash commits on the topic branch before opening a pull request.
   - Use the same coding style and spacing.
   - Open a [pull request][5] that relates to but one subject with a clear
     title and description in gramatically correct, complete sentences.

License
-------

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

[1]: https://github.com/dotphiles/dotphiles/contributors
[2]: https://github.com/dotphiles/dotphiles/issues
[3]: http://gun.io/blog/how-to-github-fork-branch-and-pull-request
[4]: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[5]: https://help.github.com/articles/using-pull-requests

