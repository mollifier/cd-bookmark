# cd-bookmark

## Synopsis
zsh plugin to bookmark directories to cd.

Inspired by [mokemokechicken post](http://qiita.com/mokemokechicken/items/69af0db3e2cd27c1c467) and shell script in the post.

This plugin is forked from the script. The original script is licensed under the [MIT License](http://mokemokechicken.mit-license.org/).

## How to set up

### Manually install

Put cd-bookmark and _cd-bookmark files somewhere in your $fpath and add the following line to your .zshrc:

```
autoload -Uz cd-bookmark
```

### Installing using Antigen
If you use [Antigen](https://github.com/zsh-users/antigen), add the following line to your .zshrc:

```
antigen bundle mollifier/cd-bookmark
```

You can set alias to this function.
e.g.

```
alias cdb='cd-bookmark'
```

## Usage


```
# 1st form
% cd-bookmark -a [BOOKMARK_ID]

# or
# 2nd form
% cd-bookmark [-c] BOOKMARK_ID

# or
# 3rd form
% cd-bookmark [-l]
```

In the 1st form, add current directory to bookmark with <var>BOOKMARK\_ID</var>.
<var>BOOKMARK\_ID</var> is used as a key in bookmark.

In the 2nd form, find directory by <var>BOOKMARK\_ID</var> and change directory to it. In this form, you can add relative path from bookmark real path at the end of BOOKMARK\_ID (see example below).

In the 3rd form, list current bookmark.

## Options
* `-a` <var>[BOOKMARK\_ID]</var>  add current directory to bookmark<br />
                                with no BOOKMARK\_ID, automatically use free ID number as BOOKMARK\_ID
* `-c` <var>BOOKMARK\_ID</var>   change directory which is identified by BOOKMARK\_ID
* `-l`                           list bookmark
* `-e`                           edit bookmark file
* `-p` <var>BOOKMARK\_ID</var>   display bookmark real path for BOOKMARK\_ID
* `-h`                           display this help and exit

## Variables

Bookmark list are stored in `~/.cdbookmark` file. This file name can be changed by `CD_BOOKMARK_FILE` variable.


## Examples

```
# Current directory is '/home/mollifier/work'.
% pwd
/home/mollifier/work

# Add current directory to bookmark. It's bookmark ID is 'work'.
% cd-bookmark -a work

# cd somewhere.
% cd

# Back to 'work' directory.
% cd-bookmark work
% pwd
/home/mollifier/work

# Add another directory to bookmark.
% cd /home/mollifier/tmp
% cd-bookmark -a tmp

# To show current bookmark, run cd-bookmark without any options or with -l option.
% cd-bookmark
tmp|/home/mollifier/tmp
work|/home/mollifier/work

# You can add relative path from bookmark real path at the end of BOOKMARK_ID.
% cd-bookmark work/project/zsh
% pwd
/home/mollifier/work/project/zsh

# To edit bookmark, run cd-bookmark with -e option.
% cd-bookmark -e
# Open bookmark file with $EDITOR (vim, emacs, etc.), so you can edit bookmark.
```

