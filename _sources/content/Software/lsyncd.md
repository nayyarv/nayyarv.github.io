Title: Lsyncd
Subtitle: Or working on remote servers
Date: 2019-05-10 10:20
Category: practical
Tags: practical, remote, training
Authors: Varun Nayyar


This is a short blog on using lsycnd, a tool to sync between you and a remote host.

## Working on a Remote Host

In many instances, I find it necessary to work on a remote host. The reasons are numerous, but commonly come down to hardware - I need a GPU or a much beefier compute instance than my laptop can provide. This is not the only reason, the other common reason has been data location - my datasets were in the US and I was in Sydney. It's much faster to send your code over than TBs of data, so that was a no brainer. Of course, corporate IT might mandate it under Data Loss Prevention ideas, but the fact of the matter, running your code on a remote server is a relatively common thing we need to do as Data Scientists.

I vastly prefer the tools I grew up with before I got good with vim and using vim over high latency connections is annoying and I haven't spent the time configuring vim to be on par with what an IDE gets you out of the box. So I use a tool called `lsyncd` instead

## Lsyncd

[Lsyncd](https://github.com/axkibe/lsyncd) is a daemon written in lua and C that watches a series of folders and syncs the files that change over rysnc. It's perfect for keeping your code in sync with a remote host. 

Here's a minimum lsycnd config file. Save it to a location say `~/.lsyncd`. Use the `rsync` conventions to replace the angle bracket fields.

```lua
settings {
    logfile    = "/tmp/lsyncd.log",
    statusFile = "/tmp/lsyncd.status",
    nodaemon   = true,
}
sync {
    default.rsyncssh,
    source    = <source folder>,
    host = <destination host>,
    targetdir = <dest folder on host>,
    delay = 5,
    rsync     = {
        binary   = "/usr/local/bin/rsync",
        archive  = true,
        compress = true,
    },
    exclude = {
        "build",
        "downloads"
    },
    ssh = {
       identityFile = <private key>,
       options = {
          User = '<username on remote host>'
        }
    },    
}
```

Start with `lsyncd ~/.lsyncd` and now lsyncd will sync the folders over (it will need `sudo` on OS X). The config is in lua syntax, so use lua conventions to expand and make it more effective. You can even daemonize the process and have it start on computer startup, though it has a tendency to hang

## Caveats

1. It's not instant - as you write code, you'll have to wait a few seconds for the sync to happen. Get into the habit of writing a little doc and saving, by then, your code will have sync'd over and you can run
2. Latency severely affects performance - it's over TCP so your bandwith is latency bound. It's much worse to servers that are far away. 
3. Keep it to code only - Having too many files and too much data to sync over can cause issues with the daemon. I generally keep a few configs handy to ensure I have a few lsyncd instances up that are independent of each other.

Happy coding!

