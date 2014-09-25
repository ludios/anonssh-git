anonssh-git
===========

The purpose of anonssh-git is to let you clone any GitHub repo using SSH instead of
HTTPS, even on machines which don't have your `~/.ssh/id_rsa`.  This is ideal
because OpenSSH is less buggy than SSL libraries, and has a security model
that does not let rogue or compromised certificate authorities MITM
your git clone/fetch.

anonssh-git uses a publicly-known "private" key registered to
https://github.com/anonssh-keys, and the key (like any other registered to GitHub)
can be used to clone any repo.

To configure `~/.ssh/config` and `~/.ssh/known_hosts` to use this key, run
`./install-anonssh-config`.  If you already have a `Host github.com` in
`~/.ssh/config`, it will not change `config`.  You should not use this key
on machines from which you push code to GitHub, because cloning using
your own SSH key will work fine.

To use the git wrapper that converts `git clone https://github.com/x/y` to
`git clone git@github.com/x/y`, run `anonssh-git` or `alias git=anonssh-git`.
