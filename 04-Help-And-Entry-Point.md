# 04 — Help Command & Entry Point

> Reviewers are not going to dig through your GitHub README to figure out how to use your bot. If there's no clear way to get started, they decline and move on.

---

## The Rule

Your bot must have a **working help command** or a **clearly documented point of entry**. A reviewer should be able to add your bot to a server and know how to start using it within 30 seconds — with no prior knowledge of your bot.

---

## What Gets You Rejected

### No Help Command and No Obvious Entry Point

```
Your bot doesn't have a (working) help command or obvious point of entry.
Please make sure your bot has a help command or has an explanation in the
bot description.
```

```
Your bot does not provide a working help command or a clear and obvious
point of entry. Please ensure the bot includes a functional /help command
and/or a properly structured bot description that clearly explains how
users can start using its features.
```

---

### Help Command Requires Owner Permission

```
Your bot's help command requires owners permission to work. Your help
command should be able to function without this permission.
```

A help command gated behind bot-owner-only access is useless to everyone else. Any member of any server must be able to run `/help` or `!help` and receive a response — no permission check, no role check, no owner check.

---

### Slash Commands Not Deployed Globally

```
Please make sure if your bot has slash commands, they are deployed globally.
```

If your slash commands only appear in your development server, they won't show up in the reviewer's test server. You must use `Routes.applicationCommands()` for global deployment.

---

### No Response on Any Command

```
Your bot doesn't have any actual (functioning) features/commands.
```

If a reviewer adds your bot, runs `/help`, tries every command they can find, and gets nothing back — that's an immediate rejection.

---

## What To Do

**Do:**
- Build a `/help` or `!help` command that lists all commands with short descriptions
- Make the help command accessible to everyone — zero permission requirements
- Deploy slash commands globally before submitting
- Include your bot's prefix and basic commands in the Top.gg description so reviewers know where to start
- Consider sending a welcome message when the bot joins a server, with a quick-start guide

**Don't:**
- Don't lock your help command behind any permission, role, or owner check
- Don't deploy slash commands only to your development server
- Don't assume reviewers will find your GitHub or docs website to learn how to use your bot
- Don't make onboarding dependent on a dashboard the reviewer may not be able to access

---

## What a Good Help Command Looks Like

```
/help

BotName — Command List

Moderation
  /ban [user] [reason]     — Ban a user
  /kick [user] [reason]    — Kick a user
  /mute [user] [duration]  — Timeout a user
  /lock [channel]          — Lock a channel

Music
  /play [query]            — Play a song or playlist
  /skip                    — Skip the current track
  /queue                   — View the queue
  /stop                    — Stop and clear the queue

Setup
  /setup                   — Run the initial bot setup

Use /help [command] for more detail on a specific command.
```

---

## Global Slash Command Deployment

```js
const { REST, Routes } = require('discord.js');
const rest = new REST({ version: '10' }).setToken(TOKEN);

// Deploy globally
rest.put(Routes.applicationCommands(CLIENT_ID), { body: commands })
  .then(() => console.log('Global commands deployed.'))
  .catch(console.error);
```

> Note: Global commands can take up to 1 hour to propagate after deployment.

---

## Key Takeaway

If a reviewer can't figure out how to use your bot within the first minute, it's a rejection. A working, open, no-permission help command is not optional.
