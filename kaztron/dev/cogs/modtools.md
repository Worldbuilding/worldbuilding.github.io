---
title: "Cogs: ModTools"
last_updated: 21 February 2018
summary: "The ModTools cog provides miscellaneous tools for moderators."
---

## 1. up

Colours a moderator's username.

This command colours the moderator's username by applying a special role to it. This is used for moderators to be able to signal when they are speaking or intervening officially in their role as moderator.

**Usage:** `.up`

**Arguments:** None

**Channels:** Any

**Usable by:** Moderators only


## 2. down

Uncolours a moderator's username.

This command undoes the `.up` command.

**Usage:** `.down`

**Arguments:** None

**Channels:** Any

**Usable by:** Moderators only


## 3. whois

Finds a Discord user from their ID, name, or name with discriminator.

This command will not search for users based on a partial name, only find exact matches.

{% include warning.html content="If the user is in the channel where you use this command, the user will receive a notification." %}

**Usage:** `.whois <user>`

**Arguments:**
* `user`: An ID number, name, name with discriminator, etc. of a user to find.

**Channels:** Any

**Usable by:** Moderators only

**Example:**
* `.whois 1234567890` will find user 1234567890.
* `.whois JaneDoe#0921` will find a user called JaneDoe with discriminator #0921.
* `.whois JaneDoe` will find a user called JaneDoe. 


## 4. wb

Shows a "Please talk about worldbuilding" image.
        
For mod intervention, when discussions get off-topic.

**Usage:** `.wb [index]`
        
**Arguments:**
* index: Optional. If specified, the index of the image to show (starting at `0`). If not specified, a random image is shown.

**Channels:** Any

**Usable by:** Moderators only

**Examples:**
* `.wb` - Show a random image.
* `.wb 3` - Show image at index 3 (4th image).
