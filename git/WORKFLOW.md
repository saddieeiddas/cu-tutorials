Git WorkFlow
================================================================================

This will outline how to contribute to Camelot Unchained UI Repositories
following the recommended git workflow.

--------------------------------------------------------------------------------

Creating a Fork
--------------------------------------------------------------------------------

You will first need to create a fork of the repository you wish to contribute to

This can be achieved by visiting the repository in question and clicking the
fork button (top right).

This will create a fork of the repository under your user in github.

Example:

> https://github.com/CUModSquad/cu-core

Will be forked to:

> https://github.com/YOU/cu-core

This will create a link between your version of `cu-core` and the original
repository (AKA `upstream`) allowing you to create Pull Requests (PR's)

--------------------------------------------------------------------------------

Setting Up a Local Copy
--------------------------------------------------------------------------------

The next step is to checkout a local copy of your fork.

You can achieve this by running the following:

```
git clone https://github.com/YOU/cu-core.git
# or if you want to save your username use
# git clone https://YOU@github.com/YOU/cu-core.git
```

This will setup a working copy of your fork, which has a remote called `origin`.

This is where you will be working on your contribution.

--------------------------------------------------------------------------------

Adding the Upstream Repository
--------------------------------------------------------------------------------

You will now want to connect the upstream repository (original repository you
cloned).

Run the following from your local copy:

```
git remote add upstream https://github.com/CUModSquad/cu-core
# make sure the url is correct for the repository you forked
```

You can now list all the remotes with the following command:

```
git remote -v
# origin   https://YOU@github.com/YOU/cu-core.git (fetch)
# origin   https://YOU@github.com/YOU/cu-core.git (push)
# upstream https://github.com/CUModSquad/cu-core.git (fetch)
# upstream https://github.com/CUModSquad/cu-core.git (push)
```

--------------------------------------------------------------------------------

Synchronizing Your Fork with Upstream
--------------------------------------------------------------------------------

You will now want to synchronize your fork with the upstream.

> This is useful when other changes are merged into the upstream repository

Run the following:

```
git checkout master
git pull upstream master
git push origin master
```

This will get all the latest changes from upstream, and push them to your fork.

--------------------------------------------------------------------------------

Creating a Contribution
--------------------------------------------------------------------------------

Now you have a local copy of your fork, you might want to make changes to be
contributed back to the upstream repository.

The most important step here is to create a new branch for your changes.

** Before you do this, ensure you have synchronized your local copy and fork**

```
git checkout master
git checkout -b my-new-feature
```

You will now be on a new branch ready to develop your changes.

Once your changes are ready you will want to commit your changes and push to your
fork.

```
git add --all
git commit -m "my commit message here"
git push -u origin my-new-feature
```

This will push all your code to a branch called `my-new-feature` on your fork.

--------------------------------------------------------------------------------

Creating a Pull Request
--------------------------------------------------------------------------------

Once you have a contribution on your fork, you may want to create a Pull Request
to get your contribution included in the upstream repository.

On github you can navigate you the feature branch in your repository and click
the "Pull Request" button, which will allow you to create a PR.

You are able to select the destination Repository/Branch and the source (your
own Repository/Branch).

Once your pull request is created, it will be reviewed by others.


--------------------------------------------------------------------------------

Synchronizing an Existing Feature Branch with Upstream
--------------------------------------------------------------------------------

Once you have developed a contribution, you might need to pull in updates that
have been merged into upstream.

You can do that as follows:

**Note make sure you have commited(or stashed) all your work**

```
git checkout master
git pull upstream master
git push origin master
git checkout my-new-feature

git rebase master
```

You will be rebasing your feature branch to the latest commit from upstream.
This is essentially replaying all of your changes after all commits in the upstream
branch.

You may have to solve some conflicts during the rebase if there are changes in
files you have updated. If there are conflicts you will need to fix them and add
everything to the stage (note: you do not need to commit during a rebase, just
run `git rebase --continue`)

Your feature branch should now be synced with the upstream.

You will now want to push this to your fork.

```
git push origin my-new-feature
# The above should fail, as you will need to --force the push
git push origin my-new-feature --force
# be careful with the --force flag
```
