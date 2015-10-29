# mattertee #

*mattertee* works like [tee](http://en.wikipedia.org/wiki/Tee_(command)) command (and inspired by [slacktee](https://github.com/course-hero/slacktee)
Instead of writing the standard input to files, *mattertee* posts it to your mattermost installation


## binaries
Binaries will be found [here] (https://github.com/42wim/matterstuff/releases/)

## building
Make sure you have [Go](https://golang.org/doc/install) properly installed, including setting up your [GOPATH] (https://golang.org/doc/code.html#GOPATH)

```
cd $GOPATH
go get https://github.com/42wim/matterstuff/mattertee
```

You should now have mattertee binary in the bin directory:

```
$ ls bin/
mattertee
```

## usage

```
Usage of ./mattertee:
  -c string
         Post input values to specified channel or user.
  -i string
        This url is used as icon for posting.
  -m string
        Mattermost incoming webhooks URL.
  -n    Post input values without buffering.
  -p    Don't surround the post with triple backticks.
  -u string
        This username is used for posting. (default "mattertee")
  -x    Add extra info (user/hostname/timestamp).
```

You can also set MM_HOOK containing your mattermost incoming webhook URL as an enviroment variable.

```
export MM_HOOK=https://yourmattermost/hooks/webhookkey
```

### example
```
uptime | mattertee -c off-topic -x -m https://yourmattermost/hooks/webhookkey
```

or if you've set MM_HOOK environment variable:

```
uptime | mattertee -c off-topic -x
```

![Image](http://snag.gy/qJomi.jpg)


## examples (taken from slacktee)
```

If you'd like to post the output of `ls` command, you can do it like this.

```
ls | mattertee
```

To post the output of `tail -f` command line by line, use `-n` option.

```
tail -f foobar.log | mattertee -n
```

You can specify `channel`, `username`, `iconurl` too.

```
ls | mattertee -c "general" -u "mattertee" -i "http://myimage.png" 
```

Of course, you can connect another command with pipe.

```
ls | mattertee | email "ls" foo@example.com
```