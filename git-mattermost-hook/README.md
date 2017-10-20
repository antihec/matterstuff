# Simple Git post-receive hook for mattermost 
(Based on https://github.com/chriseldredge/git-slack-hook)

This is a bash script that posts a message into your
[Mattermost](https://mattermost.org) channel when changes are pushed.

Hook this script into `post-receive` for your git repositories.

This is a fork of a more elaborate Version
https://github.com/42wim/matterstuff/tree/master/git-mattermost-hook

## How to Install

Requires [curl](https://curl.haxx.se/) - _apt install curl_ for debian /
ubuntu.

Note: some git repositories may be "bare". You'll know if your repo is
bare or not by checking for a `.git` folder where your repo lives.

For bare repos, copy git-mattermost-hook to
`/path/to/your/repo/hooks/post-receive`.

For normal/non-bare repos, copy it to
`/path/to/your/repo/.git/hooks/post-receive`.

Finally, `chmod +x post-receive` to allow the script to be executed.

## Configuration

Add an Incoming WebHooks integration in your mattermost. In the script
change MM_HOOK to the webhook URL. Change MM_NAME and MM_CHAN if needed.
