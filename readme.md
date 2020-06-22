# git-monitor

`git-monitor` is a bash script based on `git-notify` made by [Jake Moffatt][1]. Whenever it notices that there is a new commit, it will automatically pulls new commit to the local repository.

I was looking for a solution, which pulls automatically whether there is a new commit. However, I found `git-notify`, which in fact is a little bash script that will monitor new commits, and then notifies the user that there is a new commit on remote repository. I modified some code a bit, so it will automatically pulls new commit(s) if there's any within specified period.

Originally, I intend to use this for my local development, which uses a separate physical machine. I treat this as an alternative to SMB/NFS, as sometimes it's quite a hassle to setup (especially when I use different development platforms -- e.g. Windows and Linux-based distros like Ubuntu).

## Original `git-notify` Author Notes

I asked [this question](http://stackoverflow.com/questions/5082001/is-there-a-tool-to-watch-a-remote-git-repository-on-ubuntu-and-do-popup-notificat) on StackOverflow to find out if there was a tool to notify me of commits to remote git repositories, and the answer came back no!

Thus, `git-notify` was born!

## Installation:

Just download git-notify and put it somewhere in your `PATH`. If you want to specify a new `PATH`, add

```sh
export PATH="your_directory:$PATH"
```

to your `.bashrc` file, put `git-monitor` inside, and close and reopen the terminal.

## Usage

```
git-monitor
```

The script will run in the background. By default, it will monitor for commit changes every `60` seconds.

## Terminating

If you want to kill `git-monitor` later, grab its PID by running

```
ps aux | grep '[g]it-monitor'
```

It will output something like

```
jake      9541  0.0  0.0  12012  1392 pts/3    S    12:54   0:00 /bin/bash ./git-monitor
```

Note the PID, which is the first number of the line. Then, use `kill` with the PID provided above, like

```
kill 9541
```

[1]: https://github.com/jakeonrails/git-notify
