---
title: "Cogs: Core"
last_updated: 4 February 2018
summary: "The Core cog contains essential KazTron functionality: core setup and configuration tasks, general-purpose error handling for other cogs and commands, etc. It also includes commands for general bot information and control. The Core cog is essential to KazTron and cannot be disabled."
---



## 1. info

Provides bot info and useful links.

This command provides the version of the KazTron instance currently running, the latest changelog summary, and links to documentation, the GitHub repository, and other resources for operators and moderators.

As a very simple command with no external dependencies or failure points, it is also useful to check if the bot is up and running and responding to commands. If ever in doubt if KazTron is running, first check if `.info` is working.


**Usage:** `.info`

**Arguments:** None

**Channels:** Any

**Usable by:** Moderators only


## 2. request (issue, bug)

Submit a bug report or feature request to the bot DevOps Team.

This command is rate-limited to prevent excessive spam. This is a *global* limit. Abusive users should be dealt with in the same way as general channel spam.

Any content is allowed in the request, including any formatting supported by Discord. **One message = one issue.** As much as possible, avoid bundling multiple issues into one `.request`, or of splitting up a single issue or feature request into many `.request`. Otherwise the DevOps team will get mad at you.

Received requests are posted to the #bot_issues channel.

**Usage:**
* `.request <Any request text.>`
* `.issue <Any request text.>`
* `.bug <Any request text.>`

**Channels:** Any

**Usable by:** Everyone

**Example:**
```
.request When trying to use the `.roll 3d20` command, I get the message:
"An error occurred! Details have been logged. Let a mod know so we can investigate."

This only happens with d20, I've tried d12 and d6 with no problems.
The last time this happened in #tabletop on 2018-01-31 at 5:24PM Pacific time.
```
