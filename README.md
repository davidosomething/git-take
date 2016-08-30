# git-take

Curry-style command to `git checkout` files


| Name          | Link     |
| ------------- | -------- |
| Project Home: | [https://github.com/davidosomething/git-take](https://github.com/davidosomething/git-take)

## About

Remembers the last branch you called `git take` with (persistes across sessions 
via storage in local git config), and provides a shortcut to
`git checkout BRANCH FILE`.

## Installation

- Add the `git-take` file somewhere in your path, e.g. `/usr/local/bin/`

### via zplug

```sh
zplug "davidosomething/git-take",   as:command
```

## Usage

From command line execute:

```sh
git take BRANCH FILENAME
```

This will essentially call

```sh
git checkout BRANCH FILENAME
```

but with the added benefit that it remembers the `BRANCH` on future calls.

Then, you can call

```sh
git take SOMEOTHERFILE
```

while will automatically assume you want `SOMEOTHERFILE` from the previously
specified `BRANCH` -- e.g.

```sh
git checkout BRANCH SOMEOTHERFILE
```

### Use cases

Sometimes I start a feature branch and find some bugs that I fix in that branch.
Those bug fixes should really go into a bugfix branch and be integrated
separately. So I would have:

1. `git checkout -b feature` to start working on a feature (topic) branch.
1. Fix up some bugs that I discover in `fixedfile1` and `fixedfile2`
1. `git checkout bugfix master` to create a new clean branch off of master.
1. `git take feature fixedfile`
1. Using the shortcut I can now `git take fixedfile2` without having to re-type
   the branch name (and `git take fixedfile3`, etc.)
1. `git commit` to the `bugfix` branch (or `git reset` and `git add -p` to
   patch in)

----

MIT Licensed

Copyright (c) 2015 David O'Trakoun <me@davidosomething.com>


