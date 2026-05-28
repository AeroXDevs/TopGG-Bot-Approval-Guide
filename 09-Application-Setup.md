# 09 — Application Setup

> Misconfigured Developer Portal settings can stop reviewers from even inviting your bot. Fix these technical issues before you submit — they have nothing to do with your bot's code.

---

## The Rule

Your bot application must be correctly configured in the Discord Developer Portal. Reviewers must be able to invite your bot, add it to a server, and have it function without any application-level errors blocking them.

---

## What Gets You Rejected

### Unknown Application Error on Invite

```
There's an unknown application error when trying to invite your bot.
Please make sure of the following:
  - The application ID you entered is correct
  - You have a bot user with your application
  - Your bot application wasn't deleted
```

If the Discord invite URL throws an error before the bot is even added, the reviewer cannot do anything. This is usually caused by:

- Wrong Application/Client ID in the invite URL
- No bot user created under the application
- The application was deleted
- The invite URL was built incorrectly

Test your own invite URL in a private/incognito window before submitting.

---

### REQUIRES OAUTH2 CODE GRANT Turned On

```
Your bot seems to need a code grant for no reason. Make sure the option
"REQUIRES OAUTH2 CODE GRANT" on your bot application page is off. If your
bot does need user authorization, feel free to open a ticket in our Discord
server.
```

This toggle must be **OFF** for virtually every bot. When it's on, adding the bot requires an OAuth2 flow that reviewers cannot complete through the standard invite process.

**Where to fix it:** Discord Developer Portal → Your Application → Bot tab → scroll down → `REQUIRES OAUTH2 CODE GRANT` → toggle OFF.

---

### Multiple Instances Running at Once

```
Your bot application seems to be running multiple instances, which could
cause unhandled ratelimits and API abuse, as well as spam. Please be sure
that your bot isn't running on multiple instances prior to resubmitting.
```

Running the same bot token on two or more processes simultaneously causes:
- Duplicate responses to every command
- Rate limit abuse
- Spam behaviour

This happens when you forget to stop a local instance before starting the hosted one, or run both your PC and a server at the same time.

---

### Bot Flagged by Discord

```
Your bot has been flagged by Discord, which results in us being unable to
test your bot. Please reach out to Discord directly: https://dis.gd/contact
```

If Discord has placed a flag on your application, the Top.gg Verification Center cannot add your bot. Resolve this with Discord before resubmitting.

---

### Bot Automatically Leaves the Test Server

```
Upon inviting your bot, it seems to automatically leave our Verification
Center without any action from us.
```

Your bot is coded to leave unrecognised servers. Before submitting, either:
1. Remove the auto-leave / guild whitelist logic temporarily
2. Or add the Top.gg Verification Center ID (`333949691962195969`) to your whitelist

---

## What To Do

**Do:**
- Test your invite URL yourself in an incognito window before submitting
- Turn off `REQUIRES OAUTH2 CODE GRANT` in the Discord Developer Portal
- Stop local development instances before relying on your hosted version for review
- Add `333949691962195969` to any guild whitelists if you must keep that logic
- Test adding your bot to a fresh server — make sure nothing crashes and it doesn't auto-leave
- Verify your Application ID is correct in both the invite URL and your Top.gg submission

**Don't:**
- Don't submit with `REQUIRES OAUTH2 CODE GRANT` enabled
- Don't run your bot from two places at the same time during review
- Don't have a guild whitelist that excludes the Top.gg test server
- Don't submit if your Discord application has been flagged or deleted
- Don't have auto-leave logic that triggers on servers you haven't manually added

---

## Building a Correct Invite URL

```
https://discord.com/api/oauth2/authorize
  ?client_id=YOUR_CLIENT_ID
  &permissions=PERMISSION_INTEGER
  &scope=bot%20applications.commands
```

- `client_id` — Your application's Client ID from the Developer Portal (not the bot's username)
- `permissions` — Integer representing your required permissions
- `scope` — Must include both `bot` and `applications.commands` if you use slash commands

---

## Avoiding Multiple Instances (pm2)

```bash
# Check for existing instances
ps aux | grep node

# Use pm2 to manage — restart cleanly without duplicating
pm2 start bot.js --name mybot
pm2 restart mybot   # restarts without creating a duplicate process
```

---

## Key Takeaway

If reviewers can't invite your bot, everything else is irrelevant. Test your invite URL, turn off OAuth2 Code Grant, and make sure only one instance is running.
