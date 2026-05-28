# 01 — Bot Availability

> The single most common rejection reason. Over 99 bots were declined purely because they were offline when a reviewer showed up.

---

## The Rule

Your bot must be **online and fully functional** at all times during the review period. Reviewers do not book time slots — they pick up your submission whenever they're free and immediately try to invite and test your bot. If it's offline, it gets declined instantly, no exceptions.

---

## What Gets You Rejected

### Bot Was Offline at Review Time

```
Your bot was offline when we tried to review it. For that reason, we are
unable to test it. Please get your bot online and re-apply.
```

The most frequent rejection in the entire dataset. Your bot doesn't have to be broken — it just has to be off. This usually happens when people run their bot on their personal computer and close it.

---

### Bot Crashed Mid-Review

```
Your bot went offline while testing it. Due to this, I wasn't able to
finish testing your bot.
```

The reviewer was already partway through testing and the bot disconnected or crashed. They do not come back — it's an immediate decline. This points to unstable hosting or an unhandled error in your code.

---

### Bot Auto-Leaves the Server

```
Your bot kept leaving the server as soon as it was added, so we were
unable to test it. Please fix this issue and reapply.
```

Some bots are coded with a guild whitelist — if they join an unrecognised server, they automatically leave. The Top.gg Verification Center is not on your list, so the bot leaves before any testing can happen.

---

### Bot Set to Private

```
Your bot is set to private, so we were unable to review it. Please make
the bot public and reapply.
```

If `PUBLIC BOT` is toggled off in the Discord Developer Portal, nobody can invite your bot. Go to your application → Bot tab → turn `PUBLIC BOT` on.

---

## What To Do

**Do:**
- Host your bot on a VPS or cloud server — not your personal computer
- Use a process manager like `pm2` so your bot restarts automatically if it crashes
- Run your bot for at least 48 hours before submitting to confirm it's stable
- Enable `PUBLIC BOT` in the Discord Developer Portal
- If you have a guild whitelist, add the Top.gg Verification Center ID (`333949691962195969`)
- If your bot only runs during certain hours, note those hours in UTC+0 in the reviewer notes field

**Don't:**
- Don't run the bot on your laptop or desktop
- Don't submit and then shut it down to save resources
- Don't have auto-leave logic that triggers on unrecognised servers
- Don't gate your bot behind an invite-only whitelist during review

---

## Setting Up pm2 (Node.js)

```bash
# Install globally
npm install -g pm2

# Start your bot
pm2 start bot.js --name mybot

# Make it survive server reboots
pm2 startup
pm2 save
```

---

## Hosting Options

| Host | Cost | Notes |
|------|------|-------|
| Railway | Free / ~$5/mo | Simple GitHub deploys |
| Fly.io | Free tier available | More configuration options |
| Oracle Cloud | Always-free tier | Solid free VPS |
| DigitalOcean | ~$4-6/mo | Reliable, full control |
| Replit | Free tier | Use Reserved VM — free tier sleeps |

---

## Key Takeaway

An offline bot is an instant rejection regardless of how good the bot actually is. Get proper hosting in place before you submit.
