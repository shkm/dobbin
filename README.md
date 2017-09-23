# dobbin
A script managing workhorse.

## Description
Dobbin is a simple package manager for miscellaneous binaries and scripts. Given a git repository and a list of files, the repository will be cloned and the files symlinked to a central bin directory.

One benefit of this approach is that there's no need for projects to explicitly support Dobbin, e.g. with a `package.json` or something.

I wrote this primarily so I don't have to manually pull down various scripts into my dotfiles, and can instead store a simple list of those packages.

## Installation
Since Dobbin is just a script, you can use it to manage itself.

```sh
\curl -sS https://raw.githubusercontent.com/shkm/dobbin/master/dobbin | \
bash -s add https://github.com/shkm/dobbin dobbin
```

Now just add `$HOME/.dobbin/bin` to your `$PATH`.

## Usage

### `dobbin[ install]`
Installs packages listed in your `$HOME/.dobbin/package_list`.

### `dobbin add repo_url path [path...]`
Adds the package to your package list and installs it.

Each path passed is relative to the repository and will be symlinked into `$HOME/.dobbin/bin`.

### `dobbin remove repo_url`
__not implemented yet__

Removes the entire package from your package list.

This will remove the git repository and all symlinked files.

#### Example
`dobbin add https://github.com/shkm/dobbin dobbin`

### `dobbin update`
__not implemented yet__

Updates all packages in your package list, adding any symlinks where necessary.

### `dobbin clean`
__not implemented yet__

Removes any packages that aren't in your package list.

- When a package is no longer listed at all, the symlinks and repo will be deleted.
- When a package is in the list, but extraneous symlinks are detected, just those symlinks will be deleted.

### `dobbin edit`
__not implemented yet__

Opens the package list in your editor.

## TODO
- Implement a `help` command
- Implement `remove` command
- Implement `update` command
- Implement `clean` command
- Implement `edit` command
