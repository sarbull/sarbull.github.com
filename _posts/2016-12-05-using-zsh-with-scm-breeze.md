---
title: Using oh-my-zsh with scm_breeze
---

# Using oh-my-zsh with scm_breeze

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
$ touch file{1..10}.txt
$ gs
# On branch: master  |  [*] => $e*
#
➤ Untracked files
#
#      untracked:  [1] file1.txt 
#      untracked:  [2] file10.txt 
#      untracked:  [3] file2.txt 
#      untracked:  [4] file3.txt 
#      untracked:  [5] file4.txt 
#      untracked:  [6] file5.txt 
#      untracked:  [7] file6.txt 
#      untracked:  [8] file7.txt 
#      untracked:  [9] file8.txt 
#      untracked: [10] file9.txt 
#
```
