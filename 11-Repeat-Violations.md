# 11 — Repeat Violations

> Getting declined once is normal. Getting declined for the exact same reason three times leads to a ban.

---

## The Rule

Top.gg tracks how many times your bot has been rejected and for what reason. If you keep resubmitting without fixing the flagged issue, you will be banned from Top.gg — not just rejected again.

---

## How the Warning System Works

Reviewers begin issuing explicit warnings at the **third decline for the same reason**:

```
This is the 3rd time your bot has been declined for the same reason.
Failure to fix this issue may result in your bot being banned from Top.gg.
```

```
This is the 3rd time your bot was declined for the same reason!
Failure to fix this issue may result in you getting banned from Top.gg.
```

These warnings have appeared on bots declined for:
- Wrong permissions in lock commands
- Unnecessary permissions
- DM commands without opt-out
- Premium gating without reviewer access
- Broken ticket systems

---

## Progression Table

| Submission | What Happens |
|------------|-------------|
| 1st decline | Normal rejection with reason |
| 2nd decline (same reason) | Normal rejection — reviewer may note the pattern |
| 3rd decline (same reason) | Explicit ban warning included in the rejection |
| 4th+ decline (same reason) | Ban from Top.gg |

---

## Owner Bans

```
The primary owner of this bot was banned from the Top.gg server. They are
prohibited from adding any bots. IMPORTANT: If you would like to appeal,
please read the following:
https://support.top.gg/hc/en-us/articles/23143055448220-How-to-Appeal-your-Ban
```

This was the 9th most common rejection reason in the dataset — 13+ bots declined because the owner was banned from the Top.gg server. An owner ban blocks all future submissions. If this applies to you, the appeals process is your only option.

---

## Most Common Reasons for Repeat Rejections

| Reason | Why It Keeps Happening |
|--------|------------------------|
| Wrong permissions in lock commands | Developers don't realise `MANAGE_ROLES` is the correct permission |
| Bot offline | No stable hosting — keeps going offline between submissions |
| Unnecessary permissions | Hard to catch without auditing every command individually |
| Broken main feature | Underlying dependency (Lavalink, external API) not actually fixed |
| Premium gating | Owner forgets to whitelist or provide a code again on resubmission |
| DM commands without opt-out | Owner thinks the current implementation is acceptable |

---

## What To Do

**Do:**
- Read the rejection reason in full — don't skim it
- Fix the exact issue stated before resubmitting
- Test your fix specifically before resubmitting — verify the issue is actually resolved
- Ask for clarification in the Top.gg Discord server if you're unsure what the reason means
- Treat a "3rd time" warning as final — one more unresolved submission risks a ban
- If banned, use the appeals process: https://support.top.gg/hc/en-us/articles/23143055448220

**Don't:**
- Don't resubmit immediately after a rejection without making any changes
- Don't make a minor unrelated change and hope the reviewer doesn't notice the same issue
- Don't submit the same bot repeatedly without addressing the stated reason
- Don't ignore the warning language in rejection messages

---

## Key Takeaway

Top.gg reviewers will not approve a bot just because you resubmitted. Fix the exact issue stated. If you see a "3rd time" warning, treat it as your final chance.
