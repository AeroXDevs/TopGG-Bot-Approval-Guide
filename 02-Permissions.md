# 02 — Permissions

> One of the most misunderstood areas in bot development. Requesting the wrong permissions is a guaranteed rejection — and one specific mistake (lock commands) appears dozens of times in the dataset.

---

## The Rule

**Only request the permissions your bot actually needs to function.** Not what might be useful one day. Not what looks thorough. Each command should request only the permissions that specific command genuinely requires to run.

---

## What Gets You Rejected

### Requesting ADMINISTRATOR Permission

```
Your bot has a command ([/backup load]) that requires the bot itself to have
the ADMINISTRATOR permission. Please only require the permissions your bot
truly needs.
```

`ADMINISTRATOR` grants unrestricted access to the entire server. It overrides every other permission. Reviewers will reject this every single time unless there is an exceptional reason — and even then it's unlikely to pass. Nearly no legitimate bot feature actually requires it.

---

### Lock Commands Using MANAGE_CHANNELS Instead of MANAGE_ROLES

This is one of the most repeated specific mistakes in the entire dataset. Dozens of bots were declined for this exact error across many different command names:

```
Your bot's [/lock] command states that it needs the MANAGE_CHANNELS
permission to function. This is incorrect, to remove view or send messages
permission from users, a lock command only needs MANAGE_ROLES. Please update
this and resubmit.
```

**Why this is wrong:** Locking a channel means editing the permission overwrites on the `@everyone` role — which is a role operation. That requires `MANAGE_ROLES`. `MANAGE_CHANNELS` is for creating, deleting, and editing channel properties like name, topic, and slowmode.

This mistake has been found in: `/lock`, `!lock`, `.lock`, `,lock`, `#lock`, `?lock`, `-lock`, `f!lock`, `>lock`, `/lockdown`, `-lockdown`, `,lockdown`, `/channel lock`, and more.

```js
// Wrong
const requiredPermissions = ['MANAGE_CHANNELS'];

// Correct — for locking/unlocking channels
const requiredPermissions = ['MANAGE_ROLES'];
```

---

### Unnecessary Permissions on Specific Commands

```
Your bot has a command ([/setuphanaura]) which requires Manage Channels,
Manage Messages, Manage Threads, Manage Roles, Create Invite, and Use
Activities even though the command itself does not make use of them.
```

```
Your bot requires permissions such as Manage Channels, Manage Permissions,
and Manage Messages, which do not seem necessary for its functionality,
i.e. number guessing.
```

Reviewers test each command and check which permissions it actually uses. If your number-guessing command asks for `BAN_MEMBERS`, that is a rejection.

---

### Incorrect Permission Error Messages

```
Your bot asks for some unknown permission or role in order to run commands.
Please make sure that your error messages/missing permissions are labeled
correctly and resubmit your bot.
```

If your bot says "Missing permission: MANAGE_CHANNELS" but actually needs `MANAGE_ROLES`, that counts as a mislabelled permission. Error messages must accurately state what permission is actually required.

---

### Poll / Setup Commands Asking for Manage Guild

```
Your bot includes the `-createpoll` command, which currently requires the
`Manage Guild` permission even though the command can function without it.
```

Survey, poll, and setup commands frequently over-request permissions. Audit each one individually.

---

## What To Do

**Do:**
- Go through every single command and map it to only the permissions it actually needs
- Use `MANAGE_ROLES` for lock and unlock commands — this is the correct permission
- Use `MANAGE_CHANNELS` only when creating, deleting, or editing channel properties
- Test every command using a non-admin test account with only the stated permissions
- Make sure permission error messages accurately reflect what is missing

**Don't:**
- Don't request `ADMINISTRATOR` for any command unless you have a genuinely extraordinary reason
- Don't use `MANAGE_CHANNELS` in lock commands
- Don't bulk-request permissions "just in case"
- Don't show error messages that name the wrong permission

---

## Permission Reference for Common Features

| Feature | Correct Permission |
|---------|--------------------|
| Lock / unlock a channel | `MANAGE_ROLES` |
| Create / delete / edit a channel | `MANAGE_CHANNELS` |
| Kick members | `KICK_MEMBERS` |
| Ban members | `BAN_MEMBERS` |
| Timeout (mute) members | `MODERATE_MEMBERS` |
| Delete messages | `MANAGE_MESSAGES` |
| Assign or remove roles | `MANAGE_ROLES` |
| Create a server invite | `CREATE_INSTANT_INVITE` |
| Manage member nicknames | `MANAGE_NICKNAMES` |
| View audit log | `VIEW_AUDIT_LOG` |

---

## Key Takeaway

The most repeated permission mistake in the dataset is using `MANAGE_CHANNELS` in lock commands. Fix that first, then audit every other command one by one.
