# Introduction #

Git-related tips (mostly my workspace for remembering commands)

# To bring in changes from a cloned repository into the main repository #

1. Clone the main repository.
> `git clone https://konigsberg@code.google.com/a/eclipselabs.org/p/workspacemechanic/`

2. Add the other repository as a remote to your clone repository.

> `git remote add <name> URL`
> > e.g.

> `git remote add stevemash https://code.google.com/a/eclipselabs.org/r/stevemash-devel/`

3. Fetch the contents of the other repository into yours.
> e.g. `git fetch stevemash`

> This will create a new branch in your local repository, e.g.
> `* [new branch]      master     -> stevemash/master`.

> You can verify this with `git branch -a`

4. Merge the changes that came from the remote branch into yours.
> `git merge stevemash/master`