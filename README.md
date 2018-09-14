# bash-anime-girl
Randomly says somewhat nice things to the user when typing wrong command. It includes actual japanese.

Based on the [bash-insulter](https://github.com/hkbakke/bash-insulter) by @hkbakke.

# Compatibility
* Bash v4 and newer
* Zsh

# Installation

    # Method 1 - know what you are doing
    git clone https://gitlab.com/RaitaroH/bash-anime-girl.git bash-insulter
    sudo cp bash-anime-girl/src/bash.command-not-found /etc/

    # Method 2
    sudo wget -O /etc/bash.command-not-found https://gitlab.com/RaitaroH/bash-anime-girl/master/src/bash.command-not-found

Then source the file automatically for new logins by adding the following to `/etc/bash.bashrc` or any of the other locations where you can configure your shell automatically during login (zsh have different config files):
```
if [ -f /etc/bash.command-not-found ]; then
    . /etc/bash.command-not-found
fi
```
Login again and type some invalid commands for the effects to be visible.

# Configuration
bash-anime-girl can be customized, by populating `CMD_NOT_FOUND_MSGS` or `CMD_NOT_FOUND_MSGS_APPEND` environment variables. The values should be arrays. `CMD_NOT_FOUND_MSGS` replaces the default messages, while `CMD_NOT_FOUND_MSGS_APPEND` appends more messages to the existing ones.

It is probably cleanest to source a file populating the environment variable as needed. In this example I create a file `/etc/bash.command-not-found-messages` with the following content:

    CMD_NOT_FOUND_MSGS=(
        "You are so smart!"
        "You look pretty today!"
        "I don't know what to say"
    )
    
Then source this file before you source the script:
```
if [ -f /etc/bash.command-not-found-messages ]; then
    . /etc/bash.command-not-found-messages
fi

if [ -f /etc/bash.command-not-found ]; then
    . /etc/bash.command-not-found
fi
```

Then logout and in again. The end result is that you will now use your messages instead of the default ones.
