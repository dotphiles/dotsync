Contribute
----------

This project would not exist without all of its users and [contributors][1].

If you have ideas on how to make the configuration easier to maintain or
improve its performance, do not hesitate to fork and send pull requests.

If you want to contribute to the project, check out the list of open [issues][2]

You can:

 - raise an issue
 - suggest a feature

If you would like to contribute code to the project:

  1. A bit of background reading:
    - [Setting up Git for Windows and connecting to GitHub][3]
    - [The Simple Guide to Git][4]
    - [How to GitHub: Fork, Branch, Track, Squash and Pull Request][4]
    - [Write good commit messages][11].
  2. [Fork the repository][5]
  3. Make some changes to the code base
  4. [Send us a Pull Request once you're happy with it][6]

We'll do a bit of a code review before accepting your patch.

### Git Flow

We use the Git Flow branching model, [first described][7] by [nvie][8],
so dotsyncs's `master` branch moves on only at specific points, when we're
really sure we want to promote something to production.

**Use of Git Flow is not required for contributing to dotsync**, particularly
if you're submitting a bug-fix or small feature.  Its use is recommended for
larger changes where `develop` might move on whilst you're completing your work.

#### Configuring Git Flow

There is a set of [helper scripts][9] that will work on both Unix-based
operating systems and Windows.  Follow the appropriate
[installation instructions][10] for your operating system, and configure your
working copy repository for use with Git Flow by typing `git flow init`.
Accept all the default options to the questions that it asks you.

#### Using Git Flow

Pick a feature or bug to work on and create a new branch for that work by
typing `git flow feature start <featurename>`.  This will create you a new
*feature branch* for your work called `feature/<featurename>`, and you can use
git as usual from this point.

Once your feature is finished, type `git flow feature publish <featurename>`.
This will copy the *feature branch* to your `origin` repository on GitHub and
you will then be able to submit a pull request to have it merged into dotsync's
own `develop` branch.

**Note: do not use `git flow feature finish <featurename>`!**

This will automatically merge your *feature branch* back into `develop` and
delete the *feature branch*, making it harder for you to submit your pull
request.

If you wish to update your published feature branch after the initial publish,
use a regular `git push origin feature/<featurename>`.  This will also update
your pull request if you have one open for that branch.

If you find dotsync's `develop` branch has moved on, and you need/want to take
advantage of the changes made there, you can update your feature branch as
follows:

  1. Ensure you have a remote configured for the upstream repository.

       git remote add upstream git://github.com/dotphiles/dotsync.git

  2. Update your local repository with the upstream refs.

        git pull upstream develop:develop`

  3. Rebase your feature branch on top of the new `develop`.

        git flow feature rebase <featurename>

There is a lot of help available for Git Flow, which can be accessed by typing
`git flow feature help`.

[1]: https://github.com/dotphiles/dotsync/contributors
[2]: https://github.com/dotphiles/dotsync/issues
[3]: http://help.github.com/win-set-up-git/
[4]: http://rogerdudler.github.com/git-guide/
[5]: http://help.github.com/fork-a-repo/
[6]: http://help.github.com/send-pull-requests/
[7]: http://nvie.com/posts/a-successful-git-branching-model/
[8]: http://www.twitter.com/nvie
[9]: https://github.com/nvie/gitflow
[10]: https://github.com/nvie/gitflow/wiki/Installation
[11]: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html

