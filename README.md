# ScrimBot

[![Add ScrimBot to server](https://img.shields.io/static/v1?label=Add%20ScrimBot&message=to%20server&color=7289DA&logo=Discord&logoColor=white&style=flat-square)](https://discord.com/oauth2/authorize?client_id=715030981894995998&scope=bot&permissions=285355008)

[![ScrimBot Support](https://img.shields.io/static/v1?label=ScrimBot%20Support&message=server&color=7289DA&logo=Discord&logoColor=white&style=flat-square)](https://discord.gg/hfFJxUG)




ScrimBot is Discord bot meant to allow for the easy creation of VALORANT custom matches.

 You tell the bot how many players per team, when the match will be and what map you would like and the bot will do the rest. Interested players can then react to the message to join a team, and once the match is complete you can add the final score and the match will be recorded for posterity.

 Players can also tell the bot their competitive rank and it will automatically assign them a role in all servers that they share with the bot.

_ScrimBot is based off [Mountainz](https://github.com/Kalissaac/Mountainz)._

## Running this yourself

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

### Requirements:
1. Firebase Project (https://console.firebase.google.com/)
2. Discord Bot Token (https://discord.com/developers/applications)
3. Node.js Version 12 or higher (https://nodejs.org/en/download/)

### Instructions:
ScrimBot configuration is handled through environment variables. These can be set inside your terminal, on your hosting platform, or using a file named `.env` in the project directory.

Here's a helpful guide on how to set them up for your platform: https://www.twilio.com/blog/2017/01/how-to-set-environment-variables.html

For the purposes of this guide, we'll be using a `.env` file, which is the easiest option.

---
0. Clone the repository
```
$ git clone https://github.com/SchwaIndustries/ScrimBot.git
$ cd ScrimBot
```

1. Create a file named `.env` in the root directory of the bot with the following contents:
```
TOKEN=<discord bot token>
TIME_ZONE=<(OPTIONAL) desired time zone (https://en.wikipedia.org/wiki/List_of_tz_database_time_zones), default is America/Los_Angeles> 
PREFIX=<(OPTIONAL) desired bot prefix, default is v!>
```

2. Replace `<discord bot token>` with your bot token

3. In your Firebase project, navigate to Settings > Service Accounts > Firebase Admin SDK and click **Generate a new key**

4. You now have two options: if you want to store the JSON locally, you can put the file in your project folder and set an additional key which points to it:
```
GOOGLE_APPLICATION_CREDENTIALS=</path/to/service-account-file.json>
```
or, if you are unable to store a JSON file in your project directory, you can add some specific keys and ScrimBot will do the rest for you.
```
FIR_PROJID=<Firebase project ID>
FIR_CLIENTID=<Firebase client ID>
FIR_PRIVATEKEY_ID=<Firebase private key ID>
FIR_PRIVATEKEY=<Firebase private key>
```
If both are present, `GOOGLE_APPLICATION_CREDENTIALS` will be preferred.

6. Run `npm install` to install bot dependencies

7. Run `npm start` and the bot should be online!

8. You can add yourself as a bot admin by modifying your user entry in the database. In the `users` collection, find your user ID and add a field named `admin` with the boolean value of `true`. This will allow you to access certain bot admin commands.
