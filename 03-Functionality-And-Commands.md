# 03 — Functionality & Commands

> If your commands don't work, your bot doesn't get approved. Reviewers test everything listed on your page.

---

## The Rule

Every command listed on your bot's Top.gg page must work during the review. Every feature you advertise must be testable by the reviewer. Broken commands and non-functional features are an immediate decline.

---

## What Gets You Rejected

### Main Feature Not Working

```
Your bot's main feature (music) does not seem to be working. Please fix
this issue and re-submit your bot.
```

```
Your bot's main feature ([.ticket panel]) does not seem to be working.
Please fix this issue and re-submit your bot.
```

Even if ten other commands work perfectly, a broken primary feature means rejection. Music bots, ticket bots, economy bots, moderation bots — the core purpose of your bot must function end to end.

---

### Majority of Commands Not Responding

```
The majority of your commands listed on your bot's page, or help command
do not provide a response, or do not seem to function/work.
```

```
The commands listed on your bot's page do not seem to actually exist in
the bot. Additionally, the commands that are present in the bot do not
appear to function properly.
```

If you list 20 commands and 12 of them produce no response, that is an instant rejection. Only list commands that exist and are working right now.

---

### Not Enough Commands or Features

```
For a bot to be considered approvable, it must have at least 1 "feature"
OR 5 valuable commands. Your bot has [4] valuable command(s) and no features.
```

Top.gg requires a minimum of either:
- **1 meaningful feature** — a complete system such as a ticket system, leveling system, or music player
- **5 valuable commands** — not `/ping`, `/help`, `/invite` — actual utility commands users would come for

Bots with 2–3 trivial commands will not be approved.

---

### Commands Only Work in One Server

```
Your bot has been declined because its commands are server-locked and only
functional within a specific server. Due to this, we are unable to properly
test and review the bot's features.
```

If your bot only responds in your own server, the reviewer cannot test it. All commands must work globally, or at minimum in the Top.gg Verification Center.

---

### Dashboard Not Accessible

```
Your bot needs to be configured on the dashboard in order for its main
functions to work, but I was unable to log in to the dashboard.
```

If your bot requires dashboard setup before it functions, that dashboard must be accessible to a standard Discord user — not just you. If the reviewer can't log in or navigate it, the bot gets declined.

---

### Ticket System Not Creating Tickets

```
We successfully posted the ticket panel, but when opening a ticket, the
bot gave an error. The bot had the MANAGE_CHANNELS and MANAGE_ROLES
permissions required for opening a ticket.
```

Ticket bots are one of the most commonly rejected bot types. The full flow must work: panel posts → ticket opens → channel is created → ticket closes. Test the entire flow before submitting.

---

### Music Bot Joins But Doesn't Play

```
Your bot's main feature, music, is not working properly. It gave an error
while trying to play music and kept leaving the voice channel immediately
after joining.
```

Joining the voice channel is not enough. The bot must actually play audio. If your Lavalink node is down, your YouTube or Spotify integration is broken, or the bot errors on play — fix it before submitting.

---

### Features Locked to Bot Owner

```
Your bot's main feature (tickets) seems to be locked behind bot owner only.
Please fix this issue and re-submit your bot.
```

If setting up your bot's core functionality requires being the bot owner, reviewers can't use it. Core features must be accessible to any server administrator.

---

## What To Do

**Do:**
- Test every command listed on your page before submitting — use a fresh server and a non-admin account
- Test the full flow of every feature system end to end, not just the setup step
- Deploy slash commands globally using `Routes.applicationCommands()` — not guild-only
- Remove any command from your listing that doesn't fully work yet
- Make your dashboard accessible to any Discord user, not only yourself
- If you have a music bot, test with multiple sources: YouTube links, search queries, playlists

**Don't:**
- Don't list commands that haven't been built or don't work yet
- Don't submit with a broken Lavalink or audio setup
- Don't lock core features to bot owner only
- Don't deploy slash commands only to your own server
- Don't submit a bot whose primary feature requires server-specific setup only you can do

---

## Global Slash Command Deployment

```js
const { REST, Routes } = require('discord.js');
const rest = new REST({ version: '10' }).setToken(process.env.TOKEN);

// Correct — deploys globally to all servers
await rest.put(
  Routes.applicationCommands(process.env.CLIENT_ID),
  { body: commands }
);

// Wrong for review — only works in one specific guild
await rest.put(
  Routes.applicationGuildCommands(process.env.CLIENT_ID, GUILD_ID),
  { body: commands }
);
```

> Global command propagation can take up to 1 hour after deploying. Do this well before you submit.

---

## Key Takeaway

Only list commands that exist and actually work. Test every single one before submitting. If your bot's main purpose is broken, nothing else matters.
