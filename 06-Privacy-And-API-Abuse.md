# 06 — Privacy & API Abuse

> Top.gg takes privacy and Discord API usage seriously. Commands that expose user data, mass-DM people, or abuse rate limits will get your bot rejected — and some will get it banned.

---

## The Rule

Your bot must respect the privacy of server members and Discord's API limits. Any command that leaks server or user information without consent, sends unsolicited mass messages, or abuses the API is forbidden.

---

## What Gets You Rejected

### Server List Command

```
Your bot has a server list command, [/bumpleaderboard], which is considered
a privacy breach as it lists all the servers your bot is in. Please do one
of the following before resubmitting:
- Limit the command to the bot owner(s) (you)
- Make this an opt-in feature
- In your bot's description or privacy policy, mention that you publicly
  show the guilds your bot is in and have an opt-out feature
- Remove the command entirely
```

Any publicly accessible command that lists all servers your bot is in reveals the names and existence of servers that may not want to be publicly listed. This is a privacy violation.

**Acceptable fixes:**
1. Remove the command entirely
2. Restrict it to bot owner only
3. Make it opt-in — servers must consent to being listed

---

### DM Commands With No Opt-Out

```
Your bot has a DM command (/dm) which allows anyone to DM a user which can
be used maliciously. The message your bot sends in DMs must state the author
or that it's from an anonymous user. It must also have a block/opt-out
feature. Otherwise, remove this command entirely before resubmitting.
```

Any command that lets one user DM another through your bot must:
1. State who sent the message (or clearly mark it as anonymous)
2. Include a block or opt-out mechanism so recipients can stop receiving them

---

### Bulk DM / Mass Message Commands

```
Your bot has a command ([/bulkdm]) that sends a message to every member
in the server. This is considered to be API abuse. Please remove this
command before resubmitting.
```

Commands that send a message to every server member — regardless of intent — are API abuse. Discord rate limits exist for a reason. Mass DM commands will also likely get your bot token flagged by Discord itself.

---

### Creating Server Invites Without Consent

```
Your bot creates an invite link upon joining. Even if these invites are only
seen by owners, it's considered a privacy breach as it creates an invite of
any server without that server's consent. Remove this command/feature
entirely before resubmitting.
```

Automatically generating an invite link to a server — even one sent only to the server owner — is a privacy violation. You're creating a shareable link to someone else's server without their explicit consent.

---

### Wipe / Nuke Commands

```
Your bot seems to have a /wipeserver command that deletes multiple channels
and/or roles at once. This violates our guidelines, please remove it entirely
and re-submit your bot.
```

Commands that mass-delete channels, roles, or other server assets are not allowed under any circumstances. These get bots banned from Top.gg, not just rejected.

---

### Downloader Commands

```
Your bot has a command with a downloader feature which isn't allowed because
of privacy/piracy content laws. Please remove this command.
```

Commands that download or rip videos, music, or media from third-party platforms (YouTube, TikTok, Spotify, etc.) violate copyright law. Remove them entirely.

---

### Updating Status Too Frequently

```
Your bot's presence is changing too frequently. The maximum allowed frequency
for updating status is 5 times per 20 seconds (approximately every 4 seconds).
Any faster than this is considered Discord API abuse. We recommend updating
the status at a more reasonable interval, such as every 120 seconds.
```

Updating your bot's presence more than 5 times per 20 seconds is Discord API abuse. Top.gg will reject you for it and Discord will rate-limit you.

---

### Asking for Login Credentials

```
Bots cannot ask for user login information (i.e. username/password/token)
for any site or service.
```

Under no circumstances should your bot ask for a user's password, username for an external service, or any token. This is an immediate rejection and likely a ban.

---

### Multiple Instances Running Simultaneously

```
Your bot application seems to be running multiple instances, which could
cause unhandled ratelimits and api abuse, as well as spam.
```

Running the same bot token on two or more processes at once causes duplicate responses, rate limit abuse, and spam. Use sharding if you need to scale — do not duplicate the process.

---

## What To Do

**Do:**
- Add opt-out mechanisms to any command that sends DMs on behalf of another user
- Disclose the sender's identity in any DM your bot sends on a user's behalf
- Restrict server list commands to bot owner only, or remove them
- Update your bot's status at a reasonable interval — every 60–120 seconds minimum
- Use sharding instead of running multiple instances
- Remove all downloader, nuke, and bulk-DM commands

**Don't:**
- Don't build commands that message every member of a server
- Don't auto-create server invites on join
- Don't publicly expose which servers your bot is in without opt-in consent
- Don't allow anonymous DMs without a block option for the recipient
- Don't update your bot's presence dozens of times per minute
- Don't ask users for passwords, tokens, or login credentials of any kind
- Don't include commands that mass-delete channels or roles
- Don't run two copies of your bot on the same token at the same time

---

## Key Takeaway

Privacy violations and API abuse can get your bot **banned** from Top.gg, not just rejected. These are hard rules, not guidelines.
