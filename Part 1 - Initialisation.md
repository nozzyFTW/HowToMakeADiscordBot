# How to Make a Discord Bot using JavaScript
## Part 1 - Initialisation
### Creating the Discord Bot Account
Within this tutorial, you will learn how to create a Discord bot using Node.JS and Discord's API. Before we get started, please ensure you meet the following **requirements**:
- An active Discord account
- An IDE (i.e. Visual Studio Code)
- [Downloaded Node.JS](https://nodejs.org/en/)

If these have been met, then you can continue to setting up the bot account. This can be done by accessing the [Discord Developer's Portal](https://discord.com/developers/applications). Once there, click on **New Application**.

After this, you will be greeted by a dialog box. Within this dialog box, you must name your bot to proceed. (Don't worry, you can change the name afterwards).

Once the application has been created, head to the "**Bot**" tab and click **Add Bot**.

Now that the bot has been create, you must copy the token. (This token must not be shared with anyone, as this is the password to the bot).

### Inviting Your Bot to a Server
Now that the bot has been created, it must be invited into a server. As you may already know, this is done through an OAuth2 link.
To get this link, you will need to head over to the "**OAuth2**" tab. Once in this tab, you are to select **bot** which is located under the **Scopes** section.

Now that the scope has been set, you will need to scroll down to the **Permissions** section, in which you will need to select the permissions your bot will require upon joining any servers.

Once the appropriate permissions are selected, click on the **copy** button, which is located just above the **Permissions** section. Now that you have done this, you are to paste this URL into your browser and authorize the bot to join your server, of which you are going to test it in.

### Setting up the Node.JS project
Assuming you have Node.JS installed and up to date, you will need to load up the **Node.js Command Prompt**.

Once this has loaded up, type the following code:
```shell
mkdir mybot
cd mybot
```
Once this has been completed you can begin to setup your project files. This is done by using the following code:
```shell
npm init
```
To complete this part, fill in the information that you seem fit to your project. Now that the project has been setup, you will need to download the require dependecies by using the following code:
```shell
npm install discord.js dotenv
```

### Starting the code
Before you start to program the bot, you must change some settings within the  `package.json` file. To do this, first, type the following code into the **Node.js Command Prompt**:
```shell
npm install nodemon
```
Now that you have install the Nodemon dependency, you will need to load up your IDE (mine is [Visual Studio Code](https://code.visualstudio.com/)), and load up your project folder, of which you created in the previous step, via the Command Prompt.

Now that you are within this folder, you will need to access the  `package.json` file. Now that you are in this file, you will now need to type the following in under `"scripts"`:
```json
"dev": "nodemon main.js"
```

Now that the project has been fully setup, with the dependencies, you can start to code the bot. To do this, create a **New File** and name it  `main.js`.

Now that you have created the JavaScript file, type the following code: 
```js
require("dotenv").config();
const { GatewayIntentBits } = require("discord.js");
const Discord = require("discord.js");

const client = new Discord.Client({
	intents: [
		GatewayIntentBits.Guilds,
		GatewayIntentBits.GuildMembers,
		GatewayIntentBits.GuildBans,
		GatewayIntentBits.GuildEmojisAndStickers,
		GatewayIntentBits.GuildIntegrations,
		GatewayIntentBits.GuildWebhooks,
		GatewayIntentBits.GuildInvites,
		GatewayIntentBits.GuildVoiceStates,
		GatewayIntentBits.GuildPresences,
		GatewayIntentBits.GuildMessages,
		GatewayIntentBits.GuildMessageReactions,
		GatewayIntentBits.GuildMessageTyping,
		GatewayIntentBits.DirectMessages,
		GatewayIntentBits.DirectMessageReactions,
		GatewayIntentBits.DirectMessageTyping,
		GatewayIntentBits.MessageContent,
		GatewayIntentBits.GuildScheduledEvents
	]
});

client.on("ready", () => {
	console.log(`Logged in as ${client.user.tag}!`);
});

client.login(process.env.TOKEN);
```

Now that you have inputted this code, you must now create a `.env` file, of which will store the token of your bot (you copied this earlier from the **Bot Tab** in **Discord's Developer Portal**).

Within this file, type the following code:
```shell
TOKEN = "PASTE_TOKEN_HERE"
```
### Running your Bot
Now that you have programmed a basic bot with no functionality as of yet, you can run the bot by typing the following into the **Node.js Command Prompt**:
```shell
npm run dev
```

Now that you have completed this part, you can continue onto [Part 2 - Commands](Part%202%20-%20Commands), or you can return to the [Contents Page](https://github.com/nozzyFTW/HowToMakeADiscordBot/blob/main/README.md).
