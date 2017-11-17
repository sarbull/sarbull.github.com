---
title: Using oh-my-zsh with scm_breeze
---

## oh-my-zsh
Oh-My-Zsh is an open source, community-driven framework for managing your ZSH configuration.

### Installing oh-my-zsh
```bash
$ sudo apt-get install zsh
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
$ vim ~/.zshrc # ZSH_THEME="frisk"
```

## scm_breeze
SCM Breeze is a set of shell scripts (for bash and zsh) that enhance your interaction with git.

### Installing scm_breeze
```bash
$ git clone git://github.com/scmbreeze/scm_breeze.git ~/.scm_breeze
$ ~/.scm_breeze/install.sh
```
### Example scm_breeze commands
```bash
$ mkdir test
$ cd test
$ git init
$ touch file{1..4}.txt
$ gs
# On branch: master  |  [*] => $e*
#
> Untracked files
#
#      untracked:  [1] file1.txt 
#      untracked:  [2] file2.txt 
#      untracked:  [3] file3.txt 
#
$ git add 1-3
$ gs
# On branch: master  |  [*] => $e*
#
> Changes to be committed
#
#       new file:  [1] file1.txt 
#       new file:  [2] file2.txt 
#       new file:  [3] file3.txt 
#
> Untracked files
#
#      untracked:  [4] file4.txt 
#
```
