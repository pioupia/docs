---
layout: post
title: "Configuration"
date: 2020-21-12 00:00:00 -0400
categories: v1.7.1
---
# Configuration

Each and every option listed below is optional. Running tmi.js without options will result as an anonymous connection to Twitch and you will have to join the channels manually.

``options``: (_Optional_)

- ``clientId``: _String_ - Used to identify your [application](https://dev.twitch.tv/console/apps) to the API (Default: ``null``)
- ``debug``: _Boolean_ - Show debug messages in console (Default: ``false``)

``connection``: (_Optional_)

- ``server``: _String_ - Connect to this server (Default: ``irc-ws.chat.twitch.tv``)
- ``port``: _Integer_ - Connect on this port (Default: ``80``)
- ``reconnect``: _Boolean_ - Reconnect to Twitch when disconnected from server (Default: ``false``)
- ``maxReconnectAttempts``: _Integer_ - Max number of reconnection attempts (Default: ``Infinity``)
- ``maxReconnectInterval``: _Integer_ - Max number of ms to delay a reconnection (Default: ``30000``)
- ``reconnectDecay``: _Integer_ - The rate of increase of the reconnect delay (Default: ``1.5``)
- ``reconnectInterval``: _Integer_ - Number of ms before attempting to reconnect (Default: ``1000``)
- ``secure``: _Boolean_ - Use secure connection (SSL / HTTPS) (_Overrides port to ``443``_) (Default: ``false``)
- ``timeout``: _Integer_ - Number of ms to disconnect if no responses from server (Default: ``9999``)

``identity``: (_Optional_)

- ``username``: _String_ - Username on Twitch
- ``password``: _String_ - [OAuth password](http://twitchapps.com/tmi/) on Twitch

``channels``: _Array_ - List of channels to join when connected (Default: ``[]``)

``logger``: _Object_ - Custom logger with the methods ``info``, ``warn``, and ``error``

## Examples

### Node

~~~ javascript
const tmi = require('tmi.js');

const client = new tmi.Client({
    options: { debug: true, messagesLogLevel: "info" },
    connection: {
        reconnect: true,
        secure: true
    },
    identity: {
        username: 'your_username',
        password: 'oauth:your_auth'
    },
    channels: [ '#schmoopiie' ]
});

client.connect().catch(console.error);
~~~

### Browser
**index.html**

~~~ html
<!DOCTYPE html>
<html lang="en">
	<head></head>
	<body>
        <!--[IF IE]><!-->
        <script src="https://cdn.polyfill.io/v2/polyfill.min.js"></script>
        <!--<![endif]-->
        <script src="//gitcdn.xyz/repo/tmijs/cdn/master/latest/1.x/tmi.min.js"></script>
        <script src="example.js"></script>
	</body>
</html>
~~~
**example.js**

~~~ javascript
let client = new tmi.Client({
    options: { debug: true, messagesLogLevel: "info" },
    connection: {
        reconnect: true,
        secure: true
    },
    identity: {
        username: 'your_username',
        password: 'oauth:your_auth'
    },
    channels: [ '#schmoopiie' ]
});

// Connect the client to the server..
client.connect().catch(console.error);
~~~
