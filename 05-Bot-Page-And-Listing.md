# 05 — Bot Page & Listing

> Your bot's page on Top.gg is reviewed just as closely as the bot itself. A bad description or the wrong prefix listed will get you declined before a reviewer even runs a command.

---

## The Rule

Your listing must accurately represent what your bot does, use a genuine description written for real users, and have the correct prefix so reviewers can actually test your bot.

---

## What Gets You Rejected

### Spam or AI-Generated Description

```
The long description on your bot's page is filled out with irrelevant/spam/
AI-generated content to reach the 300 character minimum requirement. Please
rewrite your description to include more useful information about your bot.
```

This was the **second most common rejection reason** in the entire dataset — 56+ bots declined for it. Reviewers identify filler content immediately. Copy-pasted AI output, keyword stuffing, or repeating sentences to hit the character limit is a guaranteed rejection.

---

### Wrong Prefix Listed

```
The prefix you've listed on your bot page seems to not match your bot's
actual prefix. Please make sure the prefix you list is correct so we are
able to test your bot properly. If your bot uses slash commands, the prefix
should be listed as "/".
```

```
Your prefix is currently listed as "/", but there do not appear to be any
slash commands. If your bot does have slash commands, please ensure they
are deployed globally.
```

27+ bots were rejected solely for this. The prefix on your page is what reviewers use to test your bot. If it's wrong, nothing works, and you get declined immediately.

---

### Mentions Illegal or Controlled Substances

```
Your bot and/or bot's page mentions or depicts illegal or controlled
substances. Please remove all mentions and depictions before resubmitting.
```

Any mention of drugs, controlled substances, or related paraphernalia — in your bot's name, description, tags, or responses — results in rejection.

---

### Promotes a Competing Service

```
Your bot promotes or operates a service that competes with Top.gg on your
bot page. We do not allow any competition on a website as that competes
with Top.gg. Please remove that function and resubmit.
```

Advertising other bot listing platforms in your description, commands, or bot responses will get your submission rejected.

---

### Listed Commands Don't Match the Bot

```
The commands listed on your bot's page do not seem to actually exist in
the bot.
```

Keep your listing in sync with your actual bot. Do not advertise features or commands that haven't been built yet.

---

## What To Do

**Do:**
- Write your description yourself, in plain language, describing what your bot does and how to use it
- List the correct prefix — if slash commands, use `/`; if a custom prefix, list the exact character(s)
- Only list commands that exist and work in the bot right now
- Write at least 300 characters of genuine content — explain your bot's features, commands, and setup process
- Update your listing any time you change your bot's prefix

**Don't:**
- Don't use AI to write your description or pad the character count
- Don't copy another bot's description
- Don't list a prefix that doesn't match your actual bot
- Don't mention drugs, substances, or illegal activities anywhere on the page
- Don't link to or promote other bot listing websites
- Don't list commands that aren't built or working yet

---

## Good vs Bad Description

**Bad — AI filler:**
> BotName is an incredible, feature-rich, multi-purpose Discord bot designed to revolutionize your server management experience. With powerful tools and an intuitive interface, BotName provides everything you need to create an engaging and well-moderated community.

**Good — actual description:**
> BotName is a moderation and ticketing bot for Discord servers.
>
> **Commands:**
> `/ban` — Ban a user | `/kick` — Kick a user | `/mute` — Timeout a user
> `/ticket setup` — Set up a ticket panel | `/ticket close` — Close a ticket
>
> **Setup:** Run `/setup` after inviting the bot. Requires `MANAGE_ROLES` permission.
>
> Support server: discord.gg/yourinvite

---

## Prefix Reference

| Bot Type | What to List as Prefix |
|----------|------------------------|
| Slash commands only | `/` |
| Prefix commands only | Your actual prefix (e.g. `!`, `.`, `-`) |
| Both | List both (e.g. `/` or `!`) |

---

## Key Takeaway

Wrong prefix and a spam description are two of the easiest things to fix — and two of the most common reasons for rejection. Double-check both before submitting.
