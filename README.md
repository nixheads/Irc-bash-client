# This is a IRC client written in BASH

#### Usage:
````
[-h hostname] [-p port] [-n nick] [-x password] [-f configfile]  [-y logging YES/NO]  [-u log file] [-v]
i also intergrated commands to talk a bot (if you own one)
[-l bot pass] [-k bot nick] [-j bot op chan]

You can set the options in 3 ways:
from commandline as shown above
create a config file (.bashirc) and set the variables there.
or edit the irc-bash script and change the options at the top of the file
````
## Features
##### Ping
````
when the sever pings the client a ✓ is displayed to show you that connection is still active
````
#### autojoin
````
If you get kicked from the channel the client will auto join for you
````
#### Desktop notifications
````
This client will use notify-send to inform you of:
being kicked
joining rooms
when your name is mentioned in a channel
````
#### Logging
````
You can choose to log the chat stream to a file, in a nice grep'able format
$ cat $LOGfile | grep #nixheads>
will find all chat logs from the channel #nixheads 
the format is  <$USER@$CHANNEL> $TEXT
````
#### Themes
````
Using the $IRC_PREFIX variable you can input formatting for your stream
IRC_PREFIX=(
    "\e[0m\e[4m\e[1m\e[31m::^ERROR"
    "\e[0m\e[24m\e[22m\e[0;92m\e[30m::(^<[^@]*@[^#])"
    "\e[0m::^<"
    "\e[0m::^->"
    "\e[0m\e[24m\e[22m\e[40m\e[1;97m::(.*)"
)

here is an example: If you dont know what this means, go read on how printf sets colours.
````
#### Multiple channels
````
use the chan variable to set as many channels as you want to join on login
chans=( "#channel1", "#channel2", "#channel3 )
````
#### Boot scripting
````
if you need to run commands on boot you can add them to the $IRC_SCRIPT var
i like to set mine to
IRC_SCRIPT=":s #nixheads"
to set my input to channel #nixheads
````
#### Timestamp for incoming messages
````
Uses <Hour:Min:Sec> format
````
#### Input
````
Ctrl + C will not kill the client nor will it print ^C
Tab will not auto complete file/dir listings but will insert a tab instead
````
# Commands
This client uses commands, starting with ':' and followed by the command letter i.e  :a
#### Imgur links
- :i - will send a random link from imgur to the current set channel
- :r - reads lines from file and sends to channel using sed format
:r 32p /home/user/foobar     #  will read line 32 from file foobar in the users home dir
- :k - kick user from channel (need to be op)
:k username
- :m - send a message to a channel or user
:m #channel message to send
- :l - part from channel
:l #channel
- :j - join channel
:j #channel
- :s - sets channel to the active stream so you can send messages without using :m each time
:s #channel
- :a - sends an action command, the same as /me on other clients
:a message to send
- :p - sends a command to the bot, (if your bot supports) currently a ping
- :z - sends a message to the bot, command written on bot, tells the bot to identify with nickserv
- :q - tells the client to quit from server and exit client

#### Keybinds
- Ctrl + L  - If someone sends a mesage to you while your typing and it interfers with your input this will redraw the line for you
- Ctrl + D  - If you decide what you have typed isnt what you want to send, this will delete all the text in you input line
