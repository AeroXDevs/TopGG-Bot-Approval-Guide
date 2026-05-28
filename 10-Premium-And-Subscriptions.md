# 10 — Premium & Subscriptions

> Locking your bot's main features behind a paywall during review is a quick rejection. Reviewers need to be able to test your bot's full functionality — without paying for it.

---

## The Rule

Reviewers must be able to access and test your bot's **core features** without any subscription or payment. If your primary functionality is gated behind premium, you must give reviewers access before submitting.

---

## What Gets You Rejected

### Core Feature Requires a Paid Subscription

```
Your bots main feature requires a server subscription. Please add the
Top.gg Verification Center (333949691962195969) to a whitelist or create
a temporary premium subscription, or provide premium activation in the
reviewer's note/bot description so we can access your bot's full functionality.
```

```
Your bot's main feature (!sync_all) requires premium to use. Please add
the Top.gg Verification Center (333949691962195969) to a whitelist or
create a temporary premium subscription so we can test your bot properly.
```

If the very thing your bot is built around requires a paid plan to access, reviewers cannot evaluate it. They will decline immediately.

---

### Feature Locked Behind Support Server Join

```
The bot's main feature is locked behind a requirement to join the support
server. As per our guidelines, this is only allowed if the feature is not
the core functionality of the bot and the majority of commands remain
accessible without requiring a server join.
```

Requiring users to join your support server to unlock features is only acceptable if it applies to secondary or bonus features — not the primary purpose of the bot.

---

## Free vs Premium — What's Acceptable

### Must Be Free During Review
- The primary advertised functionality of your bot
- Anything mentioned in your short description
- The feature a reviewer would test first
- Whatever makes your bot worth listing

### Can Be Gated Behind Premium
- Extended limits (free = 50 songs, premium = unlimited)
- Cosmetic upgrades (custom embed colours, custom status)
- Priority support or faster response times
- Advanced analytics or logging
- Bonus commands that add value but aren't the core reason to use the bot

---

## How to Give Reviewers Access

Top.gg accepts three approaches:

### Option 1 — Whitelist the Verification Center

Add the server ID `333949691962195969` to your premium whitelist so the server automatically gets premium when your bot joins.

```js
const PREMIUM_SERVERS = [
  '333949691962195969', // Top.gg Verification Center — always include this
];

function hasPremium(guildId) {
  return PREMIUM_SERVERS.includes(guildId) || checkDatabase(guildId);
}
```

### Option 2 — Provide a Temporary Activation Code

Generate a one-time or temporary premium code and include it in the "Note for Reviewer" field when submitting. The reviewer will activate it themselves.

### Option 3 — Document It in the Description

If there's a way to get free trial access, document it clearly in your bot's description and mention it in the reviewer notes.

---

## Designing a Good Free / Premium Split

```
Free — always accessible:
  /play, /skip, /queue, /stop     (basic music)
  /ban, /kick, /mute              (basic moderation)
  /help, /info, /ping

Premium — can be gated:
  24/7 mode (bot stays in voice channel)
  Unlimited queue length
  Audio filters (bassboost, nightcore)
  Priority queue
  Custom DJ role settings
```

This lets reviewers test your core music functionality for free, while premium tiers offer genuine extras.

---

## What To Do

**Do:**
- Whitelist the Top.gg Verification Center (`333949691962195969`) for premium access every time you submit
- Include a temporary activation code in your reviewer notes if you can't whitelist
- Make sure at least the core functionality is free and testable
- Design premium around limits and extras, not core features

**Don't:**
- Don't gate your bot's only main feature behind a subscription with no way for reviewers to access it
- Don't require reviewers to pay to test your bot
- Don't make joining your support server a requirement for core functionality
- Don't submit without notifying the reviewer about premium requirements

---

## Key Takeaway

If a reviewer can't access your bot's main feature without paying, it gets declined. Whitelist the Verification Center server ID or provide a review code in the submission notes — every single time you submit.
