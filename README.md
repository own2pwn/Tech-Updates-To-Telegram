# Tech Updates To Telegram

Simple script to automatically post WikiToLearn tech updates to a telegram channel. 

## Setup

- Download/Clone this repo
- npm install
- Create a Telegram Bot (https://core.telegram.org/bots#botfather)
	- Set the 'token' variable inside bot.js with the generated token.
- Add the newly crated bot to your channel/chat (if adding it to a channel add the bot as an administrator)
	- Set the 'chat' variable inside bot.js with the username of the channel (formatted as @channelusername) or with the Group Chat Id.
- Set the port (**yourport**, defaults to 8421) inside bot.js
- Make sure the port **yourport**/TCP is open on your Firewall/Router (you can change the port editing bot.js)
- Make sure the machine/newtork running thr script is always reacheable from the outside either by having a static public IP or by a domain name (if you have a dynamic IP look into Dynamic DNS services such as duckdns)
- Login to GitHub and open the repo you want to receive live updates from
- Add a new WebHook following this guide https://developer.github.com/webhooks/creating/
	- Payload URL: http://**yourdomain**:**yourport**/push
	- Content Type: application/json
	- Events: Just the push event
	- You can do this for as many repos as you want

## Setup by env variables
If you don't want to edit bot.js you can also set env variables. 

You can either edit env.sh and then execute "source env.sh" before running the bot
Or you can manually set them.


## Running the bot
- node bot.js

## Stopping the bot
- CTRL+C

## Solving Problems
- GitHub updates are not delivering
	- Make sure the script can be accessed from the outside of your network.
	- Make sure the port 8421/TCP is open on your Firewall/Router

- The script is not posting to Telegram
	- Make sure you have set the 'token' variable
	- Make sure you have added the bot to your Telegram Group or as an admin to your Telegram Channel


##Running bot docker
docker run -ti -p "port":"port" -e TELEGRAM_TOKEN="...." -e CHAT='...' -e PORT="port" wikitolearn/telegram-bot:0.1
	
## License
GPL 
