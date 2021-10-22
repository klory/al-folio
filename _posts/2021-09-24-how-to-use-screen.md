---
layout: post
title: Use screen to keep sessions alive when you leave
description: Use screen to keep the training going on
date: 2021-09-24
comments: true
---

## What is screen

`screen` is a Linux tool to create seesions in your terminal, these sessions will remain alive even when you close your terminal, which happens quite often when running deep learning models on remote clusters.

## Common usages

* `screen -ls` lists all sessions
* `screen -S your-session-name` creates a new session
* `screen -r your-session-name` attach an existing session, you can just type in the first few letters
* `screen -X -S your-session-name quit` kill an existing session

I like shortcuts, I create a few and put them in `~/.bashrc`, so I dou't need to input these long commands
```shell
alias sls='screen -ls'
alias sr='screen -r'
alias sS='screen -S'
alias ns='nvidia-smi' # extra bonus
function sk() {
  var=$(screen -ls $1|awk 'NR==2 {print $1}')
  echo 'trying to kill' $var
  screen -X -S $1 quit
}
```

When you are inside a screen session:

* press `control + A`, release then press `D` to detach the current session
* press `control + D`, quit the current session
* press `control + A`, release then type `:sessionname new-session-name` to rename the current session.


## Defects
  
* Sometimes I forget whether I'm in a session or which session I'm in, but I could not find a way to always show the current session name.

## Q&A

* [can't re-attach to your screen session after a lost connection](https://kb.iu.edu/d/ahrm)