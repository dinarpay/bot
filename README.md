
README.md
IDENA Telegram Bot

IDENA Telegram Bot is a Telegram bot created by @endogen for the IDENA community.
Overview

The bot is build around the python-telegram-bot module and is polling based. Webhook mode is implemented but untested.
General bot features

    Every command is a plugin
    Every plugin can be enabled / disabled without restarting the bot
    Every plugin can be updated by drag & dropping the plugin file into the bot chat
    Restart or shutdown the bot via command
    Bot can be used with or without SQLite database
    Bot can be administered by more then one user

IDENA specific features

    Sending DNA coins to addresses
    Notifications about DNA balance changes
    Generating QR-Code (of address) for deposits
    Enable / disable mining
    Kill your identity
    Import / export identity
    Show info for ceremony, epoch and your identity
    Show enode ID, IP and port
    Show sync status
    Show node version that is being used
    Show your address, balance and stake
    Show transactions (also pending once)

Configuration

Before starting up the bot you have to take care of some settings and add a Telegram API token. The configuration file and toke file are located in the config folder.
config.json

This file holds the configuration for the bot. You have to at least edit the value for admin_id. Everything else is optional.

    admin - ids: This is a list of Telegram user IDs that will be able to control the bot. You can add your own user or multiple users if you want. If you don't know your Telegram user ID, get in a conversation with Telegram bot @userinfobot and if you write him (anything) he will return you your user ID.
    admin - notify_on_error: If set to true then all user IDs in the "admin - ids" list will be notified if some error comes up.
    idena - api_key: The API key that your node is using (the value that you provide for the --apikey=<value> parameter)
    idena - timeout: Timeout value in seconds for the communication with the IDENA node
    idena - host: The hostname that is being used by the remote node. If you run your node locally then localhost is what you want to enter
    idena - port: The port that is being used by the remote node
    telegram - read_timeout: Read timeout in seconds as integer. Usually this value doesn't have to be changed.
    telegram - connect_timeout: Connect timeout in seconds as integer. Usually this value doesn't have to be changed.
    webhook - listen: Required only for webhook mode. IP to listen to.
    webhook - port: Required only for webhook mode. Port to listen on.
    webhook - privkey_path: Required only for webhook mode. Path to private key (.pem file).
    webhook - cert_path: Required only for webhook mode. Path to certificate (.pem file).
    webhook - url: Required only for webhook mode. URL under which the bot is hosted.
    database - use_db: If true then new database files (SQLite) will be created if a plugin tries to execute some SQL statements. If false, no databases will be used.

token.json

This file holds the Telegram bot token. You have to provide one and you will get it in a conversation with Telegram bot @BotFather while registering your bot.

If you don't want to provide the token in a file then you have two other options:

    Provide it as a command line argument while starting your bot: -tkn <your token>
    Provide it as an command line input (MOST SECURE): --input-tkn

Starting

In order to run the bot you need to execute it with the Python interpreter. If you don't have any idea where to host the bot, take a look at Where to host Telegram Bots. Services like Heroku (free) will work fine. You can also run the script locally on your own computer for testing purposes.
Prerequisites

You have to use at least Python 3.7 to execute the scripts. Everything else is not supported.
Installation

Install all needed Python modules

pip3 install -r requirements.txt

Starting

    First you have to make the script run.sh executable with

chmod +x run.sh

    Then you need to start the script file

./run.sh &

Stopping

The recommended way to stop the bot is by using the bot command /shutdown. If you don't want or can't use this, you can shut the bot down with:

pkill python3.7

which will kill every Python 3.7 process that is currently running.
Usage
Available commands
Bot

/about - Show info about the bot
/backup - Backup whole bot folder
/feedback - Send us your feedback
/help - Show all available commands
/log - Download current logfile
/restart - Restart the bot
/shutdown - Shutdown the bot

Identity

/ceremony - Show ceremony intervals
/epoch - Show info about current cycle
/export - Export private key for identity
/identity - Show details about a identity
/import - Import private key for identity
/kill - Kill your IDENA identity

Node

/enode - Get enode info
/offline - Go offline and stop mining
/online - Go online and start mining
/sync - Check if your node is synced
/version - Show version number of node

Wallet

balance - رصيد محفظة الجنيه الفلسطيني
deposit - إظهار عنوان المحفظة ورمز الاستجابة السريعة
feedback -  أرسل لنا ملاحظاتك
help - إظهار كافة الأوامر المتاحة للمحفظة
rain - إحصل علي جنيه فلسطيني مجاناً
send_t2x - تحويل جنيه فلسطيني من محفظتك
send_trx - تحويل دولار من محفظتك
withdraw_t2x - سحب كل الجنيه الفلسطيني من محفظتك
withdraw_trx - سحب كل الدولار من محفظتك
If you want to show a list of available commands as you type, open a chat with Telegram bot @BotFather and execute the command /setcommands. Then choose the bot you want to activate the list for and after that send the list of commands with description. Something like this:

balance - رصيد محفظة الجنيه الفلسطيني
deposit - إظهار عنوان المحفظة ورمز الاستجابة السريعة
feedback -  أرسل لنا ملاحظاتك
help - إظهار كافة الأوامر المتاحة للمحفظة
rain - إحصل علي جنيه فلسطيني مجاناً
send_t2x - تحويل جنيه فلسطيني من محفظتك
send_trx - تحويل دولار من محفظتك
withdraw_t2x - سحب كل الجنيه الفلسطيني من محفظتك
withdraw_trx - سحب كل الدولار من محفظتك
