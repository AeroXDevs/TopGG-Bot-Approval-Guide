# 07 — Content Policy

> What your bot produces, displays, or enables is reviewed just as much as how it functions. Some of these violations lead straight to a ban, not just a rejection.

---

## The Rule

Your bot must not produce, enable, or promote content that is illegal, explicitly sexual in the wrong context, or that violates Discord's own Terms of Service. This applies to what your bot does and what your bot's listing page says.

---

## What Gets You Rejected

### Illegal or Controlled Substances

```
Your bot and/or bot's page mentions or depicts illegal or controlled
substances. Please remove all mentions and depictions before resubmitting.
```

Any reference to illegal drugs, controlled substances, or related content — in your bot's name, description, commands, or responses — is a rejection. This includes references framed as jokes or satire.

---

### NSFW Content in Non-NSFW Channels

```
Your bot has a command ([/erp]) that sends NSFW content in a non-NSFW
channel (DM). Please lock this command to only NSFW channels. If your
command uses an API or searches the web, please use safe search to filter
the content if you wish to have it available in non-NSFW channels.
```

Explicit content must be locked to age-verified NSFW channels only. DMs are **not** NSFW-safe by default. You cannot send explicit content to DMs.

```js
// Check before sending any explicit content
if (!interaction.channel.nsfw) {
  return interaction.reply({
    content: 'This command can only be used in NSFW channels.',
    ephemeral: true
  });
}
```

---

### Promoting a Competing Service

```
Your bot promotes or operates a service that competes with Top.gg on your
bot page. We do not allow any competition on a website as that competes
with Top.gg. Please remove that function and resubmit.
```

Advertising other bot listing platforms — whether in your description, commands, or bot responses — will get your submission rejected and potentially banned.

---

### Bot Flagged by Discord

```
Your bot has been flagged by Discord, which results in us being unable
to test your bot. This could be due to any of the following:
- Spam
- Abusive behaviour
- Reaching guild limit without verification
- Using privileged intents that your application was not approved for
```

If Discord has flagged your application, Top.gg's Verification Center cannot add your bot. You need to resolve this with Discord directly at **https://dis.gd/contact** before resubmitting to Top.gg.

Common causes:
- Bot joined too many servers too fast
- Bot was reported for abusive behaviour
- Bot uses `GUILD_MEMBERS` or `MESSAGE_CONTENT` intent without approval
- Bot hit the 100-server limit without going through Discord verification

---

### Piracy / Copyright Violations

```
Your bot has a command with a downloader feature which isn't allowed
because of privacy/piracy content laws. Please remove this command.
```

Commands that download, rip, or convert copyrighted media (YouTube videos, Spotify tracks, TikTok videos, etc.) violate copyright law and Top.gg's policies. There is no approved version of this — remove it entirely.

---

## What To Do

**Do:**
- Lock all NSFW commands to NSFW-only channels with a proper check
- Use safe-search APIs if your bot fetches content from the web
- Remove all drug and substance references from every part of your bot and listing
- Remove all links or references to competing bot listing platforms
- Apply for privileged intents through the Discord Developer Portal if your bot needs them and is in 100+ servers
- Contact Discord at https://dis.gd/contact if your application has been flagged

**Don't:**
- Don't send explicit content in DMs or non-NSFW channels under any circumstances
- Don't reference illegal drugs or controlled substances anywhere in your bot
- Don't promote other bot listing sites in your description, commands, or responses
- Don't include video or audio downloader functionality
- Don't use privileged intents without Discord's approval once your bot is verified

---

## NSFW Channel Check

```js
// Discord.js v14
if (!interaction.channel || !interaction.channel.nsfw) {
  return interaction.reply({
    content: 'This command can only be used in NSFW-marked channels.',
    ephemeral: true
  });
}

// Block DMs entirely for explicit commands
if (interaction.channel.type === ChannelType.DM) {
  return interaction.reply({
    content: 'This command cannot be used in DMs.',
    ephemeral: true
  });
}
```

---

## Key Takeaway

Content violations — especially drug references and NSFW in the wrong context — result in hard bans, not soft rejections. Clean your bot thoroughly before submitting.
