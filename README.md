Discord Webhooks Wrapper for PHP
====

A lightweight wrapper to interact with [Discord](https://discordapp.com) webhooks!

### Getting Started
This wrapper is installed by using [Composer](https://getcomposer.org). You also need to have (at least) PHP 5.3 installed, along with ext-curl. This wrapper has not been tested with HHVM, but there's no reason it shouldn't work!

1. Run `composer require auroraari/discord-webhooks` to install the latest release.
2. Include the Composer autoload file at the top of your file:
    - `include __DIR__.'/vendor/autoload.php';`
3. Enjoy!

### Setting up a webhook in Discord
*This currently only works in Discord's public test build, which can be found [here for Windows](https://discordapp.com/api/download/ptb?platform=win) and [here for Mac](https://discordapp.com/api/download/ptb?platform=osx).*

1. On a server you own (or have the "Manage Webhooks" permission on), open Server Settings, and select 'Webhooks' on the menu: ![Step 2](http://i.imgur.com/jovnbVO.png)

2. Click the "Create Webhook" button and complete the form. The "Name" field and avatar that you set are the defaults, and may be overriden in this wrapper, but ***the channel you pick cannot be changed by the wrapper.*** You'll need a separate URL for each channel you want to post to. ![Step 2](http://i.imgur.com/u8CcmE6.png)

3. Copy the "Webhook URL," and use that when initializing the class. 

4. Enjoy!

### Example
```php
<?php
    include __DIR__.'/vendor/autoload.php';

    use \DiscordWebhooks\Client as DiscordWebhook;
    
    $discord = new DiscordWebhook('URL-FROM-DISCORD');
    $discord->name('AuroraAri'); // Optionally, provide a name that the message will be sent from. If not set, uses the name set in Discord.
    $discord->avatar('http://i.imgur.com/RNYMCQp.png'); // Optionally, a URL for the user's avatar. If not set, uses the avatar set in Discord.
    $discord->message('Hi, Discord!'); // Optionally, set the message to be sent here. If not set, uses the message in $this->send().
    $discord->send('Hi again, Discord!'); // If the message wasn't set in $this->message, it must be set here. This method sends the message.
```
