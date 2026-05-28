# 08 — Unmodified Clones

> Reviewers know the popular open-source bots. Submitting a clone with no meaningful changes is one of the most commonly caught issues — and it results in an immediate rejection.

---

## The Rule

You may build on top of open-source bots, but the result must be **meaningfully different** from the original. Changing the name, avatar, prefix, or embed colours does not count as modification.

---

## What Gets You Rejected

Reviewers specifically identify the source repository in the rejection:

```
Your bot appears to be an unmodified instance of Olympus
(https://github.com/sonujana26/olympus). We don't allow unmodified clones
of other bots.
```
```
Your bot seems to be an unmodified instance of BotGhost
(https://www.botghost.com/). We do not allow unmodified clones of other bots.
```
```
Your bot appears to be an unmodified instance of Lavamusic
(https://github.com/bongodevs/lavamusic). We do not allow unmodified clones
of other bots. Please note that you must add a new, unrelated feature or a
minimum of five valuable commands in order for us to consider a clone as
modified.
```
```
Your bot seems to be an unmodified instance of discord-js-bot
(https://github.com/saiteja-madha/discord-js-bot). We don't allow unmodified
clones of other bots. Please note that you must add a new, unrelated feature
or add a minimum of five valuable commands in order for us to consider a clone
to be modified.
```

Reviewers are familiar with the most popular open-source Discord bot repositories. They compare your bot's commands, responses, structure, and behaviour against known public repos.

---

## What Counts as "Modified"

Top.gg's standard, stated directly in their rejection messages:

> You must add **a new, unrelated feature** OR a **minimum of five valuable commands** in order for a clone to be considered modified.

### Does NOT count as a modification

- Changing the bot's name or avatar
- Changing the prefix
- Renaming commands (`.help` → `!help`)
- Updating embed colours or styles
- Changing config values
- Translating responses to another language (on its own)
- Adding 1–2 trivial commands like `/ping` or `/invite`

### DOES count as a modification

- Adding a complete new feature system (e.g. a ticket system to a music bot)
- Adding 5 or more valuable, functional commands that didn't exist in the original
- Substantially rewriting the logic of a core existing feature
- Adding a web dashboard that didn't exist in the source
- Adding an economy or leveling system from scratch

---

## How Reviewers Detect Clones

- Identical command names and aliases
- Identical embed designs and response text
- Identical error messages and help structure
- Behaviour that matches a known public repository exactly

---

## What To Do

**Do:**
- Build something original — even if simple, original work always passes this check
- If using open-source as a base, add at least one completely new feature system or five new valuable commands
- Mention what you added in the reviewer notes when resubmitting
- Check whether the source bot is already listed on Top.gg — if it is, your version needs to be substantially different

**Don't:**
- Don't clone a repo, change the name, and submit it
- Don't treat a language translation alone as sufficient modification
- Don't use BotGhost or other no-code bot builders and submit the output without heavy customisation
- Don't think changing colours or the avatar qualifies as meaningful modification

---

## Building on Open Source — Example

```
Base: Lavamusic (music player)

Additions that would qualify your submission:
  - Ticket system  (/ticket setup, /ticket close, /ticket panel)
  - Economy system (/daily, /balance, /leaderboard, /shop, /buy)
  - Custom automod  (/automod setup, /automod add-word, /automod logs)
```

Any one of those additions on top of the original would likely qualify. The key is that it must be a genuinely new, complete system — not a handful of trivial extra commands.

---

## Key Takeaway

Top.gg reviewers know the popular open-source bots. If you clone without adding substantial new functionality, you will be caught. Build something original, or build meaningfully on top of something existing.
