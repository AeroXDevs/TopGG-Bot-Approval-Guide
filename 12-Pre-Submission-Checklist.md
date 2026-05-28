# 12 — Pre-Submission Checklist

> Go through every item before hitting submit. This checklist covers every rejection reason found across 1,000+ real review decisions. If everything here passes, you're in a strong position to be approved.

---

## How to Use This

Work through each section one by one. For every item, confirm it passes or fix it first. Do not skip sections that seem irrelevant — the most common rejections come from things people assumed were fine.

---

## Section 1 — Bot Availability

- [ ] My bot is hosted on a reliable server, not my personal computer
- [ ] My bot has been running continuously for at least 24 hours without crashing
- [ ] My bot will stay online during the entire review period (days to weeks)
- [ ] I have a process manager (pm2, systemd) set up so the bot restarts on crash
- [ ] `PUBLIC BOT` is enabled in the Discord Developer Portal
- [ ] My bot does not auto-leave unrecognised servers
- [ ] If I have a guild whitelist, `333949691962195969` (Top.gg Verification Center) is on it
- [ ] If my bot runs on a schedule, I have noted those hours in UTC+0 in the reviewer notes

---

## Section 2 — Permissions

- [ ] I have audited every command — each one only requests permissions it actually needs
- [ ] My lock and unlock commands use `MANAGE_ROLES`, not `MANAGE_CHANNELS`
- [ ] No command in my bot requires `ADMINISTRATOR` permission
- [ ] My bot does not request `Manage Guild` for commands that don't modify guild settings
- [ ] Permission error messages accurately state which permission is actually missing
- [ ] I have tested every command using a non-admin role with only the stated permissions

---

## Section 3 — Functionality

- [ ] Every command listed on my bot's page exists in the bot
- [ ] Every command listed on my bot's page produces a correct response
- [ ] My bot's main/primary feature works end to end
- [ ] If music bot: the bot joins voice AND plays audio — tested with multiple sources
- [ ] If ticket bot: panel posts → ticket opens → channel created → ticket closes — full flow tested
- [ ] If dashboard required: a standard Discord user (not just me) can log in and use it
- [ ] My bot has at least 1 complete feature system OR 5+ valuable commands
- [ ] My bot's commands work in any server, not only my own
- [ ] Slash commands are deployed globally, not guild-only

---

## Section 4 — Help Command & Entry Point

- [ ] My bot has a working `/help` or `!help` (or equivalent) command
- [ ] The help command is accessible to any user — no permissions, roles, or owner check required
- [ ] The help command lists all available commands with descriptions
- [ ] A new user can figure out how to start using my bot within 30 seconds of adding it
- [ ] Slash commands appear in the slash command menu (type `/` in the server to verify)

---

## Section 5 — Bot Page & Listing

- [ ] The prefix listed on my bot page matches my bot's actual prefix exactly
- [ ] If slash commands only: prefix is listed as `/`
- [ ] My long description is written by me, in plain language, about my bot's actual features
- [ ] My description is not filler, not AI-generated padding, and not copied from another bot
- [ ] My description contains useful information — commands, setup steps, use cases
- [ ] My bot's name, description, tags, and responses contain no drug or substance references
- [ ] My bot's page does not promote or link to competing bot listing services
- [ ] All commands listed on my page exist and work in the bot right now

---

## Section 6 — Privacy & API Abuse

- [ ] My bot does not have a command that messages every server member
- [ ] My bot does not automatically create server invite links on join
- [ ] My bot does not have a publicly accessible server list command (or it's owner-only with opt-in)
- [ ] Any DM command discloses the sender's identity or states it's anonymous
- [ ] Any DM command has a block or opt-out mechanism for recipients
- [ ] My bot does not have a channel or server wipe/nuke command
- [ ] My bot does not have a downloader command (YouTube, TikTok, Spotify, etc.)
- [ ] My bot updates its presence no more than once every 4 seconds (recommended: every 120s)
- [ ] My bot does not ask users for passwords, tokens, or login credentials
- [ ] My bot is running as a single instance only — not simultaneously on two machines

---

## Section 7 — Content Policy

- [ ] My bot has no references to illegal drugs or controlled substances anywhere
- [ ] All NSFW commands are locked to NSFW-only channels with a proper channel type check
- [ ] My bot does not send explicit content in DMs
- [ ] My bot does not promote other bot listing platforms anywhere
- [ ] My bot does not include video or audio downloader functionality
- [ ] My bot has not been flagged by Discord (check the Developer Portal)

---

## Section 8 — Clones & Originality

- [ ] My bot is either original or meaningfully modified from its open-source base
- [ ] If based on open source: I have added at least 1 new feature system OR 5+ new valuable commands
- [ ] My bot's commands, responses, and behaviour are not identical to a known public repository
- [ ] I am not submitting a no-code bot builder output without heavy customisation

---

## Section 9 — Application Setup

- [ ] `REQUIRES OAUTH2 CODE GRANT` is turned OFF in the Discord Developer Portal
- [ ] My Application/Client ID is correct in the invite URL I submitted
- [ ] My bot application has not been deleted
- [ ] I have a bot user created under my application
- [ ] My invite URL works — I tested it myself in a private/incognito window
- [ ] My invite URL includes `applications.commands` scope if I use slash commands
- [ ] My bot is not running on multiple instances simultaneously
- [ ] My bot's application has no Discord flags on it

---

## Section 10 — Premium & Subscriptions

- [ ] My bot's core functionality is accessible without any subscription
- [ ] If my bot has premium features, I have whitelisted the Verification Center (`333949691962195969`)
- [ ] Or I have included a temporary premium activation code in my reviewer notes
- [ ] Core features are not locked behind a requirement to join my support server
- [ ] A reviewer can test everything advertised on my bot's page without paying anything

---

## Final Check

- [ ] I have added my bot to a fresh test server and tested every command as a regular member
- [ ] My bot has been running for 24+ hours with no manual restarts
- [ ] My bot's listing page is accurate and up to date
- [ ] If I was previously rejected, I have confirmed the specific fix is in place

---

## Quick Reference — Top Rejection Reasons

| Reason | Fix |
|--------|-----|
| Bot offline during review | Stable hosting + process manager |
| Spam or AI description | Rewrite it yourself |
| Wrong prefix listed | Match the prefix on your page to the actual bot |
| Bot crashes mid-review | Fix stability and use pm2 |
| Wrong permissions in lock commands | Use `MANAGE_ROLES`, not `MANAGE_CHANNELS` |
| Commands don't work | Test every listed command before submitting |
| No help command | Build one, open to all users |
| Not enough commands or features | Minimum: 1 feature OR 5 valuable commands |
| Owner banned from Top.gg | Appeal: https://support.top.gg/hc/en-us/articles/23143055448220 |
| Premium gating during review | Whitelist Verification Center or provide a review code |

---

> Every box checked? Submit. Any box unchecked? Fix it first.
